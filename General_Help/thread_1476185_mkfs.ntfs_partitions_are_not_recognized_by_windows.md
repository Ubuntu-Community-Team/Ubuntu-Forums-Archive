---
title: "mkfs.ntfs partitions are not recognized by windows 7"
date: 2010-05-07
forum: General Help
---

### Post by colossus73 on 2010-05-07
Hi guys,

I formatted with mkfs.nts a USB 500 GB external drive. Under Linux when I connect it to the USB port it's recognized and works. Under windowz 7 home is's seen in the device list but not in the computer window. I can't do anything with it apart eject it. This is what I get from fdisk:

sudo fdisk /dev/sdc

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):

and this from fdisk -ls /dev/sdc:

gt[~]$ sudo fdisk -ls /dev/sdc

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcecd3954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)
gt[~]$

Strangely the partition is reported as W95 FAT32 (LBA) instead of NTFS.

I can't reformat. What do you guy suggest?

Thanks,

---

### Post by nikhilbhardwaj on 2010-05-07
try formatting it as fat in linux
and then after connecting to windows format it to ntfs

---

### Post by The Cog on 2010-05-07
The type for ntfs should be 7, not c. You can change the type (id) without reformatting by using fdisk:
```
sudo fdisk /dev/sdc
t   [COLOR="RoyalBlue"]change type[/COLOR]
1   [COLOR="RoyalBlue"]partition 1[/COLOR]
7   [COLOR="RoyalBlue"]type 7[/COLOR]
w   [COLOR="RoyalBlue"]write to disk[/COLOR]
```
Don't use gparted because it will also reformat the partition as it changes the type.

The type you are editing here is the type indicator stored in the partition table that says what type of filesystem is actually in the partition. To properly change the partition type, you have to both use mkfs to change the partition contents and use fdisk to change the id reported in the partition table.

---

### Post by colossus73 on 2010-05-08
> **The Cog said:**
> The type for ntfs should be 7, not c. You can change the type (id) without reformatting by using fdisk:
```
sudo fdisk /dev/sdc
t   [COLOR="RoyalBlue"]change type[/COLOR]
1   [COLOR="RoyalBlue"]partition 1[/COLOR]
7   [COLOR="RoyalBlue"]type 7[/COLOR]
w   [COLOR="RoyalBlue"]write to disk[/COLOR]
```
Don't use gparted because it will also reformat the partition as it changes the type.

The type you are editing here is the type indicator stored in the partition table that says what type of filesystem is actually in the partition. To properly change the partition type, you have to both use mkfs to change the partition contents and use fdisk to change the id reported in the partition table.

Thank you so much for the reply. So I have to use mkfs first and then the above instructions with fdisk but what of mkfs? The partition was already formatted with mkfs.ntfs. Which command shall I issue with mkfs since I CAN'T format again?

Thank you,

---

### Post by The Cog on 2010-05-08
> **colossus73 said:**
> Thank you so much for the reply. So I have to use mkfs first and then the above instructions with fdisk but what of mkfs? The partition was already formatted with mkfs.ntfs. Which command shall I issue with mkfs since I CAN'T format again?,

Just use fdisk to change the partition table label. It looks to me as though you're changing a FAT partition to NTFS. You've already changed the contents of the partition with mkfs, (your post says) but you haven't yet changed the partition table label to match. The fdisk commands I posted will re-label the partition table so it says that partition contains an NTFS filesystem. That should remove the confusion from Windows.

<lecture>
It worries me that you say you CANNOT re-format. Don't you have a backup? You should always have a backup. I learned the hard way when a sudden hard disk failure lost lots of family photos. Just one day the computer BIOS said I had no hard disk when I turned it on. No warning signs earlier. Poof! Now (too late), I'm rather more careful about keeping backups.</lecture>

---

### Post by colossus73 on 2010-05-08
> **The Cog said:**
> 
<lecture>
It worries me that you say you CANNOT re-format. Don't you have a backup? You should always have a backup. I learned the hard way when a sudden hard disk failure lost lots of family photos. Just one day the computer BIOS said I had no hard disk when I turned it on. No warning signs earlier. Poof! Now (too late), I'm rather more careful about keeping backups.</lecture>

This USB disk IS the backup disk. Before it was FAT32 formatted but I went into trouble when copying files more than 4GB (the limit of FAT) so I copied the WHOLE USB disk into my hard disk and then reformatted to NTFS then recopied the content to it and then deleted the data in the hard disk. I would avoid to repeat the same operation once again but as you said data is too precious to be lost. I will recopy the data back to the hard disk and change the partition type as you described. I will let you know the outcome, thanks for helping.

EDIT: It perfectly worked! No data was lost and windowz 7 recognized the NTFS partition. Thank you so much. I'm really grateful to you for your kind help!

---

### Post by Literati on 2012-04-30
> **The Cog said:**
> The type for ntfs should be 7, not c. You can change the type (id) without reformatting by using fdisk:
```
sudo fdisk /dev/sdc
t   [COLOR="RoyalBlue"]change type[/COLOR]
1   [COLOR="RoyalBlue"]partition 1[/COLOR]
7   [COLOR="RoyalBlue"]type 7[/COLOR]
w   [COLOR="RoyalBlue"]write to disk[/COLOR]
```
Don't use gparted because it will also reformat the partition as it changes the type.

The type you are editing here is the type indicator stored in the partition table that says what type of filesystem is actually in the partition. To properly change the partition type, you have to both use mkfs to change the partition contents and use fdisk to change the id reported in the partition table.

I realize I'm bumping a dead thread, but I'd like to thank you for this post, as it really helped me after I had a momentary heart-attack. :P

Thank you!

---

