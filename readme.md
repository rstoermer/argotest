# Intro

1. Create Cluster: kind create cluster --config hack/kind-cluster.yaml
2. Install Argo: helm install argocd argo/argo-cd --values hack/argo-values.yaml --namespace argocd --create-namespace
3. Create namespace to house pyro-vectors: k create ns pyro-vectors
4. Create Secrets for Vectors
   1. k create secret generic clickhouse-credentials --from-literal=lpvic=test -n pyro-vectors
   2.  k create secret generic kafka-connect-secret --from-literal=KAFKA_USERNAME=test --from-literal=KAFKA_PASSWORD=test -n pyro-vectors
5. Let Argo do the rest:  k apply -f clickhouse-vectors/applicationset.yaml