# ci-workflows

Em qualquer outro repositório onde você deseja usar esses workflows, você pode chamá-los da seguinte maneira:


Workflow no Repositório de Projeto
Crie um arquivo .github/workflows/ci.yml no repositório do projeto:

name: CI

on:
  push:
    branches:
      - '*'
      - '!main'

jobs:
  build:
    uses: your-username/ci-workflows/.github/workflows/build.yml@v1.0.0
    with:
      java-version: '17'
      github-access-token: 'token_do_seu_github'

  test:
    uses: your-username/ci-workflows/.github/workflows/test.yml@v1.0.0
    with:
      java-version: '17'
      github-access-token: 'token_do_seu_github'

  create_pr:
    needs: [build, test]
    uses: your-username/ci-workflows/.github/workflows/git_pull_request.yml@v1.0.0
    with:
      github-access-token: 'token_do_seu_github'
