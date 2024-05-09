
2. Add the OpenAI API key as a [secret] in your repository's settings.
3. Create a workflow YAML file, e.g. `.github/workflows/openai-pr-description.yml` with the following contents:

```yaml
name: Autofill PR description

on: pull_request

jobs:
  openai-pr-description:
    runs-on: ubuntu-22.04

    steps:
      - uses: platisd/openai-pr-description@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          openai_api_key: ${{ secrets.OPENAI_API_KEY }}
```

| Input             | Description                                           | Required | Default                    |
| ----------------- | ----------------------------------------------------- | -------- | -------------------------- |
| `github_token`    | The GitHub token to use for the Action                | Yes      |                            |
| `openai_api_key`  | The [OpenAI API key] to use, keep it hidden           | Yes      |                            |
| `pull_request_id` | The ID of the pull request to use                     | No       | Extracted from metadata    |
| `openai_model`    | The [OpenAI model] to use                             | No       | `gpt-3.5-turbo`            |
| `max_tokens`      | The maximum number of **prompt tokens** to use        | No       | `1000`                     |
| `temperature`     | Higher values will make the model more creative (0-2) | No       | `0.6`                      |

