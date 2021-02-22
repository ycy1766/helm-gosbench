
This project is based on https://github.com/mulbc/gosbench and uses helm for flexible management in kubernetes environment.

Modify the values.yaml file and perform a test using gosbench with helm
example 
```
# cp values-example.yaml values.yaml
# helm install     test  -f values.yaml .
# kubectl  get all
NAME                                        READY   STATUS    RESTARTS   AGE
pod/test-gosbench-server-74b4449c58-pwlh8   1/1     Running   0          69s
pod/worker1-r2wq2                           1/1     Running   0          69s
pod/worker2-65cbm                           1/1     Running   0          69s
pod/worker3-kx4x2                           1/1     Running   0          69s
pod/worker4-8lqrl                           1/1     Running   0          69s
 
NAME                           TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/kubernetes             ClusterIP   10.233.0.1     <none>        443/TCP          3d3h
service/test-gosbench-server   NodePort    10.233.15.95   <none>        2000:32000/TCP   70s
 
NAME                                   READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/test-gosbench-server   1/1     1            1           69s
 
NAME                                              DESIRED   CURRENT   READY   AGE
replicaset.apps/test-gosbench-server-74b4449c58   1         1         1       69s
 
NAME                COMPLETIONS   DURATION   AGE
job.batch/worker1   0/1           69s        69s
job.batch/worker2   0/1           69s        69s
job.batch/worker3   0/1           69s        69s
job.batch/worker4   0/1           69s        69s
```

When the test is finished, uninstall the helm chart.
```
# helm uninstall test
```
