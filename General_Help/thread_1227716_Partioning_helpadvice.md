---
title: "Partioning help/advice"
date: 2009-07-31
forum: General Help
---

### Post by adempewolff on 2009-07-31
I just got a new 250GB hard drive for my laptop.  I had planned to partition it as follows:

Primary Partition 1: (~60MB) Dell Utility Partition (FAT32)
Primary Partition 2: 40GB Windows XP (NTFS)
Primary Partition 3: 20GB MS OS testing area--Windows 7, Vista 64 (NTFS)
Primary Partition 4: Extended Partition
Logical Partition 1: 20GB Linux OS testing--Karmic (ext4)
Logical Partition 2: 4GB Shared swap (Linux Swap)
Logical Partition 3: 20GB Main OS--Ubuntu 9.04 (ext4)
Logical Partition 4: ~145GB /home (NTFS--so windows can access)

First does anything in that plan seem unusual?  Second I am having some trouble deciding how to go forward.

Gparted is not noticing the unformated drive in an external usb enclosure.  So I decided to go the way I had thought was best anyway:

1. Install Dell Utility Partition--erases all existing partitions if any, I could clone the old one though([http://www.goodells.net/dellutility/recreate.htm](http://www.goodells.net/dellutility/recreate.htm))
2. Install XP
3. Use GParted to resize NTFS and set up partition tables as I want.
4. Install Ubuntu
5. Install other OSes later

I had a problem slipstreaming AHCI drivers into my xp install so I decided to skip step two and install XP later.

However when I opened gparted (I put my old hdd back in the laptop and am accessing the new one via usb) it just sees  232.88GiB of unformatted drive.  This is weired because 1. the dell utilities should not use more than 100MB (although since gparted couldn't access the hdd before I don't know what the original size was) and 2. gparted on my old hdd recognizes the Dell utility partition as FAT 32 and 62.72MiB.

Part of the problem could be that the utility partition is "sealed". "In its sealed state, the DE partition is marked as the 'active' partition in the partition table. Thus, the first time the computer boots from the hard disk it will boot the DE partition, not the Windows partition. This section describes this one-time-only scenario." ([http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm)).  However I think it is waiting for a Windows XP OS to be installed before allowing itself to unseal.  The partition also edits its type in the partition table from 06h to DEh (hex) so the partition is hidden from Windows despite being FAT32. ([http://www.goodells.net/dellutility/partparm.htm](http://www.goodells.net/dellutility/partparm.htm)).  I could see this confusing gparted but it instantly recognize the Dell utility partition on my old hdd...

I'm sure I could talk with Dell about this but I would think I would rather proceed just starting out with the partitions I want and using another way to install the utility partition.

Does anyone have suggestions on how I can get some linux-based partition editor to recognize the whole 250GB so I can partition it as I desire?

This is all a lot to read so anyone who does so and can give me some advice I really, really, appreciate it!

Thanks!

---

### Post by adempewolff on 2009-07-31
So I tried using a gparted livecd and the Debian Kernel failed to load... So then I used a Ubuntu 9.04 amd64 livecd whiched loaded correctly and I was able to use gparted.

Still only ~230Gib and no sign of the utility partition!  Gah!  Where is that extra space going and where the hell is the utility partition?  I guess I'll send Dell an email.  Maybe this post should be moved to the Dell subforum...

---

### Post by SlugSlug on 2009-07-31
I woulnd not use ntfs for /home - winodws can see ext3  with a little help from a prg called somthing like ext2fs

---

### Post by bodhi.zazen on 2009-07-31
> **adempewolff said:**
> I just got a new 250GB hard drive for my laptop.  I had planned to partition it as follows:

Primary Partition 1: (~60MB) Dell Utility Partition (FAT32)
Primary Partition 2: 40GB Windows XP (NTFS)
Primary Partition 3: 20GB MS OS testing area--Windows 7, Vista 64 (NTFS)
Primary Partition 4: Extended Partition
Logical Partition 1: 20GB Linux OS testing--Karmic (ext4)
Logical Partition 2: 4GB Shared swap (Linux Swap)
Logical Partition 3: 20GB Main OS--Ubuntu 9.04 (ext4)
Logical Partition 4: ~145GB /home (NTFS--so windows can access)

First does anything in that plan seem unusual?  Second I am having some trouble deciding how to go forward.

You should set up a ntfs data partition and not a shared home (IMO). You can not user either FAT or NTFS as /home . So give each distro it's own home and mount the shared data drive in say /media/data and use links

ln -s /media/data/music /home/user/music

I give my Linux installs 10 Gb with a larger data partition.

> Gparted is not noticing the unformated drive in an external usb enclosure.  So I decided to go the way I had thought was best anyway:

1. Install Dell Utility Partition--erases all existing partitions if any, I could clone the old one though([http://www.goodells.net/dellutility/recreate.htm](http://www.goodells.net/dellutility/recreate.htm))
2. Install XP
3. Use GParted to resize NTFS and set up partition tables as I want.
4. Install Ubuntu
5. Install other OSes later

Just take care not to destroy your recovery partition.

> I had a problem slipstreaming AHCI drivers into my xp install so I decided to skip step two and install XP later.

However when I opened gparted (I put my old hdd back in the laptop and am accessing the new one via usb) it just sees  232.88GiB of unformatted drive.  This is weired because 1. the dell utilities should not use more than 100MB (although since gparted couldn't access the hdd before I don't know what the original size was) and 2. gparted on my old hdd recognizes the Dell utility partition as FAT 32 and 62.72MiB.

Part of the problem could be that the utility partition is "sealed". "In its sealed state, the DE partition is marked as the 'active' partition in the partition table. Thus, the first time the computer boots from the hard disk it will boot the DE partition, not the Windows partition. This section describes this one-time-only scenario." ([http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm)).  However I think it is waiting for a Windows XP OS to be installed before allowing itself to unseal.  The partition also edits its type in the partition table from 06h to DEh (hex) so the partition is hidden from Windows despite being FAT32. ([http://www.goodells.net/dellutility/partparm.htm](http://www.goodells.net/dellutility/partparm.htm)).  I could see this confusing gparted but it instantly recognize the Dell utility partition on my old hdd...

I'm sure I could talk with Dell about this but I would think I would rather proceed just starting out with the partitions I want and using another way to install the utility partition.

Does anyone have suggestions on how I can get some linux-based partition editor to recognize the whole 250GB so I can partition it as I desire?

This is all a lot to read so anyone who does so and can give me some advice I really, really, appreciate it!

Thanks!Not sure .

---

### Post by egalvan on 2009-07-31
One reason for the difference in sizes is in HOW the different utilities 'report' capacity...

250GB is a decimal base... much beloved of marketing and MS types,
because it allows the size to be 'bigger'.
Which is why it's put on the label.
One KiloByte only needs 1000 bytes.


232GB is a binary base... much beloved of computer programers and such,
because it uses the same numbering system as computers...
One KiloByte needs 1024 bytes

Put another way, one reports 1000 bytes (decimal)
the other reports 976 bytes (binary)

And the capacity of hard drives is also reduced by the drive's need
for sectoring information, and spare sectors.

It's all a numbers game...
man's constant need to be "bigger" than his competitor.

---

### Post by adempewolff on 2009-07-31
thanks for all the replies, through some research I quickly discovered that advertised and usuabled space weren't the same...  I had always known this but the difference between 250GB and 230GB seems a lot bigger than 74GB and 80GB... sigh...

So now my only problem is why gparted isn't seeing the Dell Utility Partition and why there isn't a partition table despite the Dell partition functioning...

Maybe a moderator could move this post to the Dell subforum? (if I am able to do this myself I cannot seem to find this link)

---

