---
title: "Can't use Ubuntu"
date: 2012-07-20
forum: General Help
---

### Post by barrdakota on 2012-07-20
Yesterday when I turned my laptop on, Ubuntu wasn't working at all. It sent me to a black screen where I have to choose what Ubuntu I want to run. I chose the first one: Ubuntu, with Linux 2.6.35-32 Generic. Recovery mode also doesn't work.

Once I click on the first one, it sends me to another black screen. This one with a long message:

[     3.527172] Slow work thread pool: Starting up
[     3.532936] Slow work thread pool: Ready
[     3.538598] acpi device: 0a registered as cooling-device1
[     3.539054] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVideo:01/input/input4
[     3.539302] ACPI: VideoDevice [GFXO] (multi-head: yes  rom:no post: no
[     3.539348] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02:0 on minor 0
No init found. Try passing init= bootary.
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) 

Right now I am currently using a Ubuntu installation disk on the Try It option. I tried using my installation disk to re-install Ubuntu, but it won't let me. I click install, and then it sends me to a screen with some options. When I press forward (to install), my computer freezes and won't let me do anything.

---

### Post by ajgreeny on 2012-07-20
You may have a filesystem problem so first thing I would do, having got that busybox error is to boot to the live CD desktop, then in a terminal run ```
sudo e2fsck /dev/sda1
```assuming sda1 is your ubuntu root partition.  Make a note of any error messages that appear, and copy them here.

You will need to make sure that the root partition is unmounted before you can run the filesystem check on it, but it should be if you have not specifically mounted it for other purposes.

---

### Post by barrdakota on 2012-07-20
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?



That's what I got when I did that. How do I unmount it?

---

### Post by ajgreeny on 2012-07-20
> **barrdakota said:**
> ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?



That's what I got when I did that. How do I unmount it?
Command ```
sudo umount /dev/sda1
``` should do it, then try that first e2fsck command again.

---

### Post by barrdakota on 2012-07-20
Got the same message.

sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 


Here's my information on sda1:

File System: ext4
Size: 227.03 Gib
Used: 14.48 GiB (6%)
Unused: 212.54 GiB (94%)
Flags: boot

Path: /dev/sda1
Status: not mounted
Label: 
UUID: e42e0c8c-5aac-43d3-ae14-1bf1630ed6d2

First Sector: 2048
Last Sector: 476108799
Total Sectors: 476106752

---

### Post by ajgreeny on 2012-07-20
OK, let's see the output of command ```
sudo fdisk -l
```Maybe it is a logical partition in the same extended partition as swap,

---

### Post by oldfred on 2012-07-20
We have seen a couple of cases where the partition says it is mounted in Ubuntu even when it is not. Last one was from a crash with Samba, I think. The work around was to run fsck from a different Linux. 

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
Terminate with "kill [pid]" or "kill -9 [pid]

If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by barrdakota on 2012-07-21
ajgreeny, here is what I get.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000256c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris

---

### Post by barrdakota on 2012-07-21
> **oldfred said:**
> We have seen a couple of cases where the partition says it is mounted in Ubuntu even when it is not. Last one was from a crash with Samba, I think. The work around was to run fsck from a different Linux. 

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
Terminate with "kill [pid]" or "kill -9 [pid]

If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz


I inherited this computer with this operating system already on it. I am a VERY beginner when it comes to this system. Please dumb this down for me. :P

---

### Post by oldfred on 2012-07-21
Instead of using a Ubuntu LIveCD, you use a Slitaz liveCD. It does work a bit differently, but you just want to run the e2fsck commands.

 Something about Ubuntu not clearing the mount and other systems like Slitaz either clearing it or ignoring it and then working. Only suggest Slitaz as it worked for others and is a small system so easy to download.

---

