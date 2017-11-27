# node-ssh-access
Specs for enabling ssh access to Kubernetes nodes

## Deploy Specs
```
kubectl create -f node-ssh-deployment.yaml
kubectl create -f node-ssh-service.yaml
```

## Get External IP for ssh
```
$ kubectl get service node-ssh-service
NAME               CLUSTER-IP   EXTERNAL-IP      PORT(S)        AGE
node-ssh-service   10.0.33.27   52.165.141.205   22:30623/TCP   6m
```
You will ssh with the `EXTERNAL-IP` of the `node-ssh-service`. If you see `<pending>` under `EXTERNAL-IP` you will need to wait for the load balancer to issue an IP.

## ssh to cluster node
```
ssh <cluster user name>@<EXTERNAL-IP>
```
For example:
```
ssh azureuser@52.165.141.205
```
If your key isn't located at `~/.ssh/id_rsa` then you will need to provide the key location using `ssh -i`.
