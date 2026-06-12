---
title: "Time machine permissions problem"
date: 2009-12-12
forum: General Help
---

### Post by sumone on 2009-12-12
Hi

I am using an external hard drive for backup and data storage. It is partitioned to allow use with Windows 7,OS X Leopard and shared data. My mac book pro laptop has died and I'm trying to access the time machine backup via ubuntu. I was hoping to chown the folder containing the time machine backup and see if it contained any recoverable data. However I dont seem to be able to even navigate to the folder, the ternminal output follows-
david@pc-ubuntu:/$ ls 
bin    etc             lib         mnt   sbin     tmp      vmlinuz.old 
boot   home            lost+found  opt   selinux  usr 
cdrom  initrd.img      man1        proc  srv      var 
dev    initrd.img.old  media       root  sys      vmlinuz 
david@pc-ubuntu:/$ cd media 
david@pc-ubuntu:/media$ ls 
cdrom  cdrom0  DATA  Dell Win7 backup  mac bakup 
david@pc-ubuntu:/media$ cd mac bakup 
bash: cd: mac: No such file or directory 
david@pc-ubuntu:/media$ 

Any suggestions appreciated, I'm researching fixing the mbp on other forums.

TIA
David

---

### Post by fleenort on 2009-12-12
>  ...
david@pc-ubuntu:/media$ cd mac bakup 
bash: cd: mac: No such file or directory 
david@pc-ubuntu:/media$ 



This:
```
cd mac bakup
``` 

is causing it to try and change directory to a directory called "mac" .. which obviously doesn't exist.

This:
```
cd "mac bakup"
``` 

will cause it to change directory to "mac bakup". This is why it's best to use capitals rather than spaces, i.e. "macBakup".

---

