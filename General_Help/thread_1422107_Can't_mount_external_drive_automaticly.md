---
title: "Can't mount external drive automaticly"
date: 2010-03-05
forum: General Help
---

### Post by nomko on 2010-03-05
Hi there,

I'm having a problem with my external drive under Ubuntu 9.04. After a reboot Ubuntu seems no longer to mount the the 3 seperate partitions on my external drive. I've added some screenshots of my fstab file which i tried just to let Ubuntu mount my drives, without any results!

Can someone help me? If more info is requered, please let me know!

Many thanks in advance!
Nomko

---

### Post by oldfred on 2010-03-05
This is my entry but I mount it where it will not be seen and link the folders in data to home. Some say UUID's are better or using the label to mount.

If this do you get any error messages? 
mount -a


# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  


Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog way of linking:
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by efflandt on 2010-03-05
What is the output of 
**ls -l /media**
**mount | grep media**?

---

### Post by nomko on 2010-03-06
> **efflandt said:**
> What is the output of 
**ls -l /media**
**mount | grep media**?

Output of commando _**ls -l /media:**_

```

totaal 32
lrwxrwxrwx  1 root  root     6 2010-03-02 19:16 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2010-03-02 19:16 cdrom0
drwxrwxr-x 14 nomko nomko 4096 2010-03-03 18:17 Documenten
drwxr-xr-x  4 root  root  4096 2009-10-03 19:40 Email
drwxrwxr-x 16 nomko nomko 4096 2010-01-20 20:47 Multimedia
drwxrwxr-x  4 nomko nomko 4096 2009-11-26 14:29 NNTPGrab
drwxr-xr-x  2 root  root  4096 2010-03-04 17:36 sdc1
drwxr-xr-x  2 root  root  4096 2010-03-05 07:18 sdc2
drwxr-xr-x  2 root  root  4096 2010-03-05 07:18 sdc3

```

Output of commando _**mount | grep media**_

```

/dev/sdb1 on /media/NNTPGrab type ext3 (rw,relatime)
/dev/sdc1 on /media/Email type ext3 (rw)
/dev/sdc2 on /media/Multimedia type ext3 (rw)
/dev/sdc3 on /media/Documenten type ext3 (rw)

```

---

### Post by efflandt on 2010-03-07
Judging from that, they appear to be mounted read/write where you told it to mount them.  Although, your fstab entries for them (2nd image) are missing any options, and numbers of whether to dump, or when to fsck.  So they are apparently are mounted with defaults (rw, suid, dev, exec, auto, nouser, async) and not dumped or checked by fsck to make sure those partitions are still good.

In a terminal see **man fstab** and **man mount** (FILESYSTEM INDEPENDENT MOUNT OPTIONS)

After the options in fstab you would typically have 0 2 (zero to dump, and 2 to fsck those after main file system).

You should be able to access /media/Documenten and /media/Multimedia, but Email is owned by root, so permissions there would be limited by directory permissions.  Your user nomko might not be able to write to it unless ownership and/or permissions of directories are correct.

---

