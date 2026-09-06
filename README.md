# cryptography — iOS wheel build

This repository builds official, unmodified [pyca/cryptography](https://github.com/pyca/cryptography)
source code into iOS-compatible wheels, using [cibuildwheel](https://cibuildwheel.pypa.io/)
on GitHub's free macOS Actions runners (free and unlimited on public repos).

## Why this exists

`cryptography`'s Rust-based build previously had no working iOS target.
As of cibuildwheel 3.x, official iOS support exists (`CIBW_PLATFORM: ios`).
This repo builds the wheel **in-house, from the exact official upstream
source**, rather than relying on any third party's pre-built binary — the
build config is fully visible here, and the exact source commit built is
logged in every run's output.

## Contents

- No application code lives here. This repo contains only the build
  workflow itself.
- The `cryptography` source is fetched fresh, at a pinned version tag you
  specify, every time the workflow runs — nothing is vendored or committed
  into this repo.

## How to build

1. Go to the **Actions** tab of this repo.
2. Select **"Build cryptography for iOS"**.
3. Click **"Run workflow"**, enter the exact `cryptography` version to
   build (check [pyca/cryptography's releases](https://github.com/pyca/cryptography/releases)
   for the current stable version), and run it.
4. Once it finishes, download the wheel from the run's **Artifacts** section.

## Verifying what was actually built

Every run's log shows the exact git commit hash of the `cryptography` source
it built, under the "Show exactly what commit/tag we're building" step —
check this against the official tag on GitHub before trusting a build.
