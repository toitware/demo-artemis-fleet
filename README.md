# Fleet management with Artemis - Showcase

This repository demonstrates how fleet-management with Artemis can be done in
combination with GitHub actions.

## Setup

We assume two repositories:
1. https://github.com/toitware/show-artemis-pods: the development repository.
2. https://github.com/toitware/show-artemis-fleet: this repository.

Development of the code (pods) is done in the development repository. Deployment and
management of the fleet is done in this repository.

## Idea

The source code and pod-specification of pods live in the development repository.
Once a pod is ready for deployment it is uploaded from the development repository's
GitHub action to the fleet in this repository.

At this point the [fleet.json](fleet.json) should be updated (often with a
pull request). When the new fleet.json file is merged into the main branch
the GitHub action rolls out the new configuration to all affected devices.

Note that this repository does not build any pod. This is done in the
development repository.

## GitHub actions

The [GitHub action in this repository](.github/workflows/ci.yml) shows
how to automatically roll out new configurations when a commit is merged
into `main`, or when a workflow_dispatch is triggered.
