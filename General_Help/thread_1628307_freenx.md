---
title: "freenx"
date: 2010-11-22
forum: General Help
---

### Post by vranjan on 2010-11-22
Hello,

I have successfully run freenx on 10.04. However, since I upgraded to 10.10 it stopped working. Following latest post on freeNX community page, I was able to reinstall it. However, I cannot start freenx.

>ps ax |grep freenx
1811 pts/0    S+     0:00 grep freenx

>sudo /etc/init.d/freenx-server start
utility, e.g. service freenx-server start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start freenx-server
start: Unknown job: freenx-server

>service freenx-server start
start: Unknown job: freenx-server

>start freenx-server
start: Unknown job: freenx-server

No matter what command I use, it returns unknown job: freenx-server. 

> ll /etc/init.d/freenx-server
lrwxrwxrwx 1 root root 21 2010-11-22 12:43 /etc/init.d/freenx-server -> /lib/init/upstart-job

So, the file freenx-server is there in the correct place.

Any help would be appreciated.

Thank you,

Vivek

---

### Post by ajgreeny on 2010-11-22
How about ```
sudo service freenx-server start
```

That "sudo" command is needed for ssh, for example.

---

### Post by hantms on 2011-01-09
Experiencing the same issue.. Just doesn't seem to work.

> **ajgreeny said:**
> How about ```
sudo service freenx-server start
```

That "sudo" command is needed for ssh, for example.

Same result. :

```
$ sudo service freenx-server start
start: Unknown job: freenx-server

```

---

### Post by npap74 on 2011-02-17
Hello,

any answer to the above question. I have the same problem on a server with 10.04.

---

### Post by AndrewBorg on 2011-02-17
Try
sudo /etc/init.d/freenx-server start

Are you sure you installed the NX server Correctly?

---

### Post by npap74 on 2011-02-18
Thanks Andrew, but I have already tried this. As I understand, the issue is that freenx-server runs only when a client ask it. My mistake was the way I change keys.

During the installation (nxsetup --install) I decide not to create new keys and after that I copy only the **client.id_dsa.key**  to [FONT=Courier New][SIZE=2]/var/lib/nxserver/home/.ssh/[/SIZE][/FONT]  from my old installation.

So when I also copy **server.id_dsa.pub.key** and **authorized_keys2** from my old installation and changed permissions the connection worked.

:D

---

### Post by t0p on 2011-02-18
I used to use freenx; but I now use **ssh -X** and that seems to do the same job.

---

