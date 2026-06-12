---
title: "Grub2 can't see Windows 7 bootloader"
date: 2009-10-30
forum: General Help
---

### Post by themusicalduck on 2009-10-30
I did a fresh install of 9.10 yesterday and everything went fine. Grub2 detected my other operating systems (Win7 and OS X) and they were listed in the menu on bootup (although I didn't get a chance to test them).

Since then, I thought I would change the image background which required I use the update-grub command so that it could see the new image. This worked fine, but it seems to have taken out the other entries for Windows and OS X.

Using the command sudo os-prober only comes up with one entry: 

/dev/sdc1:Ubuntu 9.04 (9.04):Ubuntu:linux

which is an installation of Ubuntu Studio I installed onto a separate drive.

Is there any way to get them back?

---

### Post by themusicalduck on 2009-10-30
bump

---

### Post by themusicalduck on 2009-10-30
It seems like grub2 can't see my drives unless I delete the raid array they are in (I had this problem with the installer not seeing my drives either)

So I figured if I boot into the live CD while the raid is disabled, I might be able to update grub from there.

While running os-prober from the live CD, while the raid array is deleted, then it does see the other systems, but when trying to run update-grub while using the method outlined here - [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I get this error:

```
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
```

Any way to fix this? Seems like I'm so close to getting it figured.
os-prober gives the same error while I am chrooted in /mnt.

---

### Post by Ilalmi on 2009-11-01
Following the outlined method you need to mount proc and sys, too.
Do a ```
sudo mount -t proc /proc /mnt/proc
``` and a
```
sudo mount --bind /sys /mnt/sys
``` before the chroot. The errors should disappear.

Hope that gets you any further.

---

### Post by themusicalduck on 2009-11-02
Thanks for the reply.

In the end I found that I was being effected by this bug -https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054

and used the workaround on there to fix my problem :)

---

