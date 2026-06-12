---
title: "How I killed my system"
date: 2011-03-23
forum: General Help
---

### Post by MichaelGld on 2011-03-23
The problem: after selecting the OS from the grub menu, I get a dark screen, sometimes with an inch-high band of video garbage across the top of the screen, nothing more.

What I did: I was having this issue, but only with the .30 kernel I had downloaded from the Update Manager. Another user had me put "nomodeset" in the boot parameters, which worked. I tried to install the latest nVidia driver from their website which was a .run file. The instructions I found in this forum started with the instruction to quit X by pressing ctrl-alt-F1. When I did this, I got the blank screen.

Then I read somewhere that they had a fix for problems with nVidia drivers. That fix consisted of adding a PPA with lots of updates. Foolishly, I installed all those. When I rebooted, I have no video beyond the grub menu (except for Windows). I have the four latest kernels still on my system, none of which work.

Now, I have a backup on an external drive. I booted the 10.04 cd and ran it as a live cd. It can see my external drive, but it completely locks me out of the linux partitions on my hard drive. It occurred to me I could do a fresh install, then run the backup, but I'd rather not do that. 

My System:
nVidia GeForce 7300 GS
EVGA 590SLI motherboard
Two internal hard drives (second drive has linux, first drive Windows XP)
2G RAM
1TB external firewire drive
Samsung Synchmaster 205BW monitor

I would greatly appreciate any help on this matter.

---

### Post by hangfire on 2011-03-23
Any fix of your existing system (short of restoring an image backup) involves getting access to the boot and/or root partition, and changing the boot line and/or your xorg.conf.

You need to determine why you can't access your hard drive partitions. Are they encrypted? Do they not mount because they are dirty? Exactly what error messages do you get?

Generally you should be able to find and mount partitions as such:

```
# From live CD root prompt
fdisk -l
#Find the partition you want
mkdir /tmp/boot
#Next line may need different device and/or filesystem type
fsck /dev/sda1
mount /dev/sda1 /tmp/boot
```

At that point you should be able to cd into the partition.

---

### Post by MichaelGld on 2011-03-23
> **hangfire said:**
> Any fix of your existing system (short of restoring an image backup) involves getting access to the boot and/or root partition, and changing the boot line and/or your xorg.conf.

You need to determine why you can't access your hard drive partitions. Are they encrypted? Do they not mount because they are dirty? Exactly what error messages do you get?

Generally you should be able to find and mount partitions as such:

```
# From live CD root prompt
fdisk -l
#Find the partition you want
mkdir /tmp/boot
#Next line may need different device and/or filesystem type
fsck /dev/sda1
mount /dev/sda1 /tmp/boot
```At that point you should be able to cd into the partition.
If I try to do a cd /home/mike for example, I get an error that reads, "no such file or directory";. I ran fdisk -l and I saw the partitions:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482347008   83  Linux
/dev/sda2           60050       60802     6037505    5  Extended
/dev/sda5           60050       60802     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8235e066

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60952    30719776+   7  HPFS/NTFS
/dev/sdb2           60953       61968      512064    f  W95 Ext'd (LBA)
/dev/sdb3           61969      366730   153600048    7  HPFS/NTFS
/dev/sdb4          366731      969018   303553152    7  HPFS/NTFS
/dev/sdb5           60953       61968      512032+   7  HPFS/NTFS

I tend to think that my install is not broken per se, but something bad has happened to the video driver that prevents me from seeing anything. I hope that makes sense.

---

### Post by dragonfly41 on 2011-03-23
I'm guessing here .. and I'm a newbie also feeling my way .. but when I boot up into dual boot mode (wubi installed inside Windows as c:/ubuntu) I quickly press ESC every time (within 3 seconds to avoid a full installation) and a menu pops up.

I only use Demo mode in this menu but the full menu is

Normal mode
Safe graphic mode
ACPI workarounds
Verbose mode
Demo mode


So the question is can you get into safe graphic mode which might have reduced set of video drivers.?

---

### Post by MichaelGld on 2011-03-24
> **hangfire said:**
> Any fix of your existing system (short of restoring an image backup) involves getting access to the boot and/or root partition, and changing the boot line and/or your xorg.conf.

You need to determine why you can't access your hard drive partitions. Are they encrypted? Do they not mount because they are dirty? Exactly what error messages do you get?

Generally you should be able to find and mount partitions as such:

