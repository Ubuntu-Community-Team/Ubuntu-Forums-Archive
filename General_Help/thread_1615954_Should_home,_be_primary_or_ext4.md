---
title: "Should /home, be primary or ext4?"
date: 2010-11-07
forum: General Help
---

### Post by germanix on 2010-11-07
I am somewhat confused and hope someone here will advise me on this issue. I am running linux as sole OS and my HDD is partitioned as follows:
/ = primary partition, 10 GB
/home = ext4 (the rest of the HDD)
Swap = 2 GB (I only have 1GB Ram)
I have seen suggested in the forums that one should format both / and /home as  "primary" partitions, and swap as either primary or ext4? 
This is news to me. I have always assumed that /home is ext3 or ext4.
Have I made a mistake formatting /home as ext4? Is it better to have it as a "primary" partition?
Could someone please clear this up? :confused:

---

### Post by CharlesA on 2010-11-07
It shouldn't matter.

---

### Post by Joeb454 on 2010-11-07
I thought the options were primary or logical partitions, and then you can choose what format to use after that (e.g. ext3 or ext4).

As CharlesA said though, it shouldn't matter which you choose for your /home partition.

---

### Post by Quackers on 2010-11-07
The default for modern Linux installations is ext4 for / and home partitions. Primary or logical partition type is irrelevant to Linux. 
The swap partition will be formatted as swap - not ext4

---

### Post by germanix on 2010-11-07
> **Quackers said:**
> The default for modern Linux installations is ext4 for / and home partitions. Primary or logical partition type is irrelevant to Linux. 
The swap partition will be formatted as swap - not ext4

Now I am even more confused!  If the default for / is ext4, did I now make a mistake by partitioning / as "primary". Should I rectify this? Or does it not really matter? Or in other words would it be more beneficial for me to have / as ext4 instead of "primary"?

---

### Post by Quackers on 2010-11-07
Primary is a partition type, not a file system type. Ext4 is a file system type, which is formatted to a partition of type primary or logical etc.

---

### Post by alphacrucis2 on 2010-11-07
> **Quackers said:**
> Primary is a partition type, not a file system type. Ext4 is a file system type, which is formatted to a partition of type primary or logical etc.


Yeah. The OP has confused two distinct things. Partition type, such as primary, extended, logical versus the file system type. / can be a primary partition but you still require a file system which could any of a number of FS's such as EXT3, XFS, EXT4, ReiserFS, BTRFS etc. Each partition requires a file system no matter what sort of partition it is. The exception is a partition used for swap.

---

### Post by germanix on 2010-11-07
> **Quackers said:**
> Primary is a partition type, not a file system type. Ext4 is a file system type, which is formatted to a partition of type primary or logical etc.

I thank you for this information. Just to make sure that I have understood you correctly, does this now mean that although I had partitioned / as a primary partition, linux /, /root, /boot, etc installed itself on this primary partition as an ext4 filing system? And I can leave it as it is, meaning I do not have to change anything?

---

### Post by SaintDanBert on 2010-11-07
First, you have the drive hardware. You must create a partition table on the drive.

See [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning) to learn about partitioning in general.

Once you have partitions, each partition needs a "file system."
[list]
[*]Diskettes, "geek sticks" (or thumb or key or flash) drives, media cards, and such typically use either "fat16" or "fat32".
[*]Windows(R) uses either "fat32" or "ntfs"
[*]linux uses any of a long list of file systems -- including those used by windows.
[/list]

See [http://en.wikipedia.org/wiki/File_system_comparison](http://en.wikipedia.org/wiki/File_system_comparison) to get started thinking about "file systems" in general.

Start with [http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2) to learn about the linux **ext2** file system. Follow the references on that page to read about **ext3** and other related file systems.

Ext3 and Ext4 add recovery journals to the features of Ext2. Ext4 is now the default for most linux distributions. All sorts of other file systems offer their own features and justifications. Your choice.

Linux can deliver read-write services for both ntfs and fat32 file systems used by windows. There are utilities that enable windows to deliver read-write services for Ext2. I don't know about the other linux file systems.

Bonne chance,
~~~ 0;-Dan

---

### Post by Quackers on 2010-11-07
> **germanix said:**
> I thank you for this information. Just to make sure that I have understood you correctly, does this now mean that although I had partitioned / as a primary partition, linux /, /root, /boot, etc installed itself on this primary partition as an ext4 filing system? And I can leave it as it is, meaning I do not have to change anything?

Yes, unless you told it to use a different file system :-)

SaintDanBert gives a fuller explanation above, with links.

---

### Post by The Cog on 2010-11-07
Partitions coome in 2 types: Primary or Logical.

Primary partitions are the original type of partition on the IBM PC, and there are 4 of them (though you don't have to use all 4). When people started wanting more than 4 partitions on a disk, they devised a scheme to sub-divide one of the 4 primary partitions into Logical partitions. The primary partition that contains all the logical partitions is called an Extended partition.

So: 
Primary - there are 4 of these, not always all used
Extended - one of the 4 primaries, designated to hold Logical partitions
Logical - perhaps one of many living inside the Extended partition.

Any partition, Primary or Logical can contain any filesystem, ext, linux-swap, FAT etc.  For some reason, Windows can only boot from a primary partition although D: can be on a logical partition. I think it's a limitation of the windows bootloader. Linux doesn't have that restriction.

ext4 is the default filesystem for Ubuntu these days (and swap is the format for the swap partition).

---

### Post by sidzen on 2010-11-07
NOTE:  ext2, ext3, ext4, reiserfs, reiser4, xps, ntfs(MS), etc are all File Systems, hence the "fs" in some names.

As far as partitioning goes, / should be a primary partition if the boot loader is to be installed on it (all install says is, e.g., is */dev/sda* for GRUB or LILO to be installed upon).  It (/) can exist in an extended partition if /boot is a small primary partition and _the boot loader resides there_.  It is further recommended that all **but** *swap* and */tmp* and, if present, */boot* be ext4 file system partitions.  

I do not use a /boot partition, but there exist distros that require one and for it to use the ext2 file system (e.g. KahelOS).  I like a separate */tmp* partition of 4.6GB and reiserfs because I burn DVDs on occassion -- my preference.  It does not matter if it is primary or extended.  Neither does it matter with */home*.

Some say this is not important, but some distros balk and will not install otherwise, so this is how I do it.

Hope it helps!

EDIT:  for your purposes, now, **extended** and **logical** are the same -- to avoid confusion till your knowledge base is expanded  --sidzen

---

### Post by germanix on 2010-11-07
I thank you all for your help and support. You guys are just awesome. I have been running linux since Ubuntu 8.04, always made a fresh install but never formatted. I always used the whole disk on install. To tell the truth I was to scared to try and format to have a separate /home partition. When Ubuntu 10.10 arrived I partitioned a separate /home for the first time using Gparted and was very happy with myself for having achieved that. Everything is working fine but I got worried and confused by some entries in the forum leading me to believe that I may have made a mistake. I am now glad this has been sorted out and will now sleep more relaxed.
Thank you once again and have a good day. :P

---

### Post by Quackers on 2010-11-07
Wilkommen! Guten abend und schlaffen sie gut! :-)

---

### Post by SaintDanBert on 2010-11-08
Just remember to keep known good copies of all of your files. "Known good" means that (1) the save completed, and (2) you tested that the contents are what you expect them to be. You can always re-install the distro and its updates, but those pix of family events and the manuscript of your dissertation might be tough to replace.

Bonne chance,
~~~ 0;-Dan

---

