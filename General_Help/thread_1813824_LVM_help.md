---
title: "LVM help"
date: 2011-07-28
forum: General Help
---

### Post by rkillcrazy on 2011-07-28
**First off, I apologize, in advance, for the long post.**

Okay, so, here's my scenario.  We had a VM guest, running Ubuntu Server 10.04.3, fill up an HDD.  A reboot fixed it so I guess it was full of temp files or other cached data.  Anyway, it was built with an LVM partitioned HDD which encompassed root (/) and everything else.  I figured it would be a good time to try to extend the LV.  Well, that didn't turn out to be as easy as I thought it would!

The easiest part was making the VHD bigger in VMware's vSphere!  Once I had that, all I thought I had to do was extend the LV into that unpartitioned space.

I did a lot of Googling!  I must've had two dozen tabs open in Chrome...  I found some stuff and began to piece things together.  I know I'm missing something...  Below is the process I took.

**Let's see what we have for HDDs:**
```

user@zenoss1:~$ sudo fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e891b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1045     8136705    5  Extended
/dev/sda5              32        1045     8136704   8e  Linux LVM

```

**Let's see what we have for LVGs:**
```

user@zenoss1:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               zenoss1
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               7.76 GiB
  PE Size               4.00 MiB
  Total PE              1986
  Alloc PE / Size       1986 / 7.76 GiB
  Free  PE / Size       0 / 0
  VG UUID               6d6Zae-m7A8-m0G6-2fTw-P0Zw-l53J-CV3Pxt

```

Okay, I don't see all that space that should be there.  I know I almost doubled the size of the VHD in vSphere.  Either I'm running the wrong commands or I'm not seeing what I *think* I should be seeing.

So, I ended up cheating.  I booted to a GParted CD and added another unformatted partition that way.  After that, I rebooted and checked things again.

```

user@zenoss1:~$ sudo fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e891b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1045     8136705    5  Extended
/dev/sda3            1045        2611    12583936   83  Linux
/dev/sda5              32        1045     8136704   8e  Linux LVM

```

OK, that looks better.  I see more space not in use.  After seeing that, I extended the LVG.  Still seems odd though...  Seems like I shouldn't have had to add a partition - especially by *cheating* with GParted.

**Let's extend the LVG and make it span over both partitions:**
```

user@zenoss1:~$ sudo vgextend zenoss1 /dev/sda3
  No physical volume label read from /dev/sda3
  Physical volume "/dev/sda3" successfully created
  Volume group "zenoss1" successfully extended

```

**Let's see what we have for an LVG now:**
```

user@zenoss1:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               zenoss1
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               19.76 GiB
  PE Size               4.00 MiB
  Total PE              5058
  Alloc PE / Size       1986 / 7.76 GiB
  Free  PE / Size       3072 / 12.00 GiB
  VG UUID               6d6Zae-m7A8-m0G6-2fTw-P0Zw-l53J-CV3Pxt

```

**Ok, I think I need to extend the LVG so it uses some more of the space:**
```

user@zenoss1:~$ sudo lvextend -L12G /dev/zenoss1/root
[sudo] password for user:
  Extending logical volume root to 12.00 GiB
  Logical volume root successfully resized

```

**Let's see if we're able to use it:**
```

user@zenoss1:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               zenoss1
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               19.76 GiB
  PE Size               4.00 MiB
  Total PE              5058
  [COLOR="Red"]Alloc PE / Size       3170 / 12.38 GiB
  Free  PE / Size       1888 / 7.38 GiB[/COLOR]
  VG UUID               6d6Zae-m7A8-m0G6-2fTw-P0Zw-l53J-CV3Pxt

```

OK, that looks fine (I guess), but I still can't use it.  

**Let's resize the file system:**
```

user@zenoss1:~$ sudo resize2fs /dev/zenoss1/root
resize2fs 1.41.11 (14-Mar-2010)
Filesystem at /dev/zenoss1/root is mounted on /; on-line resizing required
old desc_blocks = 1, new_desc_blocks = 1
Performing an on-line resize of /dev/zenoss1/root to 3145728 (4k) blocks.
The filesystem on /dev/zenoss1/root is now 3145728 blocks long.

```

So, again, sorry for the long post but I wanted you to see the workflow and see how I went through it all.  What did I miss?  Again, somehow, I think GParted wasn't needed.  I also feel as though I shouldn't have even needed that other partition.

---

### Post by galvatron408 on 2011-07-30
You're almost there!! You're soooo close!! ;)

So, what is 3170 + 1888? got my calculator and it says... 5058

so, now that we know how many Free Physical Extents we have (PE), all we have to do is tell lvextend to use it! haha

sudo lvextend -l 5058 /dev/name

(That's a lowercase L by the way)

 [COLOR=Red]Alloc PE / Size       3170 / 12.38 GiB   
Free  PE / Size       1888 / 7.38 GiB[/COLOR]

---

### Post by rkillcrazy on 2011-08-02
> **galvatron408 said:**
> You're almost there!! You're soooo close!! ;)

So, what is 3170 + 1888? got my calculator and it says... 5058

so, now that we know how many Free Physical Extents we have (PE), all we have to do is tell lvextend to use it! haha

sudo lvextend -l 5058 /dev/name

(That's a lowercase L by the way)

 [COLOR=Red]Alloc PE / Size       3170 / 12.38 GiB   
Free  PE / Size       1888 / 7.38 GiB[/COLOR]

OK, that make sense.  How about the bit about having to extend the partition with Gparted?  I mean...let's say it wasn't a VM.  Let's say it was a real HDD and, when I loaded it at first, I didn't use the whole drive.  Maybe I had 10-GB (unpartitioned) left.  How would I use it?  Or, do I still need to create another partitions - regardless?

---

