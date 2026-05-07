# Security policy

## Supported versions

The latest tagged release of Release Baton receives security updates. Older
tagged versions do not.

## Reporting a vulnerability

Report security issues privately via [GitHub's "Report a vulnerability"
form](https://github.com/release-baton/release-baton/security/advisories/new).
Do not open a public issue.

You should expect an acknowledgement within five working days. If you have
not heard back in that window, escalate by opening a public issue that
states only that a security report is awaiting acknowledgement — do not
include vulnerability detail.

## Scope

Release Baton holds no secrets server-side. The GitHub App's private key
is generated and stored by the installing organization, and installation
tokens are minted at workflow time and expire when the job ends.

In scope:

- Credentials accidentally committed to this repository's history.
- Weaknesses in how the reusable workflow or composite action handles
  the minted installation token (logging, leakage to other steps, scope
  expansion beyond the caller repository).
- Supply-chain risks introduced by pinned third-party actions.
- Vulnerabilities in `bin/setup` that could allow code execution during
  contributor onboarding.

Out of scope:

- Issues in upstream `googleapis/release-please-action` or
  `actions/create-github-app-token` — report those to their respective
  maintainers.
- Misconfiguration in a consumer organization (for example, granting the
  app access to a wider set of repositories than intended). The app
  enforces what GitHub permissions it requests; consumers control where
  it is installed.
