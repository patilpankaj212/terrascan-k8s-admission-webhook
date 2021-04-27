# terrascan-k8s-admission-webhook
Deploy terrascan as kubernetes admission webhook in local kubernetes cluster

### create certificates
Run: `openssl req -x509 -sha256 -nodes -newkey rsa:2048 -keyout certs/server.key -out certs/server.crt -config certs/domain.cnf`

### update caBundle in validating-webhook.yaml 
Run: `cat certs/server.crt | base64`, copy the output and update caBundle

### create a deployment with terrascan server
Run: `kubectl create -f terrascan-deployment.yaml`

### create a service for the application
Run: `kubectl create -f terrascan-service.yaml`

### create a validating webhook for you k8s cluster
Run: `kubectl create -f validating-webhook.yaml`

# Terrascan is now ready to accept validation requests.

Run: `kubectl run nginx-server --image=nginx` and observe the response
