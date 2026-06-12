---
title: "Problems with Linux image"
date: 2009-10-14
forum: General Help
---

### Post by r.osmanov on 2009-10-14
Hi, guys. I'm experiencing problems with Linux image since last upgrade to (restricted) version 2.6.28-15.  
 It also caused hassles with MySQL daemon startup. 
  
Recently, I upgraded to restricted Linux image 2.6.28-15 from 2.6.28-14 with failure. 
 I became unable to use apt due to the bug: 
 [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/425081](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/425081) 
  
Attempts to downgrade to the stable 2.6.28-11 version failed.  
 I've fixed it somehow by removing entries(files) of "linux-headers-2.6.28-15-generic*" from /var/lib/dpkg and subdirectories.  However, I still get the following warnings on  installation: 
  
```
dpkg: serious warning: files list file for package `linux-image-2.6.28-11-generic' missing, assuming package has no files currently installed. 
  
dpkg: serious warning: files list file for package `linux-headers-2.6.28-15-generic' missing, assuming package has no files currently installed. 
 
dpkg: serious warning: files list file for package `linux-restricted-modules-common' missing, assuming package has no files currently installed. 

``` But it is still not even the problem itself for me now. I have mysqld installed. But it doesn't create /var/run/mysqld folder each startup, and is not launched. It works, when I manually create the folder and start mysqld.  It is annoying.
  
So how can I downgrade to 2.6.28-11 kernel version and, at least, resolve the problem with mysqld automatic startup? 

 Regards.

---

