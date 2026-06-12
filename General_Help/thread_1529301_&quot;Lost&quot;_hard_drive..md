---
title: "&quot;Lost&quot; hard drive."
date: 2010-07-12
forum: General Help
---

### Post by 420 on 2010-07-12
Hey all,

I've been using Ubuntu 10.4 for about a week now & still getting to grips with it.
I think I have misplaced a hard drive. Since I done a bunch of updates It doesn't appear in the Places menu any more. I can see it active in "Disk Utility" but cannot mount it. If I boot with a random CD/DvD inserted the lost drive will appear in the menu & I can browse it fully but without a CD/DvD inserted it will not.

Any idea what I've done & how can I fix it?

---

### Post by bcbc on 2010-07-12
Go to a terminal (System, Accessories, Terminal) and run 
```
sudo fdisk -l
```
Note that is a small L not a 1.

Copy and paste the output from the commands. Then say which drive you are missing.


Edit: by the way, if you installed with WUBI, then the partition you installed it on will be mounted under /host and it won't let you mount it again.

---

### Post by 420 on 2010-07-12
Nope, didn't use Wubi, my net is a little slow & downloading 699mb would have taken a few days. I bought a cd off 8days, turned up next day so quite a result. :)

Anyways, it's the 500GB one that I can't always see.

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd149d149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ade8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9332    74952704   83  Linux
/dev/sdb2            9332        9734     3228673    5  Extended
/dev/sdb5            9332        9734     3228672   82  Linux swap / Solaris
Well, the full story is that I installed onto the 80GB drive, found Ubuntu does pretty much what I want from an o/s so I whipped the 500GB drive out of my other PC to transfer some files across and as above it was working fine until a few days ago.

---

### Post by bcbc on 2010-07-12
That's a strange one... I don't have any idea. When you click on Places, Computer, does it show up there?

In the meantime, until you get it resolved, you should be able to mount it manually from Terminal

```
sudo mount /dev/sda1 /mnt
nautilus /mnt
```

---

### Post by betrunkenaffe on 2010-07-12
I'm assuming it's disappeared from the automount list.

/dev/sda1 * 1 60800 488375968+ 7 HPFS/NTFS << Windows

Check out these instructions and see if they help.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by 420 on 2010-07-12
> **bcbc said:**
> That's a strange one... I don't have any idea. When you click on Places, Computer, does it show up there?

In the meantime, until you get it resolved, you should be able to mount it manually from Terminal

```
sudo mount /dev/sda1 /mnt
nautilus /mnt
```

sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy

nautilus /mnt
Whatever that is supposed to do, it does the job. It will open the file browser & I can access the drive. Still doesn't show up places though.

In Places - Computer I have four objects; two from my usb modem (normal), cd/dvd drive & File System. 'File System' appears to just be the 80GB drive. Right click - Properties on File System confirms it is just the 80GB, no sign of the 500GB.

betrunkenaffe, yes that'll be the one. The 500GB drive has Windows XP on it. I'll have a read through the details on the link and post back. Thanks :]

---

### Post by betrunkenaffe on 2010-07-12
Okay, based on your last reply, looks like it is in fact mounting properly. It's odd that it disappeared from the list however this might work to get it back in there.

Open nautilus /mnt as you did, while it's open, click on bookmarks->add bookmark.

Is it in there? If yes, reboot. Is it still in there?

---

### Post by 420 on 2010-07-12
I tried the bookmark thing after "**sudo mount /dev/sda1 /mnt**" - "**nautilus /mnt**" was suggested and the bookmark disappeared once I rebooted. No bookmark, no 500GB drive shown in Places. Had to go to work unfortunately so that's as far as I got this afternoon.

This evening though, I had a read through the link as suggested and I came across something that may be of importance. I'm not 100% on this (*still learning*) but have a look and check.

I done "**gksu gedit /etc/fstab**" and it returned this;
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=blahblahblah-numbers-and-letters none            swap    sw              0       0
```

[COLOR=Red][Edit] *Just a note: This was on a fresh boot. Nothing else entered into the Terminal*[/COLOR]

My only previous experience with operating systems is pretty much Windows based but going by the example in the link, isn't the 500GB drive supposed to be mentioned in there, *somewhere*? Or is that just what is mounted at that moment in time?

....Another thing I though may be worth a try for a quick fix is removing the drive, booting the system, shutting down, reinstalling the drive & booting again to see if Ubuntu picks it up by it's self. I'm more interested in going the long route right now though, I like the learning.

---

### Post by bcbc on 2010-07-13
> **420 said:**
> 
I done "**gksu gedit /etc/fstab**" and it returned this;
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=blahblahblah-numbers-and-letters none            swap    sw              0       0
```
OK that explains the prob. I thought about this, but normally the fstab identifies partitions via the UUID. Anyway... when you installed ubuntu with a single drive the drive was /dev/sda and the root / was mounted on /dev/sda1. But when you add the 500GB drive it became /dev/sda and the other /dev/sdb (probably drive type or bios determines this).

To fix it you could change fstab to mount root on /dev/sdb1, but this will only work until you remove the new drive, so instead run:
```
sudo blkid
```
Make a note of the UUID of your root partition and then change /dev/sda1  in /etc/fstab to be UUID=yyyyyy

---

### Post by 420 on 2010-07-13
> **bcbc said:**
> To fix it you could change fstab to mount root on /dev/sdb1

Job done. :)

Went into fstab, changed "/dev/sda1" to "/dev/sdb1", rebooted and it all looks good. 500GB Filesystem is back in the Places menu and everything appears to be working as normal.

Well done, thanks a lot bcbc & betrunkenaffe for the help. :D

---

