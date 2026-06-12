---
title: "MyDNS Stack Smashing ubuntu 9.10 64"
date: 2010-03-12
forum: General Help
---

### Post by DantePasquale on 2010-03-12
Hi,

I'm seeing the following in my syslog:

Mar 12 14:37:15 inferno mydns[5342]: *** stack smashing detected ***: /usr/local/sbin/mydns terminated
Mar 12 14:37:15 inferno mydns[4125]: pid 5342 exited due to signal 6
Mar 12 14:37:15 inferno mydns[4125]: Server pid 5342 died
Mar 12 14:37:25 inferno mydns[5510]: *** stack smashing detected ***: /usr/local/sbin/mydns terminated
Mar 12 14:37:25 inferno mydns[4125]: pid 5510 exited due to signal 6
Mar 12 14:37:25 inferno mydns[4125]: Server pid 5510 died

I've re-downloaded from sourceforge and re-made/installed, but still see this error quite often. 

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```


Any ideas?

Danté

---

