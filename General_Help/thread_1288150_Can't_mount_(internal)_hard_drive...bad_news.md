---
title: "Can't mount (internal) hard drive...bad news"
date: 2009-10-11
forum: General Help
---

### Post by zfh10 on 2009-10-11
I installed Ubuntu a few months ago, no complaints at all.  I did have an issue with a micro SD card, so I installed Gparted to try and figure out how to do a simple format.  Unfortunately I must have deleted something in the main partition....

...next time I booted I got GRUB error 22.  Uh oh.

I burned a Jaunty cd and fired it up.  I tried the fdisk -l command and it sees my (only) 80gb sata drive, but there is nothing mounted.  I've spent the past 4 hours trying to mount my hard drive, at least so I can get the files off.  

I've tried to repair the grub, using these steps:

> 
Restoration of Grub is very easy. All you need is the Ubuntu Live CD (you should already have it if you install Ubuntu).

Boot up your live CD
In the desktop, open terminal (Applications -> Accessories -> Terminal).

sudo grub

This will set it to grub mode

find /boot/grub/stage1

This will locate your boot partition. If you already know the location, you can ignore this step.

root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

setup (hd0)
quit

Reboot your system. You should be able to access the Grub bootloader now.It can't find Stage1, it says "Error 15: file not found".  I can't find what my hrd drive is called so I can mount it.

So frustrated by this.  To be honest my affection for Ubuntu has disappeared.  Please restore it!

What can I do?  Thanks

---

### Post by zfh10 on 2009-10-11
any ideas please?  sorry to bump this, but could a Linux guru please point me in the right direction...?  thanks

---

### Post by abhilashm86 on 2009-10-11
> **zfh10 said:**
> any ideas please?  sorry to bump this, but could a Linux guru please point me in the right direction...?  thanks

use this in terminal to know all drives in your computer,
```
 sudo blkid

```
post the output of this, 
also see this,
```
df -h
```to know where your drive is mounted.........
refer this tutorial to check [URL="http://ubuntuforums.org/showthread.php?t=217009"]your media device and mount it,
also you find how to permanently mount drives here[/URL]......

---

### Post by zfh10 on 2009-10-11
> **abhilashm86 said:**
> use this in terminal to know all drives in your computer,
```
 sudo blkid

```post the output of this, 
also see this,
```
df -h
```to know where your drive is mounted.........
refer this tutorial to check [URL="http://ubuntuforums.org/showthread.php?t=217009"]your media device and mount it,
also you find how to permanently mount drives here[/URL]......

thank you.


SUDO BLKID:

/dev/loop0: type="squashfs"

DF -H

Filesystem Size Used Avail Use% Mounted on
tmpfs 375m 2.4m 372m 1% /lib/modules/2.6.28-11-generic/volatile
tmpfs 375m 2.4m 372m 1% /lib/modules/2.6.28-11-generic/volatile
tmpfs 375m 0 375m 0% /lib/init/rw
varrun 375m 84k 375m 1% /var/run
varlock                                 /var/lock
udev                                    /dev
tmpfs                                   /dev/shm
rootfs                                  /
/dev/sr0                              /cdrom
/dev/loop0                           /rofs
tmpfs                                  /tmp

(didn't type out the numbers in between, can if needed)

Any clues?

---

### Post by Eric Christopherson on 2009-10-11
It's possible you destroyed the partition table on the hard drive and/or formatted it by mistake. But I hope not! What does fdisk -l {device name of SATA drive} output?

---

### Post by zfh10 on 2009-10-11
> **Eric Christopherson said:**
> It's possible you destroyed the partition table on the hard drive and/or formatted it by mistake. But I hope not! What does fdisk -l {device name of SATA drive} output?

I hope not too!  <places head in hands>

SUDO FDISK -L:
[I]
Disk /dev/sda: 80.0GB
255 heads, 63 sectors/track 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier : 0x63a8f70b
Device Boot Start End Blocks System ID[/I]

thanks...

---

### Post by zfh10 on 2009-10-11
any ideas?  :-)

---

### Post by arrange on 2009-10-11
Get hold of your backup files :sad:

You could also try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

---

### Post by Eric Christopherson on 2009-10-11
> **zfh10 said:**
> I hope not too!  <places head in hands>

SUDO FDISK -L:
[I]
Disk /dev/sda: 80.0GB
255 heads, 63 sectors/track 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier : 0x63a8f70b
Device Boot Start End Blocks System ID[/I]

thanks...

That's all it says? That doesn't look good -- it seems to have no partitions. I'm not sure, but I think that if you haven't formatted the disk or modified it in any other way, you should be able to recreate the partitions and save your data -- *if you know exactly what partitions you had, where they started, and how big they were.* Otherwise, maybe there is software that can detect them; the aforementioned testdisk looks promising (but I've never used it). I somewhat doubt the drive has actually been formatted, because it would need to have a partition for that (but you may have formatted it and *then* deleted the partitions).

---

### Post by zfh10 on 2009-10-11
is there any way of copying key files off my hard drive, even though I can't "see" it?  

It looks bad doesn't it :(

---

### Post by zfh10 on 2009-10-11
any takers for file salvage advice?  thanks

---

### Post by Eric Christopherson on 2009-10-12
No, sorry :( Maybe a professional data-recovery company.

---

### Post by renkinjutsu on 2009-10-12
have you tried: ```
sudo grub
find /boot/grub/stage1
```?

---

### Post by zfh10 on 2009-10-12
> **renkinjutsu said:**
> have you tried: ```
sudo grub
find /boot/grub/stage1
```?
yep, tried this in the original post.  This is my girlfriends laptop that has been borked, and she's also sick of not having a printer that works.  I spent 2 days on the printer operation  (I'm hardly an expert...lol...but I did follow all the steps precisely) and it still didn't recognise it.  I might go back to Windoze.

Hold me.  :(



(I will persevere with EEEbuntu on my laptop though!)

---

### Post by 440corbon on 2009-10-12
I used test disk and one of its utilities. To recover some photos once. I got all turned around doing it but got what I wanted back. If you download the latest knoppix live cd it should be on there. That is the best I can do for you.

---

### Post by osbornlei on 2009-10-12
Just a small reminder when you use Gparted last time did you use a option called "Delete Paratition table" ?

---

### Post by zfh10 on 2009-10-13
> **osbornlei said:**
> Just a small reminder when you use Gparted last time did you use a option called "Delete Paratition table" ?
yes, I couldn't see an obvious 'format' option, so I thought this was the equivalent command for what I thought was my SD card. I was wrong!

---

