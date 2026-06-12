---
title: "Can't access or even find files on my windows partition or windows partition itself !"
date: 2010-09-24
forum: General Help
---

### Post by reza1717s on 2010-09-24
Hi,
After several times install & reinstall,i got a stable dual boot vista / ubuntu 10.10.,but i can't access or even see   my windows partition from ubuntu,i installed my dual boot with wubu this time,in previous installation when i didn't use wubi , i didn't have such a problem & windows partition with all my files in it (windows files,media ,etc,) was easily accessible from "places" on ubuntu .
I already disabled windows firewall & other security options but nothing changed ! any solution please ?

---

### Post by IcewindDale on 2010-09-24
Hello.
Vista uses the ntfs file system and it looks to me your Ubuntu install still hasn't been configured to read/write on ntfs partitions.

Please refer to the following thread to install and configure ntfs support on Ubuntu 

[http://ubuntuforums.org/showthread.php?t=1575253](http://ubuntuforums.org/showthread.php?t=1575253)

---

### Post by bcbc on 2010-09-24
with wubi your windows files are accessible under the /host directory (Places, Computer, File system, host)

---

### Post by reza1717s on 2010-09-25
> **bcbc said:**
> with wubi your windows files are accessible under the /host directory (Places, Computer, File system, host)
I can access my files with this path,thanks for tip.

---

