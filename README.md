# About

Repo to hold manifest resources that will be pulled in by the `aip-doit-modules` for customer scenarios when
deploying via `kubectl apply`. This repo is seperate from the `doit-modules` to avoid complicated relative
path logic when linking these templates to a customer deployment manifest. Kustomize does not work with absolute
paths so kustomize [remote targets](https://github.com/kubernetes-sigs/kustomize/blob/master/examples/remoteBuild.md#remote-targets) 
give us a cleaner implementation.

This repo merely holds manifests under a single directory, nothing else for now. These templates should not be modified 
in place here, they can be referenced by customers via kustomize upstream or by AIP internally in the `do-it` modules.

# Sync with GitHub

In order to fully utilize kustomize remote target we must mirror this repo in GitHub. GitLab is currently not supported by 
kustomize remote targets.

## GitHub Repo URL

fill in here

# Adding templates

As of now, simply add the `{resource}.yaml` file to the `templates` directory in its proper coomponent. Adding under a component
will allow us in the future to pick and choose which component templates to apply to a target manifest. Additionally add the new resource file as a
resource in `kustomization.yaml` in order for it to get picked up by the `doit-modules`.