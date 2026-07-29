# Contributing to OpenControlPlane

## General Remarks

You are welcome to contribute content (code, documentation etc.) to this open source project.

There are some important things to know:

1. You must **comply to the license of this project** and **sign off every commit** under the Developer Certificate of Origin (see [Commit Requirements](#commit-requirements)).
2. Please **adhere to our [Code of Conduct](CODE_OF_CONDUCT.md)**.
3. If you plan to use **generative AI for your contribution**, please see our [AI-generated code guidelines](CONTRIBUTING_USING_GENAI.md).
4. **Not all proposed contributions can be accepted**. Some features may fit another project better or don't fit the general direction of this project. Of course, this doesn't apply to most bug fixes, but a major feature implementation for instance needs to be discussed with one of the maintainers first. Possibly, one who touched the related code or module recently. The more effort you invest, the better you should clarify in advance whether the contribution will match the project's direction. The best way would be to just open an issue to discuss the feature you plan to implement (make it clear that you intend to contribute). We will then forward the proposal to the respective code owner. This avoids disappointment.

## Commit Requirements

Every commit must satisfy two independent requirements. Both are enforced on every commit in every pull request.

### 1. Developer Certificate of Origin (DCO)

By contributing, you certify that you have the right to submit the code under this project's license.
NeoNephos uses [DCO version 1.1 from the Linux Foundation](https://developercertificate.org/).

Every commit must carry a `Signed-off-by` trailer with your real name and email address:

```
Signed-off-by: Your Name <your.name@example.com>
```

The sign-off must match your configured git identity:

```
git config user.name "Your Name"
git config user.email "your.name@example.com"
```

Use `git commit -s` to append the trailer automatically. Anonymous contributions are not accepted.

### 2. Verified Commits (cryptographic signing)

Every commit must be cryptographically signed with a GPG or SSH key [registered with your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).
This protects against supply chain attacks by ensuring that code pushed to the repository was authored
by a verified contributor.

Use `git commit -S` to sign a commit.

### Combined command

To satisfy both requirements in one step:

```
git commit -s -S -m "your commit message"
```

- `-s` appends the DCO `Signed-off-by` trailer
- `-S` cryptographically signs the commit

### 3. Commit Message Format

Commit messages must follow the [Conventional Commits 1.0](https://www.conventionalcommits.org/) specification:

```
<type>(<optional scope>): <description>

<body — explain the motivation and context for the change>

<footers>
```

Allowed types: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `ci`, `perf`, `build`.

The body is free-form prose and should explain *why* the change is being made, not just what it does. It is optional for trivial changes but expected for `feat` and `fix` commits.

Footers follow the body after a blank line. The following footers are used in this project:

- `Closes: #<issue>` — links and closes the related issue
- `Refs: #<issue>` — references a related issue without closing it
- `BREAKING CHANGE: <description>` — required for any commit that introduces a breaking change; describes what broke and how to migrate

Example of a full commit message:

```
feat(api): add pagination support for resource listing

The resource listing endpoints previously returned all results in a
single response, which caused timeouts for large datasets. This change
introduces cursor-based pagination consistent with the rest of the API.

Closes: #42
```

Example with a breaking change:

```
feat(api): remove deprecated v1alpha1 endpoints

The v1alpha1 endpoints have been deprecated since v0.4.0. All clients
must migrate to v1beta1 before upgrading.

BREAKING CHANGE: The /api/v1alpha1/* endpoints have been removed.
Migrate to /api/v1beta1/* equivalents.
Closes: #87
```

## How to Contribute

1. Make sure the change is welcome (see [General Remarks](#general-remarks)).
2. Create a branch by forking the repository and apply your change.
3. Commit your changes, ensuring each commit is signed off and cryptographically signed. See [Commit Requirements](#commit-requirements).
4. Push your branch and create a pull request in the repository.
5. Wait for our code review and approval, possibly enhancing your change on request.
    - Note that the maintainers have many duties. So, depending on the required effort for reviewing, testing, and clarification, this may take a while.

## Pull Request Guidelines

Before requesting review, make sure your pull request meets the following requirements:

- The PR is linked to an existing issue, or the PR description explains the motivation if no issue exists
- Each commit is focused on a single concern and follows the [commit message format](#3-commit-message-format)
- All commits are signed off (DCO) and cryptographically signed
- CI checks pass
- Breaking changes are clearly described in the PR description

## Contributing to Project Governance

For contributions to project governance, steering committee processes, or SIG operations, please refer to the [community repository](https://github.com/openmcp-project/community).