```
# From live CD root prompt
fdisk -l
#Find the partition you want
mkdir /tmp/boot
#Next line may need different device and/or filesystem type
fsck /dev/sda1
mount /dev/sda1 /tmp/boot
```At that point you should be able to cd into the partition.
Ok, I was able to take the steps you suggested. Here is the output,

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482347008   83  Linux
/dev/sda2           60050       60802     6037505    5  Extended
/dev/sda5           60050       60802     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8235e066

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60952    30719776+   7  HPFS/NTFS
/dev/sdb2           60953       61968      512064    f  W95 Ext'd (LBA)
/dev/sdb3           61969      366730   153600048    7  HPFS/NTFS
/dev/sdb4          366731      969018   303553152    7  HPFS/NTFS
/dev/sdb5           60953       61968      512032+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa5b8c8f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS
ubuntu@ubuntu:~$ mkdir /tmp/boot
ubuntu@ubuntu:~$ fsck dev/sda1
fsck from util-linux-ng 2.17.2
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /tmp/boot
ubuntu@ubuntu:~$ cd /tmp/boot
ubuntu@ubuntu:/tmp/boot$ ls -l
total 136
drwxr-xr-x   2 root root  4096 2011-03-11 17:43 bin
drwxr-xr-x   3 root root  4096 2011-03-22 02:18 boot
drwxr-xr-x   2 root root  4096 2010-07-04 22:28 cdrom
-rw-r--r--   1 root root  2549 2010-10-31 03:02 conky.conf
drwxr-xr-x   4 root root  4096 2010-04-29 12:19 dev
drwxr-xr-x 160 root root 12288 2011-03-24 01:19 etc
drwxr-xr-x   4 root root  4096 2011-02-09 19:02 home
lrwxrwxrwx   1 root root    33 2011-03-17 17:19 initrd.img -> boot/initrd.img-2.6.32-30-generic
lrwxrwxrwx   1 root root    33 2011-03-01 17:17 initrd.img.old -> boot/initrd.img-2.6.32-29-generic
drwxr-xr-x  22 root root 12288 2011-03-17 17:18 lib
drwx------   2 root root 16384 2010-07-04 22:23 lost+found
drwxr-xr-x   4 root root  4096 2011-03-24 01:04 media
drwxr-xr-x   3 root root  4096 2011-01-04 19:29 mnt
drwxr-xr-x   8 root root  4096 2011-02-26 19:50 opt
drwxr-xr-x   2 root root  4096 2010-04-23 10:11 proc
drwx------  31 root root  4096 2011-03-21 22:37 root
drwxr-xr-x   2 root root  4096 2011-03-17 17:18 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 21:55 selinux
-rw-r--r--   1 root root  2272 2010-07-13 23:56 snapscan.conf
drwxr-xr-x   3 root root  4096 2010-09-27 15:38 srv
drwxr-xr-x   2 root root  4096 2010-03-30 07:17 sys
drwxrwxrwt   5 root root 20480 2011-03-24 01:18 tmp
drwxr-xr-x  12 root root  4096 2010-07-05 00:01 usr
drwxr-xr-x  15 root root  4096 2010-04-29 12:26 var
lrwxrwxrwx   1 root root    30 2011-03-17 17:19 vmlinuz -> boot/vmlinuz-2.6.32-30-generic
lrwxrwxrwx   1 root root    30 2011-03-01 17:17 vmlinuz.old -> boot/vmlinuz-2.6.32-29-generic

```However, the system won't let me cd to the root folder:
```

ubuntu@ubuntu:/tmp/boot$ cd /tmp/boot/root
bash: cd: /tmp/boot/root: Permission denied
ubuntu@ubuntu:/tmp/boot$ sudo cd /tmp/boot/root
sudo: cd: command not found
ubuntu@ubuntu:/tmp/boot$ 

```I need to get to /home, but can't.
I also had the thought that maybe I could create a new partition on sda1 and intall a fresh copy there. Your thoughts?

---

### Post by MichaelGld on 2011-03-24
> **dragonfly41 said:**
> I'm guessing here .. and I'm a newbie also feeling my way .. but when I boot up into dual boot mode (wubi installed inside Windows as c:/ubuntu) I quickly press ESC every time (within 3 seconds to avoid a full installation) and a menu pops up.

I only use Demo mode in this menu but the full menu is

Normal mode
Safe graphic mode
ACPI workarounds
Verbose mode
Demo mode


So the question is can you get into safe graphic mode which might have reduced set of video drivers.?
I'm not using WUBI, there is no menu of choices as you described. Thanks for trying, though.

---

### Post by sdowney717 on 2011-03-24
can you boot to the command prompt?
at grub dont select the normal gui boot.
boot recovery and then when the menu comes up to try to fix X, dont, just boot to the root prompt.
Now, if you know where the nvidia.run file is located, just go there.

if your in root of root directory, then 
cd home
cd user name
ls to list files (ls n* will list all files starting with n)
execute nvidia.run by typing in the file name like this
./nameofnvidiadriver.run 
if your in the directory where that nvidia file exists, and it is executable, then it will setup the driver.
skip threw any warnings and let it install then reboot.

---

### Post by MichaelGld on 2011-03-24
> **sdowney717 said:**
> can you boot to the command prompt?
at grub dont select the normal gui boot.
boot recovery and then when the menu comes up to try to fix X, dont, just boot to the root prompt.
Now, if you know where the nvidia.run file is located, just go there.

if your in root of root directory, then 
cd home
cd user name
ls to list files (ls n* will list all files starting with n)
execute nvidia.run by typing in the file name like this
./nameofnvidiadriver.run 
if your in the directory where that nvidia file exists, and it is executable, then it will setup the driver.
skip threw any warnings and let it install then reboot.

All the linux selections from the grub menu leave me with a blank screen, although I did get a partial image of my desktop while playing with the boot parameters. Unfortunately, mouse clicks and keyboard input changed nothing. I even had to shut down with the power button on my pc. So I cannot boot to a command prompt from the grub menu.

---

