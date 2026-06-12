---
title: "How can i find which partitions are &quot;primary&quot;?"
date: 2012-01-05
forum: General Help
---

### Post by SidebySide on 2012-01-05
possibility: System allows making:
1. Four primary partitions or
2. Three Primaries and an extended partition

So, Now,
1. How can I recognize which one of my all partitions (ntfs, ext, ...) are primary and which ones are logical?
2. Which one of primary partitions is "active primary"?

---

### Post by pretty_whistle on 2012-01-05
Disk Utility will show you.

---

### Post by neu5eeCh on 2012-01-05
type: 

> 
sudo parted -l 

in terminal. This will tell you which are primary.

---

### Post by imachavel on 2012-01-05
mine look like this:

sudo parted -l
[sudo] password for danel: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      48.8GB  337GB  288GB   primary   ext3            boot
 2      337GB   500GB  163GB   extended
 6      337GB   397GB  60.2GB  logical   ext4
 7      397GB   400GB  2675MB  logical   linux-swap(v1)
 5      437GB   474GB  36.7GB  logical   linux-swap(v1)

---

### Post by coffeecat on 2012-01-05
> **SidebySide said:**
> 1. How can I recognize which one of my all partitions (ntfs, ext, ...) are primary and which ones are logical?

If you run "sudo parted -l" or "sudo fdisk -lu", the partitions numbered 1 to 4 are primary or extended. An extended is simply a special type of primary whose only purpose is to act as a container for logicals. Parted or fdisk will tell you which, if any, is an extended partition. All logical partitions are numbered 5 and upwards. And, as VTPoet said, parted will tell you which are primary, extended or logical, but it's useful to know the numbering rule.

> **SidebySide said:**
> 2. Which one of primary partitions is "active primary"?

The one with the boot flag set. Both parted and fdisk will tell you which has the boot flag.

---

### Post by SidebySide on 2012-01-05
kind regards!
***********

Now; I've a big problem! Where is unallocated partition?
I deleted a drive in windows(D:/ => 97 GB) to install backtrack on it, but, when I boot backtrack, I can't find the free space in the list(see the latest picture)?!!

I found below script so useful!
[http://sourceforge.net/projects/bootinfoscript](http://sourceforge.net/projects/bootinfoscript)
***********************
This is my output of executing that script on my system in backtrack live mode: [http://www.pastie.org/pastes/3132205/text](http://www.pastie.org/pastes/3132205/text)

I'm going to Install Back-Tracke(based on Ubuntu) but I couldn't find mine unparted space when I try to install it manually:

[http://uploadkon.ir/uploads/d41306f166410cb6eef1e301e516777f.jpg](http://uploadkon.ir/uploads/d41306f166410cb6eef1e301e516777f.jpg)

[http://uploadkon.ir/uploads/a3716732ce4affbb824eb5a964e0af9d.jpg](http://uploadkon.ir/uploads/a3716732ce4affbb824eb5a964e0af9d.jpg)

[http://uploadkon.ir/uploads/7105cf02946607e58f889b1c114e4a59.jpg](http://uploadkon.ir/uploads/7105cf02946607e58f889b1c114e4a59.jpg)

---

### Post by coffeecat on 2012-01-05
@SidebySide, you cannot install Linux to that hard drive with the partitions you have. You have managed to convert them to Windows dynamic partitions. They need converting back to basic partitions, or you need to completely wipe the drive and start again.

I'll see if I can find you a link.

---

### Post by coffeecat on 2012-01-05
Here's a post with some explanation and links about dynamic partitions:

[http://ubuntuforums.org/showpost.php?p=11509467&postcount=11](http://ubuntuforums.org/showpost.php?p=11509467&postcount=11)

You have five dynamic partitions. Whether you can convert that back to a basic disk, I don't know, because 5 is one more that the maximum allowed 4 primary partitions.

---

