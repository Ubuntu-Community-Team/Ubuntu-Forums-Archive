---
title: "What is this? 127.0.0.1:32947"
date: 2010-05-11
forum: General Help
---

### Post by SpinningAround on 2010-05-11
Is there some way to understand why these connections are?

```

desktop@desktop:~$ netstat -n --tcp | grep 127.0.0.1
tcp        1      0 127.0.0.1:43829         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:37460         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:56641         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60756         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:56646         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:48239         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:41635         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54782         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:44995         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60746         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:37462         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60744         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:47555         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:36640         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:45323         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60742         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:58296         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60761         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54720         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:41633         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54737         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60740         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60751         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60644         127.0.0.1:32947         CLOSE_WAIT 

```

---

### Post by tgm4883 on 2010-05-11
> **SpinningAround said:**
> Is there some way to understand why these connections are?

```

desktop@desktop:~$ netstat -n --tcp | grep 127.0.0.1
tcp        1      0 127.0.0.1:43829         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:37460         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:56641         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60756         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:56646         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:48239         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:41635         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54782         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:44995         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60746         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:37462         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60744         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:47555         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:36640         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:45323         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60742         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:58296         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60761         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54720         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:41633         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:54737         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60740         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60751         127.0.0.1:32947         CLOSE_WAIT 
tcp        1      0 127.0.0.1:60644         127.0.0.1:32947         CLOSE_WAIT 

```

Thats odd. Something on your machine is trying to connect to your machine on port 32947

---

### Post by SpinningAround on 2010-05-11
> **tgm4883 said:**
> Thats odd. Something on your machine is trying to connect to your machine on port 32947

That is the weird part, it simply going around in a circle. Does it make any sense to connect from 127.0.0.1 to 127.0.0.1? Is it possible to check what processes that are connecting where or what connections are being used?

---

### Post by cdenley on 2010-05-11
```

sudo netstat -ntp
sudo netstat -ntlp

```

---

### Post by SpinningAround on 2010-05-11
> **cdenley said:**
> ```

sudo netstat -ntp
sudo netstat -ntlp

```

```

desktop@desktop:~$ sudo netstat -ntlp | grep 127.0.0.1
tcp        0      0 127.0.0.1:54384         0.0.0.0:*               LISTEN      3744/beam.smp   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1241/cupsd      
tcp        0      0 127.0.0.1:38177         0.0.0.0:*               LISTEN      3663/beam.smp   
linux@linux-desktop:~$ 


```

```

desktop@desktop:~$ sudo netstat -ntp | grep 127.0.0.1
tcp        1      0 127.0.0.1:55448         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55598         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55442         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:44715         127.0.0.1:38177         CLOSE_WAIT  3891/python     
tcp        1      0 127.0.0.1:55596         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55593         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55585         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55616         127.0.0.1:38177         CLOSE_WAIT  3891/python     
tcp        1      0 127.0.0.1:55446         127.0.0.1:38177         CLOSE_WAIT  3796/python     
tcp        1      0 127.0.0.1:55444         127.0.0.1:38177         CLOSE_WAIT  3796/python  

```

---

### Post by cdenley on 2010-05-11
```

sudo ps -f -p 3744,3663,3796,3891
sudo lsof -n -p 3744,3663,3796,3891

```

---

### Post by dcstar on 2010-05-11
> **SpinningAround said:**
> That is the weird part, it simply going around in a circle. Does it make any sense to connect from 127.0.0.1 to 127.0.0.1? Is it possible to check what processes that are connecting where or what connections are being used?

It is processes running on your localhost connecting to resources on your localhost - don't worry about it.

---

