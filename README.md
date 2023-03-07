# assignment46

while deleted voting pod/worker pod or result pod , voiting app still workes as it is , if we delete too its creating replica for it

below are the terminal observations

deployment.apps/db created
service/db created
deployment.apps/redis created
service/redis created
deployment.apps/result created
service/result created
deployment.apps/vote created
service/vote created
deployment.apps/worker created
[root@ip-172-31-15-8 k8s-specifications]# kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
db-b54cd94f4-ln4sj        1/1     Running   0          5m2s
kubia-manual              1/1     Running   0          5d23h
nishka-108                1/1     Running   0          6d
redis-868d64d78-4gb62     1/1     Running   0          5m2s
result-5d57b59f4b-dbc44   1/1     Running   0          5m2s
vote-94849dc97-tj2kd      1/1     Running   0          5m1s
worker-dd46d7584-6hnhl    1/1     Running   0          5m1s
[root@ip-172-31-15-8 k8s-specifications]# kubectl delete po vote-94849dc97-tj2kd
pod "vote-94849dc97-tj2kd" deleted
[root@ip-172-31-15-8 k8s-specifications]# kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
db-b54cd94f4-ln4sj        1/1     Running   0          6m2s
kubia-manual              1/1     Running   0          5d23h
nishka-108                1/1     Running   0          6d
redis-868d64d78-4gb62     1/1     Running   0          6m2s
result-5d57b59f4b-dbc44   1/1     Running   0          6m2s
vote-94849dc97-57xtl      1/1     Running   0          11s
worker-dd46d7584-6hnhl    1/1     Running   0          6m1s
[root@ip-172-31-15-8 k8s-specifications]# kubectl la
Error: unknown command "la" for "kubectl"

Did you mean this?
	cp
	label

Run 'kubectl --help' for usage.
[root@ip-172-31-15-8 k8s-specifications]# kubectl ls
Error: unknown command "ls" for "kubectl"

Did you mean this?
	logs
	cp

Run 'kubectl --help' for usage.
[root@ip-172-31-15-8 k8s-specifications]# ll
total 36
-rw-r--r-- 1 root root 401 Mar  7 06:29 db-deployment.yaml
-rw-r--r-- 1 root root 146 Mar  7 06:29 db-service.yaml
-rw-r--r-- 1 root root 402 Mar  7 06:29 redis-deployment.yaml
-rw-r--r-- 1 root root 152 Mar  7 06:29 redis-service.yaml
-rw-r--r-- 1 root root 299 Mar  7 06:29 result-deployment.yaml
-rw-r--r-- 1 root root 195 Mar  7 06:29 result-service.yaml
-rw-r--r-- 1 root root 289 Mar  7 06:29 vote-deployment.yaml
-rw-r--r-- 1 root root 192 Mar  7 06:29 vote-service.yaml
-rw-r--r-- 1 root root 292 Mar  7 06:29 worker-deployment.yaml
[root@ip-172-31-15-8 k8s-specifications]# vi worker-deployment.yaml
[root@ip-172-31-15-8 k8s-specifications]# kubectl delete po worker-dd46d7584-6hnhl  
pod "worker-dd46d7584-6hnhl" deleted
[root@ip-172-31-15-8 k8s-specifications]# kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
db-b54cd94f4-ln4sj        1/1     Running   0          8m41s
kubia-manual              1/1     Running   0          5d23h
nishka-108                1/1     Running   0          6d
redis-868d64d78-4gb62     1/1     Running   0          8m41s
result-5d57b59f4b-dbc44   1/1     Running   0          8m41s
vote-94849dc97-57xtl      1/1     Running   0          2m50s
worker-dd46d7584-44f88    1/1     Running   0          10s
[root@ip-172-31-15-8 k8s-specifications]# ll
total 36
-rw-r--r-- 1 root root 401 Mar  7 06:29 db-deployment.yaml
-rw-r--r-- 1 root root 146 Mar  7 06:29 db-service.yaml
-rw-r--r-- 1 root root 402 Mar  7 06:29 redis-deployment.yaml
-rw-r--r-- 1 root root 152 Mar  7 06:29 redis-service.yaml
-rw-r--r-- 1 root root 299 Mar  7 06:29 result-deployment.yaml
-rw-r--r-- 1 root root 195 Mar  7 06:29 result-service.yaml
-rw-r--r-- 1 root root 289 Mar  7 06:29 vote-deployment.yaml
-rw-r--r-- 1 root root 192 Mar  7 06:29 vote-service.yaml
-rw-r--r-- 1 root root 292 Mar  7 06:29 worker-deployment.yaml
[root@ip-172-31-15-8 k8s-specifications]# kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
db-b54cd94f4-ln4sj        1/1     Running   0          9m43s
kubia-manual              1/1     Running   0          5d23h
nishka-108                1/1     Running   0          6d
redis-868d64d78-4gb62     1/1     Running   0          9m43s
result-5d57b59f4b-dbc44   1/1     Running   0          9m43s
vote-94849dc97-57xtl      1/1     Running   0          3m52s
worker-dd46d7584-44f88    1/1     Running   0          72s
[root@ip-172-31-15-8 k8s-specifications]# kubectl delete po result-5d57b59f4b-dbc44
pod "result-5d57b59f4b-dbc44" deleted
[root@ip-172-31-15-8 k8s-specifications]# kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
db-b54cd94f4-ln4sj        1/1     Running   0          10m
kubia-manual              1/1     Running   0          5d23h
nishka-108                1/1     Running   0          6d
redis-868d64d78-4gb62     1/1     Running   0          10m
result-5d57b59f4b-cz6d6   1/1     Running   0          5s
vote-94849dc97-57xtl      1/1     Running   0          4m27s
worker-dd46d7584-44f88    1/1     Running   0          107s
[root@ip-172-31-15-8 k8s-specifications]# 
