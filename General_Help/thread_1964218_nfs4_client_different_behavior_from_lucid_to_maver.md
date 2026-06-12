---
title: "nfs4 client different behavior from lucid to maverick"
date: 2012-04-23
forum: General Help
---

### Post by taopublic on 2012-04-23
Hi, I've recently upgraded from lucid to maverick desktop. I have NFS4 client on this box. Under Lucid's version, this client will keep an "established" TCP connection to the NFS4 server all the time, however, under Maverick, it will drop the connection after some idle time then re-establish it when I need to access any NFS file.

Is there a way to restore the lucid behavior? Besides the initial connection penalty, I have a script on server side to detect active client connection by using netstat -a|grep nfs.

Thanks!

---

### Post by taopublic on 2012-04-24
bump

---

### Post by taopublic on 2012-05-01
bump

---

