---
title: "can't encrypt /tmp via /etc/crypttab"
date: 2012-07-04
forum: General Help
---

### Post by cesera on 2012-07-04
Running Kubuntu 12.04

When I add the following line to my crypttab file:
```
crypttemp1 /dev/sda7 /dev/urandom tmp,cipher=aes-cbc-essiv:sha256
```and this to fstab:```
/dev/mapper/crypttemp1      /tmp         ext2    defaults      0     2
```I can't restart my computer anymore, it keeps telling me it is waiting for /tmp to get mounted. Am I doing something wrong or have I run into something broken here?

Any help would be much appreciated.

---

### Post by cesera on 2012-07-18
bump

---

### Post by DarkDead on 2012-12-30
The following might solve your issue:

> The correct incantation in crypttab should look like this:
```
crypttmp /dev/mapper/vg_doulos-tmp /dev/urandom precheck=/bin/true,tmp,size=256,hash=sha256,cipher=aes-cbc-essiv:sha256
```
The most important part was the precheck=/bin/true. The reason why /tmp wasn't mounting was that cryptsetup was failing due to a precheck. 

by Avery Chan from [How do I encrypt my /tmp directory? - Ask Ubuntu]("http://askubuntu.com/a/146641")

---

