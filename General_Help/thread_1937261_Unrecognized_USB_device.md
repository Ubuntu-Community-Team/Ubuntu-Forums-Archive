---
title: "Unrecognized USB device"
date: 2012-03-07
forum: General Help
---

### Post by andreismart on 2012-03-07
Hello everybody,

I have an A-DATA N005 USB 3.0 USB flash drive that is not browsable, neither on Windows 7, nor on Ubuntu. It is recognized on both operating systems, but on windows it cannot be seen neither in my computer nor in Disk Management. In ubuntu, it can be seen only in diskutility, which is unable to format it.

In diskutility, the "Format drive" option does not solve the problem. Despite the fact that it doesn't return any error, it doesn't change anything.

The "Format volume" option outputs the following error:

```

Error creating file system: helper exited with exit code 1: cannot mount /dev/sdb at /tmp/job-mkfs-hzaZb7: Invalid argument

Filesystem label=New Volume
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
262144 inodes, 1048575 blocks
52428 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1073741824
32 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736

Writing inode tables:  0/32 1/32 2/32 3/32 4/32 5/32 6/32 7/32 8/32 9/3210/3211/3212/3213/3214/3215/3216/3217/3218/3219/3220/3221/3222/3223/3224/3225/3226/3227/3228/3229/3230/3231/32done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 24 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```The fdisk -l output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004e307

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2584    19530752   83  Linux
/dev/sda2            2584        2842     1951745    5  Extended
/dev/sda5            2584        2842     1951744   82  Linux swap / Solaris

Disk /dev/sdb: 4294 MB, 4294965760 bytes
133 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 8246 * 512 = 4221952 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
root@hodorogandrei:~# df -TH
Filesystem    Type     Size   Used  Avail Use% Mounted on
/dev/sda1     ext4      20G   9.7G   9.1G  52% /
none      devtmpfs     517M   259k   517M   1% /dev
none         tmpfs     526M   254k   525M   1% /dev/shm
none         tmpfs     526M   328k   525M   1% /var/run
none         tmpfs     526M      0   526M   0% /var/lock

```the df -Th output:

```

Filesystem    Type     Size   Used  Avail Use% Mounted on
/dev/sda1     ext4      20G   9.7G   9.1G  52% /
none      devtmpfs     517M   259k   517M   1% /dev
none         tmpfs     526M   254k   525M   1% /dev/shm
none         tmpfs     526M   328k   525M   1% /var/run
none         tmpfs     526M      0   526M   0% /var/lock

```the lsusb output:
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 125f:105a A-DATA Technology Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```(no doubt that it is recognized in some way, but not mountable)

Is there any chance that my device can be brought to an usable state?
Any help would be appreciated.
Thank you in advance!

---

### Post by dcstar on 2012-03-08
> **andreismart said:**
> Hello everybody,

I have an A-DATA N005 USB 3.0 USB flash drive that is not browsable, neither on Windows 7, nor on Ubuntu.
.........
Any help would be appreciated.
Thank you in advance!

Chances are it is faulty.

---

### Post by Mark Phelps on 2012-03-09
I have USB 3.0 devices and have discovered, unfortunately, that support for them is sporadic, at best.

In Win7, I could not read or write USB 3.0 devices until I had upgraded both the drivers and the FIRMWARE for the on-board USB 3.0 controller.  Got the updates from the Sony Renesas site.  The original drivers and firmware installed in Win7 were unreliable, to say the least.

But in Ubuntu 11.10, it does not see the USB 3.0 controller, so I can't use the devices on it.

Could be you're encountering the same problems.  Would try a USB 2.0 stick to confirm that the USB port, controller, and drivers are working OK.

---

### Post by pavi_elex on 2012-03-09
If it is shown in the list by using
fdisk -l
It means, it may be recovered.
Install Gparted and see your pen-drive there.
If it is seen there, it means there is problem in partition table.
Click on
```
Device --> Create Partition table
```
May be, it will help.

---

