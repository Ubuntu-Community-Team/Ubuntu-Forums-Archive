---
title: "HDD (NTSF) won't run executables."
date: 2012-03-08
forum: General Help
---

### Post by Zephilinox on 2012-03-08
I want to run some C++ code I've compiled on my other HDD which is  formatted in NTSF, but it won't allow me to change any of the  permissions for files on that HDD, is there any way around it?

---

### Post by TeoBigusGeekus on 2012-03-08
There's no way for an ntfs file system to understand linux permissions.
Move your file to a linux file system.

---

### Post by jerome1232 on 2012-03-08
Check out this thread 

[http://ubuntuforums.org/showthread.php?t=1937330](http://ubuntuforums.org/showthread.php?t=1937330)

To sum up you need to mount the device so that files on it have execute permissions.

---

### Post by jerome1232 on 2012-03-08
> **TeoBigusGeekus said:**
> There's no way for an ntfs file system to understand linux permissions.
Move your file to a linux file system.

Not true, Linux style permissions for MS file systems are decided by the mount options you pass.

---

### Post by TeoBigusGeekus on 2012-03-08
> **jerome1232 said:**
> Not true, Linux style permissions for MS file systems are decided by the mount options you pass.

Yes, of course, he could mount the hd with a umask=000 option, but I've just suggested the simplest method.

---

### Post by Zephilinox on 2012-03-08
> Check out this thread 

[http://ubuntuforums.org/showthread.php?t=1937330](http://ubuntuforums.org/showthread.php?t=1937330)

To sum up you need to mount the device so that files on it have execute permissions. 	

thanks, this will save me a lot of time.

---

