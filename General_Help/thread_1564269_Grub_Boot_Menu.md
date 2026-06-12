---
title: "Grub Boot Menu?"
date: 2010-08-30
forum: General Help
---

### Post by jameshampshire on 2010-08-30
yes im doing another post.
cause i want to know how to access the grub boot menu on ubuntu 10.04
cause due to a couple of days ago i had to reinstall ubuntu cause of this crappy program called STARTUP-MANAGER SCREWED my computer.
and wouldn't let me start up. it kept coming up with a message saying input signal is out of range so i had to reinstall ubuntu losing EVERYTHING.
i was thinking about rolling back to xp but i thought what the heck il give it another go.
how do i access this grub boot menu.
cause holding shift while starting the pc up does NOT work.

im using lucid lynx 10.04.

---

### Post by hhoyt on 2010-08-30
That would be grub2.
See if this helps ?
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Howard

btw, if you only have one linux partiton, I would recommend something standalone like parted magic.

You can then get into your linux system to access files.

Ex: linux on sda6

Parted Magic terminal:

sudo mount /dev/sda6 /mnt  << mount the linux partn on /mnt
nano /mnt/etc/fstab  <<< looking at fstab (r/o w/o sudo) on the failing linux system

---

### Post by philinux on 2010-08-30
> **jameshampshire said:**
> yes im doing another post.
cause i want to know how to access the grub boot menu on ubuntu 10.04
cause due to a couple of days ago i had to reinstall ubuntu cause of this crappy program called STARTUP-MANAGER SCREWED my computer.
and wouldn't let me start up. it kept coming up with a message saying input signal is out of range so i had to reinstall ubuntu losing EVERYTHING.
i was thinking about rolling back to xp but i thought what the heck il give it another go.
how do i access this grub boot menu.
cause holding shift while starting the pc up does NOT work.

im using lucid lynx 10.04.

It's a shame you didn't post about the problem before reinstalling. That could easily have been fixed. The out of range error to do with the monitor resolution. 
You must have specified a resolution in startup manager that was not available I'm guessing. Reinstalling is usually a very last resort.

Having /home on it's own partition can also make reinstalling that much easier.

For grub2 see this link. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jameshampshire on 2010-08-30
> **philinux said:**
> It's a shame you didn't post about the problem before reinstalling. That could easily have been fixed. The out of range is the monitor resolution. 
You must have specified a resolution in startup manager that was not available I'm guessing. Reinstalling is usually a very last resort.

Having /home on it's own partition can also make reinstalling that much easier.

damn! are you serious.
i posted one on here and waited for ages and got no reply.
so i thought no one had a solution and my only way was to reinstall.
i usually back everything on my harddrive anyway.
i was just annoyed my internet limit is like 12gb's.
and it took me ages to get ubuntu the way i wanted as in themes, applications and etc.
took me DAYS! and i installed that program stupid really cause i didnt even really know what it was to begin with, then one day i noticed my ubuntu boot screen has gone haywire, like it has now to for some unknown reason? if you can help me out.
it just looks pixelated and ugly not like high def like when you first install ubuntu.

---

### Post by jameshampshire on 2010-08-30
forgot to mention that after i noticed my boot screen went ugly.
i tampered with boot up manager change the resolution and that's when it wouldn't let me in the pc.

---

### Post by hhoyt on 2010-08-30
you might try booting your install disk.
Then from terminal
sudo su
blkid
find your ubuntu partition
mount /dev/sdax /mnt                     where x is # of ubuntu partition
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
chroot /mnt
/usr/lib/bum/bum

---

