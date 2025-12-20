# appsec-academy
Educational repository focused on Application Security applied to the development pipeline, using open source tools.

## Static Security Analysis Workflow

A static security analysis workflow has been implemented in `.github/workflows/static-security-pipeline.yml`. This workflow contains a `sast` (Static Application Security Testing) job that uses the [Semgrep](https://semgrep.dev/) tool to scan code for vulnerabilities and security issues.

### How to use this workflow in another repository

To call this workflow in another repository, you need to create a workflow file in your repository that references this reusable workflow. Example:

```yaml
name: Security Analysis

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  security-scan:
    uses: your-username/appsec-academy/.github/workflows/static-security-pipeline.yml@main
```

Replace `your-username/appsec-academy` with the correct path to the repository where this workflow is located and `@main` with the desired branch.

The workflow will:
1. Checkout the code
2. Run Semgrep with default rules
3. Generate a SARIF file with the results
4. Upload the results to the GitHub Security tab
