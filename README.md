# po1-infra



## Install

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

username: admin
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

```
helm repo add po1-infra <aws_account_id>.dkr.ecr.<region>.amazonaws.com/po1-infra
helm install po1-infra po1-infra/boostrap --namespace cattle-system --create-namespace
```

## CI



```
- export ARGOCD_SERVER=argocd.somewhere.dev
- export ARGOCD_AUTH_TOKEN=$ARGOCD_TOKEN
- argocd app sync bootstrap
- argocd app wait bootstrap

```