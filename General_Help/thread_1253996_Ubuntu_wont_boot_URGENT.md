---
title: "Ubuntu wont boot URGENT"
date: 2009-08-30
forum: General Help
---

### Post by rp181 on 2009-08-30
I have been using Ubuntu 9.04 for a long time now. Today, i turned on my computer, and let ubuntu run the routine check. That failed, and it said to run fsck manually. I went on to the ubuntu live CD, and used GParted to check the file system. After that, i rebooted. Now i am getting this (not exactly):

Grubv1.5 Starting, Please Wait
Error 25

And nothing happens. What should i do? I only have 1 hardrive, and i am booting from that.

---

### Post by mustafa-linux on 2009-08-30
error 25 means that your hard disk is failing, but any way this may work:
from the liveCD menu and boot into the rescue mode, then follow the instructions and then at the rescue shell prompt type 

grub-install /dev/sda1

---

### Post by rp181 on 2009-08-30
On my CD, the only options are Try ubuntu, Install Ubuntu, Check CD for Defects, Test Memory, Boot from first Hard disk.

---

### Post by running_rabbit07 on 2009-08-30
The Alternate installer disk is the one that has that option. You can fix grub using the grub link in my signature.

---

### Post by rp181 on 2009-08-30
Theres alot of stuff on that page, which exactly do i need to do?

---

### Post by running_rabbit07 on 2009-08-30
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=715317"). It may be of some help.

---

### Post by rp181 on 2009-08-30
no luck

i tried the fsck command, and this is what i get:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda1


And when trying to mount the hard-drive, i get this error:

Cannot mount volume
Unable to mount the volume

Details:
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error In some cases useful info is found in syslog - true dmesg | tail or so

---

### Post by rp181 on 2009-08-31
Bump any ideas? It seems i need to reinstall grub from what ive gathered, but i can not mount the hard drive from the live CD. Is there any way i can force mount? the -o force does not work/

---

