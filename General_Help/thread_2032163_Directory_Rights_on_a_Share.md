---
title: "Directory Rights on a Share"
date: 2012-07-23
forum: General Help
---

### Post by scambro on 2012-07-23
I'm racking my brain on this one and it seems like it should be pretty easy to me (in other words, I feel stupid).  Here's my setup - I have an Ubuntu server and a ReadyNas 1100 running some form of Linux.  I have the ReadyNas mapped in my fstab file as such:

```

//NAS01/media /media/nas01 nfs username=media,uid=1000,gid=1000 0 0

```

Everything works peachy except for this one pesky directory.  I FTP'd a bunch of files and directories from my Ubuntu box out to the ReadyNas, when something failed in the middle of the FTP.  For some reason one directory was failing the MD5check, so I deleted it and re'FTP'd it.  I have two directories with almost identical setups on the ReadyNas now.  When I SSH into the ReadyNas as the root user I can see everything:

```

nas01:/media/in_process/# ls -al T17*.wedt
T174.wedt:
total 5707536
drwxrwxrwx    2 media    nogroup     16384 Jul 23 07:49 .
drwxrwxrwx   12 media    nogroup     16384 Jul 23 07:37 ..
-rwxrwxrwx    1 media    nogroup      3319 Jul 23 07:49 document.info
-rwxrwxrwx    1 media    nogroup       461 Jul 23 07:37 format.info
-rwxrwxrwx    1 media    nogroup  2858327648 Jul 23 07:49 Layer 1_0000.00
-rwxrwxrwx    1 media    nogroup  2858327648 Jul 23 07:43 Layer 1_0000.01
-rwxrwxrwx    1 media    nogroup  125045074 Jul 23 07:37 Layer 1.info
-rwxrwxrwx    1 media    nogroup    401188 Jul 23 07:49 Layer 2_0000.00
-rwxrwxrwx    1 media    nogroup    401188 Jul 23 07:37 Layer 2_0000.01
-rwxrwxrwx    1 media    nogroup     22532 Jul 23 07:43 Layer 2.info
-rwxrwxrwx    1 media    nogroup     71460 Jul 23 07:49 layers.info
-rwxrwxrwx    1 media    nogroup    205129 Jul 23 07:43 master.info
-rwxrwxrwx    1 media    nogroup      1624 Jul 23 07:49 metadata.info
-rwxrwxrwx    1 media    nogroup       299 Jul 23 07:43 version.info

T175.wedt:
total 1799440
drwxrwxrwx    2 media    nogroup     16384 Jul 22 20:31 .
drwxrwxrwx   12 media    nogroup     16384 Jul 23 07:37 ..
-rwxrwxrwx    1 media    nogroup      3320 Jul 22 12:21 document.info
-rwxrwxrwx    1 media    nogroup       461 Jul 22 12:06 format.info
-rwxrwxrwx    1 media    nogroup  901266432 Jul 22 12:21 Layer 1_0000.00
-rwxrwxrwx    1 media    nogroup  901266432 Jul 22 12:15 Layer 1_0000.01
-rwxrwxrwx    1 media    nogroup  39436808 Jul 22 12:07 Layer 1.info
-rwxrwxrwx    1 media    nogroup       643 Jul 22 12:21 layers.info
-rwxrwxrwx    1 media    nogroup       531 Jul 22 12:15 master.info
-rwxrwxrwx    1 media    nogroup      1612 Jul 22 12:21 metadata.info
-rwxrwxrwx    1 media    nogroup       299 Jul 22 12:15 version.info
nas01:/media/in_process/# 

```

However, when I do this on my Ubuntu box, I get this:

```

scambro@fileserv01:/media/nas01/in_process/$ ls -all T17*
T174.wedt:
total 0

T175.wedt:
total 1799408
drwxrwxrwx  2 scambro scambro         0 Jul 22 20:31 .
drwxrwxrwx 12 scambro scambro         0 Jul 23 07:37 ..
-rwxrwxrwx  1 scambro scambro      3320 Jul 22 12:21 document.info
-rwxrwxrwx  1 scambro scambro       461 Jul 22 12:06 format.info
-rwxrwxrwx  1 scambro scambro 901266432 Jul 22 12:21 Layer 1_0000.00
-rwxrwxrwx  1 scambro scambro 901266432 Jul 22 12:15 Layer 1_0000.01
-rwxrwxrwx  1 scambro scambro  39436808 Jul 22 12:07 Layer 1.info
-rwxrwxrwx  1 scambro scambro       643 Jul 22 12:21 layers.info
-rwxrwxrwx  1 scambro scambro       531 Jul 22 12:15 master.info
-rwxrwxrwx  1 scambro scambro      1612 Jul 22 12:21 metadata.info
-rwxrwxrwx  1 scambro scambro       299 Jul 22 12:15 version.info
scambro@fileserv01:/media/nas01/in_process/$ 

```

I've chmod'd, chgrp'd, chown'd everything I can think of, re-mounted the share, etc, but for whatever reason, I cannot see this subdirectory as mounted on my Ubuntu box.  If I FTP from Ubuntu to the ReadyNas, I can ls -all and see the same output as if I had SSH'd directly to it.  

Any suggestions?  Thanks!

---

### Post by papibe on 2012-07-23
Hi scambro.

> **scambro said:**
> ```

//NAS01/media /media/nas01 nfs username=media,uid=1000,gid=1000 0 0

```

I've never seen this hybrid syntax to mount an nfs a remote directory. The //NASA01 is a smbfs/cifs sintax. For nfs I would use a syntax like this:
```
**NAS01:**/media /media/nas01 nfs username=media,uid=1000,gid=1000 0 0
```
Just a thought.
Regards.

---

### Post by scambro on 2012-07-24
> **papibe said:**
> Hi scambro,

I've never seen this hybrid syntax to mount an nfs a remote directory. The //NASA01 is a smbfs/cifs sintax. For nfs I would use a syntax like this:
```
**NAS01:**/media /media/nas01 nfs username=media,uid=1000,gid=1000 0 0
```
Just a thought.
Regards.

When I first changed it to exactly that it was giving me some mount errors, so I ended up making it like this:

```

NAS01:/media /media/nas01 nfs users,noauto,rw 0 0

```

However, I'm getting the same output where I see nothing in the T174.wedt folder from the Ubuntu box itself.

Thanks!

---

### Post by scambro on 2012-07-25
Ah!  Well, your advice that something wasn't right with my fstab entry got me poking around a bit more with that and I realized that my nfs setup wasn't working right.  While it worked before with however I had it, it clearly wasn't totally right.  I ended up doing this:

```

sudo apt-get install nfs-common

```

and set my fstab to this:

```

NAS01:/media /media/nas01 nfs defaults 0 0

```

I unmounted and mounted the share and now I can magically see those files that weren't showing before.  Thanks!

---

