---
title: "unusual disk partition"
date: 2011-11-05
forum: General Help
---

### Post by watgrad on 2011-11-05
Hi -

After attempting to upgrade ubuntu 11.04 to 11.10 I had to do a fresh install. Now when I look at my disk partition, I see several 'swap' partitions for ubuntu.  It should only need one, I think.  How do I tell which swap partition is the one ubuntu is using?  Can I force it to use the last partition and reclaim the 6 GB of wasted space in the partitions next to my ubuntu install?
If things are working now - should I even bother trying to recover the wasted disk space?
What I want:
10GB ntfs shared space for swapping files between windows and ubuntu.
155 gb windows 7 partition
150 gb ubuntu partition
4 gb swap space...

thanks for any suggestions...

edit - attached screen capture of current disk partitions

---

### Post by 23dornot23d on 2011-11-05
You only need 1 swap space .... can you do a similar shot of the disk layout using gparted though
as the view you show of the disk is not one I have seen before ......

or run the boot info script ...... instructions are here ..... 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Will give people more to work with ..... and is easy to read if you want to check it out yourself ......

Its easy using gparted to remove the non used swap space and resize the Linux partition to use the gained space. .....

But as with any disk operations backup your data first .....

---

### Post by garyed on 2011-11-05
You can check your fstab file to see the uuid of the swap file you're using.
You can change fstab to use the last partition for swap file if needed.
To view fstab:
```
cat /etc/fstab
```

To view uuid's:
```
sudo blkid

```

---

### Post by watgrad on 2011-11-05
Thanks for helping:

OK... 

cat /etc/fstab gives:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e292558c-3ff2-47d1-a54d-faa8a10fe959 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6ad4e7a5-3cab-4489-863b-5b50c8f662f8 none            swap    sw              0       0

and sudo blkid gave:
/dev/sda1: LABEL="Shared" UUID="CE149FEC149FD635" TYPE="ntfs" 
/dev/sda2: UUID="FCFCA63CFCA5F156" TYPE="ntfs" 
/dev/sda5: UUID="75edae63-3917-4e11-a1c6-2ecab8c09a4d" TYPE="swap" 
/dev/sda6: UUID="a3d4afdc-f151-44ba-b0ab-685ff63a5ab4" TYPE="swap" 
/dev/sda7: UUID="e292558c-3ff2-47d1-a54d-faa8a10fe959" TYPE="ext4" 
/dev/sda8: UUID="6ad4e7a5-3cab-4489-863b-5b50c8f662f8" TYPE="swap" 

A bit confusing for me.
does the numeral appended to the 'sda' prefix indicate the order of the partitions on the disk or the order they were created?  
The disk utility program generated the image I attached in the original posting.  This output seems to show that the 2 extra swap files are before the ubuntu partition...any ideas?

Edit - attached is how gparted see the drive...

---

### Post by garyed on 2011-11-05
So it looks like /dev/sda8 is the partition you're using for swap. Unless you have another OS that could be using one of the other swap partitions you could delete them. Even if you were using another one of the swap partitions for another OS version you could easily change fstab so they all use the same swap partition so there's still no need for more than one swap part.

---

### Post by killermist on 2011-11-05
> **watgrad said:**
> and sudo blkid gave:
/dev/sda1: LABEL="Shared" UUID="CE149FEC149FD635" TYPE="ntfs" 
/dev/sda2: UUID="FCFCA63CFCA5F156" TYPE="ntfs" 
/dev/sda5: UUID="75edae63-3917-4e11-a1c6-2ecab8c09a4d" TYPE="swap" 
/dev/sda6: UUID="a3d4afdc-f151-44ba-b0ab-685ff63a5ab4" TYPE="swap" 
/dev/sda7: UUID="e292558c-3ff2-47d1-a54d-faa8a10fe959" TYPE="ext4" 
/dev/sda8: UUID="6ad4e7a5-3cab-4489-863b-5b50c8f662f8" TYPE="swap" 

A bit confusing for me.
does the numeral appended to the 'sda' prefix indicate the order of the partitions on the disk or the order they were created?  
The disk utility program generated the image I attached in the original posting.  This output seems to show that the 2 extra swap files are before the ubuntu partition...any ideas?
There is a possibility that /dev/sda4 is the (hidden) "extended" partition that contains the logical partitions /dev/sda5-8.

As to partition numbering, when all created at once from a clean drive, they should be in an ascending order from drive begin to drive end.  When an already existing partition structure exists, and is then modified, sometimes partition numbers end up out of order or changed because of partitions that cease to be.
This is one reason that a lot of recommendation is made to use UUID in fstab entries instead of by device name, because even if partition structure changes, and device names change, the correct partitions will be mounted correctly.

All that said, 
```

/dev/sda5: UUID="75edae63-3917-4e11-a1c6-2ecab8c09a4d" TYPE="swap" 
/dev/sda6: UUID="a3d4afdc-f151-44ba-b0ab-685ff63a5ab4" TYPE="swap"

```
these swap partitions appear to be unused and so could be deleted and possibly sda7 expanded to consume the no-longer-occupied space.

As always, it is a good idea to have a backup of your data before shrinking or expanding a partition.  It being a root partition for the system, you may not be able to expand the partition from the running system and may have to use a livecd/usb to expand the partition.

---

