### local-path 설정 

kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/master/deploy/local-path-storage.yaml  
kubectl patch storageclass local-path -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'  
kubectl get sc  
ls -l /opt/local-path-provisioner  

----

### describe, delete, port-forward, -A(모든것), edit 옵션 

kubectl describe pvc redis-data-my-first-gitops-redis-master-0 -n redis-test  
kubectl delete sts my-first-gitops-redis-master -n redis-test  
kubectl port-forward svc/my-first-gitops-redis-master 6379:6379 -n redis-test  
kubectl get pod -A  
kubectl exec -it my-first-gitops-redis-master-0 -n redis-test -- redis-cli -a Qhfhfh12#  
kubectl edit statefulset -n redis-test  

----

### ArgoCD 설정 및 계정  확인

kubectl get secret argocd-secret -n argocd -o yaml  
kubectl get secret argocd-secret -n argocd -o go-template='{{index .data "admin.password"}}' | base64 -d && echo  
echo "JDJhJDEwJGl1cXlBbkNCTWY2eVlvL3E3WFlwZGVRODVMUzMxTUZoZGNHT0N0UEpnTEpCeGlWWFdmQzFL" | base64 -d && echo  

