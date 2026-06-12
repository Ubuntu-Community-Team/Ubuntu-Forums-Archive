---
title: "Mount a volume"
date: 2010-12-25
forum: General Help
---

### Post by Naved on 2010-12-25
Hi....
I am Naved from India.
I have a problem in my ubuntu 10.01 that it can't load a drive/volume in ubuntu. When I tried, it said :
"Unable to mount location
Error mounting: mount: /dev/sda1: can't read superblock".

And when I boot my pc with 'Windows', it said :
"UNMOUNTABLE_BOOT_VOLUME" under a blue screen.

What can I do to solve this problem ?
Please help me, I've some important data on that drive.
And please answer me in simple way, coz I'm new on ubuntu.

---

### Post by karthick87 on 2010-12-25
Look at the following link,it is similar to your problem

[http://ubuntuforums.org/showthread.php?t=257031](http://ubuntuforums.org/showthread.php?t=257031)

---

### Post by Naved on 2010-12-25
no, thats a different thread.

---

### Post by dino99 on 2010-12-25
WARNING! Make sure file system is UNMOUNTED. (so boot on livecd)

sudo e2fsck /dev/sda1

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by Naved on 2010-12-25
bt where should I put this command :
"# dumpe2fs /dev/sda2 | grep superblock"

---

### Post by dino99 on 2010-12-25
> **Naved said:**
> bt where should I put this command :
"# dumpe2fs /dev/sda2 | grep superblock"
its to be run into a terminal

post #4 changed

---

### Post by Naved on 2010-12-25
it doesn't show anything.

---

### Post by dino99 on 2010-12-25
boot on livecd, then into a terminal:

sudo e2fsck /dev/sda1

then reboot on hdd

---

### Post by Naved on 2010-12-25
it shows following:


e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


And dont do anything.

---

### Post by dino99 on 2010-12-25
so what is really /dev/sda1 ? (check with a formatting tool like gparted, partedmagic, or else)

a linux system can boot on ext2, ext3, ext4 (mainly)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

