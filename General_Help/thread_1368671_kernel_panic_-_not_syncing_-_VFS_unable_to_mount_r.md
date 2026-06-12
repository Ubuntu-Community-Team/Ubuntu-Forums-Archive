---
title: "kernel panic - not syncing - VFS: unable to mount root fs on unknown block"
date: 2009-12-30
forum: General Help
---

### Post by algree on 2009-12-30
I was able to boot into 2.6.31-14
take note what linux-images show up 
mine was linux-image-2.6.31-16-generic

         linux-image-2.6.31-14-generic

so scroldown to linux-image-2.6.31-14  "enter"

it booted into desktop


                    the fix that worked for me



1) Go to System > Administration > Synaptic Package Manager

2) search for linux-image

3) Locate the package "linux-image-2.6.31-16-generic"

4) Select the check-box next to this package and choose "Mark for Reinstallation"

5) Apply this changes

6) Reboot your machine



            problem solved.



I hope it works for all of you as well.


algree

---

### Post by fanndian on 2009-12-31
> **algree said:**
> I was able to boot into 2.6.31-14
take note what linux-images show up 
mine was linux-image-2.6.31-16-generic

         linux-image-2.6.31-14-generic

so scroldown to linux-image-2.6.31-14  "enter"

it booted into desktop


                    the fix that worked for me



1) Go to System > Administration > Synaptic Package Manager

2) search for linux-image

3) Locate the package "linux-image-2.6.31-16-generic"

4) Select the check-box next to this package and choose "Mark for Reinstallation"

5) Apply this changes

6) Reboot your machine



            problem solved.



I hope it works for all of you as well.


algree

thanks for sharing your experience!
I have tried your methode, it works half way. but after I did as you told, I met a new problem. After reboot, I can't get into the system anymore, and it showed(as I made a photo) in below.
I have tried some command, and it told me that there is no kernel found(or anything like this, I can't remember it exactly). any idea how to solve this? 

[IMG]http://img196.imageshack.us/img196/7123/dsc00465vz.jpg[/IMG]

---

### Post by yduras on 2009-12-31
Success!

I was stuck at the same place as fanndian, until I tried the instructions found here [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24)

Note, though, that on my first few tries the boot failed and dropped me into a shell.

A helpful note in the full thread ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)) suggested that putting in sga1 in the first step might have had the system looking in the wrong partition.  swapping for sga2 did the trick!

---

