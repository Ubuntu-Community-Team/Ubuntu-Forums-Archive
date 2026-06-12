---
title: "not able to install any software, error?"
date: 2010-04-15
forum: General Help
---

### Post by abhilashm86 on 2010-04-15
From two days my karmic is not updating and not installing anything, it shows up following error, i tried update, --fix-misssing, but nothing seems to work? 

How do i correct this?

```
abhilash@abhilash:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 36 not upgraded.
Need to get 407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  grub
Install these packages without verification [y/N]? y
Err http://ubuntuarchive.hnsdc.com karmic/main grub 0.97-29ubuntu59
  404  Not Found
Failed to fetch http://ubuntuarchive.hnsdc.com/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
abhilash@abhilash:~$ 

```

---

### Post by viralmeme on 2010-04-15
[http://ubuntuforums.org/showthread.php?p=8731303](http://ubuntuforums.org/showthread.php?p=8731303)

---

### Post by john newbuntu on 2010-04-15
I am not sure if the software source 'http://ubuntuarchive.hnsdc.com/pool' exists, which is why you are getting the http 404 error.  Did you happen to add this at any point to software source/synaptic?

---

### Post by abhilashm86 on 2010-04-16
Now i tried diffrent mirror, its cs.iitk of india, its working fine!! :P

---

