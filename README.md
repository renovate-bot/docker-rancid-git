# rancid-git on Alpine Linux

## Overview

Provide [`rancid`](http://www.shrubbery.net/rancid/),
the Really Awesome New Cisco confIg Differ,
with git support in a smallish container.
RANCID monitors a device's configuration, including software and hardware,
and uses CVS, Subversion, or Git to maintain history of changes.

Project:            https://github.com/jumanjihouse/docker-rancid-git/<br/>
Docker image:       https://registry.hub.docker.com/u/jumanjiman/rancid/<br/>
Upstream rancid:    http://www.shrubbery.net/rancid/

[![Download size](https://images.microbadger.com/badges/image/jumanjiman/rancid.svg)](http://microbadger.com/images/jumanjiman/rancid)&nbsp;
[![Version](https://images.microbadger.com/badges/version/jumanjiman/rancid.svg)](http://microbadger.com/images/jumanjiman/rancid)&nbsp;
[![Source code](https://images.microbadger.com/badges/commit/jumanjiman/rancid.svg)](http://microbadger.com/images/jumanjiman/rancid)&nbsp;
[![Docker Registry](https://img.shields.io/docker/pulls/jumanjiman/rancid.svg)](https://registry.hub.docker.com/u/jumanjiman/rancid/)&nbsp;
[![CircleCI](https://circleci.com/gh/jumanjihouse/docker-rancid-git.svg?style=svg)](https://circleci.com/gh/jumanjihouse/docker-rancid-git)


## How-to

### Pull an already-built image

    docker pull jumanjiman/rancid


### Tags

We provide multiple tags:

* optimistic:  `jumanjiman/rancid:latest`
* pessimistic: `jumanjiman/rancid:<version>_<builddate>_git_<hash>`

Example:

    jumanjiman/rancid:3.6.1-r0_20170702T1659_git_6fead99
                      ^^^^^^^^ ^^^^^^^^^^^^^     ^^^^^^^
                          |         |              |
                          |         |              +--> hash from this git repo
                          |         |
                          |         +-----------------> build date and time
                          |
                          +---------------------------> version of rancid


### Build locally

Build this image locally on a host with Docker:

    git clone https://github.com/jumanjihouse/docker-rancid-git.git
    cd docker-rancid-git
    ci/build

Run a container with bash from the built image:

    docker run --rm -it jumanjiman/rancid


### Test

We use circleci to build, test, and publish the image to Docker hub.
We use [BATS](https://github.com/bats-core/bats-core)
and [ShellCheck](https://github.com/koalaman/shellcheck) to run the test harness.

Run the tests locally:

    ci/test

Test output resembles:

    Check files for things like trailing whitespace.
    [yamllint] yamllint..........................................................................Passed
    [check-added-large-files] Check for added large files........................................Passed
    [check-case-conflict] Check for case conflicts...............................................Passed
    [check-executables-have-shebangs] Check that executables have shebangs.......................Passed
    [check-symlinks] Check for broken symlinks...............................(no files to check)Skipped
    [check-vcs-permalinks] Check vcs permalinks..................................................Passed
    [detect-private-key] Detect Private Key......................................................Passed
    [forbid-crlf] CRLF end-lines checker.........................................................Passed
    [forbid-tabs] No-tabs checker................................................................Passed
    [forbid-binary] Forbid binaries..........................................(no files to check)Skipped
    [git-check] Check for conflict markers and core.whitespace errors............................Passed
    [git-dirty] Check if the git tree is dirty...................................................Passed
    [shellcheck] Test shell scripts with shellcheck..............................................Passed
    [shfmt] Check shell style with shfmt.........................................................Passed
    [gitlint] gitlint............................................................................Passed

    Run BATS tests.
     ok image exists
     ok tagged image exists - optimistic
     ok tagged image exists - pessimistic
     ok rancid -h shows help
     ok rancid is the expected version
     - ci-build-url label is present (skipped: This test runs only on circleci)

    6 tests, 0 failures, 1 skipped
    [INFO] ci/test OK


## License

See [`LICENSE`](LICENSE) in this repo.
