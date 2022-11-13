# Origo Kubernetes Monitoring Stack

Based on [Helm dependency approach](https://github.com/argoproj/argocd-example-apps/blob/master/helm-dependency/Chart.yaml) where one custom-made chart is created which in turn loads any arbitrary chart (or more, though less desirably) in addition to the custom-defined `values.yaml` in the same repo.

Important to note only is that when any new monitoring stack component is being added in this fashion, it's `values.yaml` file should contain the component name as the first key at the top of the file and all other content below should be indented by additional 2 spaces (*check existing ones to get the idea*).

Afterwards, the ArgoCD application is created for each separate component so it can be updated and managed easily by simple updating of component chart's `Chart.yaml` file and changing of the dependency version which is upstream chart version obtained from official chart repo releases page.

Additionally, whenever the chart version is getting bumped, prior to pushing to repo, ensure that the `values.yaml` file is in sync with uptream version as well to ensure highest amount of consistency and access to latest features and eventual bug fixes.