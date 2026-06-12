---
title: "Not able to configure quota system on LINUX"
date: 2010-09-02
forum: General Help
---

### Post by anirudhtomer on 2010-09-02
hi everyone ):P

I am trying to enable quota on my /home directory for understanding how quota works.
I have not made a separate partition for my /home.
The logical name of the directory "/" is /dev/sda5 on my machine

I have just now added this entry 
/dev/sda5               /home                   ext3    defaults,usrquota 0 0
in my /etc/fstab file which looks like this now.

```
[root@localhost ~]# cat /etc/fstab 
LABEL=/1                /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               /home                   ext3    defaults,usrquota 0 0
LABEL=SWAP-sda7         swap                    swap    defaults        0 0
[root@localhost ~]# 
```then I typed this command

```
[root@localhost ~]# mount -o remount /home
mount: /home not mounted already, or bad option
[root@localhost ~]# quotacheck -c /home/
quotacheck: Mountpoint (or device) /home not found.
quotacheck: Can't find filesystem to check or filesystem not mounted with quota option.
[root@localhost ~]# 
```I tried above things even after restarting my machine & while my machine was booting I saw a few lines which said that "quota not enabled on /home"

I tried to search this on Google as well but didn't get any satisfactory results.
I usually post questions only when I have do not get results by checking earlier threads on various forums. 

If you find I am going the wrong way then please show me the right track.
Thanks in advance.:D

---

### Post by anirudhtomer on 2010-09-02
bump. Sometimes a whole day goes bad like this. Anyways I am going to sleep now.
Hoping to see some replies when I come back.

---

