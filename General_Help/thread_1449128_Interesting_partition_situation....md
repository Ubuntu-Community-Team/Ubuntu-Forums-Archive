---
title: "Interesting partition situation..."
date: 2010-04-07
forum: General Help
---

### Post by eveningsky339 on 2010-04-07
I've been running a dual-boot configuration with XP and Karmic for quite some time.  However, I haven't booted into XP in ages, so I've decided to free up that other half of my hard drive by simply erasing that NTFS partition via GParted.

So, I have a ~150 GB ext4 partition with Ubuntu under /dev/sda2, and 150 GB of unallocated space.  And.......  I can't increase the size of Ubuntu.  It's apparently "stuck" inside the confines of dev/sda2.  However, I cannot increase the size of that either.

Half my hard disk is not being used, and I would like to increase the size of the ext4 Ubuntu partition to utilize the unused half.

---

### Post by sanderd17 on 2010-04-07
Do you try to change your partitions from within Ubuntu? You should know that you can't change mounted partitions. If you want to change that partition, you should boot with your live cd.

---

### Post by eveningsky339 on 2010-04-07
> **sanderd17 said:**
> Do you try to change your partitions from within Ubuntu? You should know that you can't change mounted partitions. If you want to change that partition, you should boot with your live cd.
I'm operating from the Live CD as of this moment.  :)  Everything appears to be unmounted.

---

### Post by tom.swartz07 on 2010-04-07
> **eveningsky339 said:**
> I've been running a dual-boot configuration with XP and Karmic for quite some time.  However, I haven't booted into XP in ages, so I've decided to free up that other half of my hard drive by simply erasing that NTFS partition via GParted.

So, I have a ~150 GB ext4 partition with Ubuntu under /dev/sda2, and 150 GB of unallocated space.  And.......  I can't increase the size of Ubuntu.  It's apparently "stuck" inside the confines of dev/sda2.  However, I cannot increase the size of that either.

Half my hard disk is not being used, and I would like to increase the size of the ext4 Ubuntu partition to utilize the unused half.

Congrats on ditching the crap OS! :P

It sounds as though you might have Ubuntu installed inside of an extended partition. Could you post the output of ```
sudo fdisk -l
```
or maybe a screencap of gparted?

Ideally, what you would need to do is simply extend the "extended" partition to the beginning of the drive and then expand your ubuntu files there.

---

### Post by eveningsky339 on 2010-04-07
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00048d52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           19508       38913   155878695    5  Extended
/dev/sda5   *       19508       38120   149508891   83  Linux
/dev/sda6           38121       38913     6369741   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by oldfred on 2010-04-07
To move it you would have to first move the extend partition then move sda2. I do not recommend moving the start of a bootable partition, it sometimes can lead to boot issues. It also is very slow as you have to move all the data.

I would suggest creating a new EXT3 or EXT4 partition and use it for data or move home into it. I like separate data partitions and linking the folders into /home so I see it the same but the data is in another partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by 2hot6ft2 on 2010-04-07
I know you said they appear to be unmounted but did you right click on the swap partition and select SwapOff? Since if it's inside the extended partition it would be mounted by default and therefore locking the extended partition making it impossible to make changes to it.

---

### Post by eveningsky339 on 2010-04-07
Here's a screenie:

[IMG]http://i21.photobucket.com/albums/b282/eveningsky339/Screenshot.png[/IMG]

---

### Post by eveningsky339 on 2010-04-07
> **2hot6ft2 said:**
> I know you said they appear to be unmounted but did you right click on the swap partition and select SwapOff? Since if it's inside the extended partition it would be mounted by default and therefore locking the extended partition making it impossible to make changes to it.
Sweet Gravy, it worked!  Thanks a bunch!  :guitar:

---

### Post by 2hot6ft2 on 2010-04-07
> **eveningsky339 said:**
> Sweet Gravy, it worked!  Thanks a bunch!  :guitar:
LOL. Sometimes it's the simple things we overlook. You're welcome.

---

