---
title: "initramfs file problem !"
date: 2012-01-21
forum: General Help
---

### Post by yar0n on 2012-01-21
why i cant initiate the  
initramfs file
[i have ubuntu server 11.04 
and its do just dont work!
this is the command that i wrote :
 
$ cp initrd.img-2.6.32-14-generic-pae /tmp/initrd.img-2.6.32-14-
generic-pae.gz[/LEFT]
 
and this is what he write:
"not such a file or directory"
and i check a 100000 times and this is the command !
please help!:(

---

### Post by varunendra on 2012-01-23
> **yar0n said:**
> 
$ cp initrd.img-2.6.32-14-generic-pae /tmp/initrd.img-2.6.32-14-
generic-pae.gz[/LEFT]
 
and this is what he write:
"not such a file or directory"
Which directory you were in (in terminal) when you ran this command?

By default these files are located in /boot directory. So you have to be in that directory (cd /boot) if you don't want to type full path of the file (/boot/initrd.img-.....).

But why are you trying to copy this file to /tmp? Can you provide link to the guide or tutorial which you are following? I am asking because playing around with this directory (/boot) without properly understanding what you are doing can screw up the installation.

---

