---
title: "executing some nohup command in parallel"
date: 2010-11-11
forum: General Help
---

### Post by mahmoodn on 2010-11-11
I want to write a script to execute some nohup commands in parallel. Normally I put my command in background using
```
nohup ./run arg1 > arg1.log &
```
Now I want to run these command in parallel:
```
nohup ./run arg1 > arg1.log &
nohup ./run arg2 > arg2.log &
nohup ./run arg3 > arg3.log &
nohup ./run arg4 > arg4.log &
nohup ./run arg5 > arg5.log &
```
How can I execute them in parallel?

---

