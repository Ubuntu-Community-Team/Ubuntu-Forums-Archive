---
title: "Boinc client binding to all interfaces"
date: 2012-05-05
forum: General Help
---

### Post by Soepstengel on 2012-05-05
Hi,


I don't know if this is an issue in Ubuntu or Boinc, but I hope to find some help here.

I installed the boinc-client package on my Ubuntu 12.04 installation and everything works fine except for one configuration issue. It seems the Boinc client RPC always binds to 0.0.0.0.

Is it possible to configure the boinc-client to bind to a single interface instead of 0.0.0.0? I don't think there is any logic in always binding to all interfaces, so I want to change this (if possible).


```
root@desktop:/etc/boinc-client# netstat -napt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      9421/boinc
```


Does anyone know if this is possible?

---

### Post by dcstar on 2012-05-05
> **Soepstengel said:**
> 
.........
Is it possible to configure the boinc-client to bind to a single interface instead of 0.0.0.0? I don't think there is any logic in always binding to all interfaces, so I want to change this (if possible).
.........
Does anyone know if this is possible?

Just because **you** "don't think there is any logic" in a way a program works is no reason to stuff around with it. Change it and you will probably break BOINC for no good reason whatsoever.

I can already see that you run Ubuntu with a root shell against the specific recommendations on this way of doing things, so if you intend to do more things in that manner can I please request that you don't post too many requests in these forums asking others to (somehow) help you recover from your adventures?

---

