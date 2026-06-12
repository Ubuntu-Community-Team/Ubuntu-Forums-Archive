---
title: "One or more of the mounts listed in /etc/fstab"
date: 2010-09-21
forum: General Help
---

### Post by pankajsisodiya on 2010-09-21
Hi,

I have UBUNTU 9.10 Karmic Koala over Thinkpad R-61i. Whenever i boot my system i have the following message waiting for me,

--------------------------------------------------------------------------------------------------

[I]One or more of the mounts listed in /etc/fstab cannot yet be mounted:  

swap: waiting for UUID=00e09251-80bb-43dd-8a11-61e975fa3e09

Press Esc to enter a recovery shell[/I]

---------------------------------------------------------------------------------------------------

And once i press esc, my UBUNTU loads properly.


The file /etc/fstab have following content

------------------------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=c0eaba67-44d5-4e68-bfe8-408437ce8c01 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=00e09251-80bb-43dd-8a11-61e975fa3e09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

-------------------------------------------------------------------------------------------------------


What i need to do repair this. And make my UBUNTU to perform a normal boot

---

### Post by fjsimpkins on 2010-09-21
look here [http://ubuntuforums.org/showthread.php?t=1301766](http://ubuntuforums.org/showthread.php?t=1301766)

---

### Post by coffeecat on 2010-09-21
A couple of questions:

Have you installed another Linux distro on another partition? Some distros have the annoying habit of reformatting (quite unnecessarily) the swap partition and thus changing the UUID.

I notice your Ubuntu 9.10 root partition is formatted ext2. Was there a reason for this choice? Ext2 was not the default for 9.10 and is less robust than ext3 because it is non-journalled.

Anyway, to your problem. Most likely, the UUID for your swap is no longer 00e09251-80bb-43dd-8a11-61e975fa3e09, or you no longer have a swap partition. Open a terminal and post the output of of these two comands:

```
sudo blkid
sudo fdisk -lu
```... and someone will help you edit /etc/fstab. I'll be logging off soon so I won't be able to check up on this thread untl tomorrow.

---

### Post by pankajsisodiya on 2010-09-22
Have you installed another Linux distro on another partition? Some  distros have the annoying habit of reformatting (quite unnecessarily)  the swap partition and thus changing the UUID
**>> I have UBUNTU - Jaunty before i upgraded it to UBUNTU Karmic **


I notice your Ubuntu 9.10 root partition is formatted ext2. Was there a  reason for this choice? Ext2 was not the default for 9.10 and is less  robust than ext3 because it is non-journalled.
**>> how can i change(upgrade) it from ext2 to ext3?**


Anyway, to your problem. Most likely, the UUID for your swap is no  longer 00e09251-80bb-43dd-8a11-61e975fa3e09, or you no longer have a  swap partition. Open a terminal and post the output of of these two  comands: sudo blkid & sudo fdisk -lu
[B]>>

------------------------------------------------------------------------------------------
livestrong@pritabose:~$ sudo blkid
[sudo] password for livestrong: 
/dev/sda1: TYPE="swap" 
/dev/sda3: UUID="c0eaba67-44d5-4e68-bfe8-408437ce8c01" TYPE="ext2" 
/dev/sda5: UUID="1200167700166251" TYPE="ntfs" 
/dev/sda6: UUID="EA60244760241CB7" TYPE="ntfs" 

-------------------------------------------------------------------------------------------
livestrong@pritabose:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa651a651

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     8819684     4409811   82  Linux swap / Solaris
/dev/sda2        78140160   234436544    78148192+   f  W95 Ext'd (LBA)
/dev/sda3         8819685    78140159    34660237+  83  Linux
/dev/sda5        78140223   143382959    32621368+   7  HPFS/NTFS
/dev/sda6       143383023   234435599    45526288+   7  HPFS/NTFS

Partition table entries are not in disk order
------------------------------------------------------------------------------------------[/B]

---

### Post by coffeecat on 2010-09-22
> **pankajsisodiya said:**
> [B]livestrong@pritabose:~$ sudo blkid
[sudo] password for livestrong: 
/dev/sda1: TYPE="swap" 
/dev/sda3: UUID="c0eaba67-44d5-4e68-bfe8-408437ce8c01" TYPE="ext2" 
/dev/sda5: UUID="1200167700166251" TYPE="ntfs" 
/dev/sda6: UUID="EA60244760241CB7" TYPE="ntfs" [/B]
There's something wrong with that /dev/sda1 line. I've never seen one without a UUID, which is the information we need. Are you sure you didn't leave anything out? Compare the swap line from blkid on my machine:

```
/dev/sda9: UUID="0434c8a6-b643-43f7-b167-f9b81faf7c5a" TYPE="swap" 
```By the way, please enclose terminal outputs in code tags the way I have rather than emboldening them. The code tags preserve formatting.

It's easy enough to convert ext2 to ext3, but you'd also need to edit fstab. Let's clarify the situation regarding your swap partition first.

---

### Post by andrewthomas on 2010-09-22
What is the output of 

```
cat /etc/blkid.tab
```

---

### Post by CharlesA on 2010-09-22
> **coffeecat said:**
> There's something wrong with that /dev/sda1 line. I've never seen one without a UUID, which is the information we need. Are you sure you didn't leave anything out? Compare the swap line from blkid on my machine:

```
/dev/sda9: UUID="0434c8a6-b643-43f7-b167-f9b81faf7c5a" TYPE="swap" 
```

I've not seen it without the UUID either.

Mine looks the same as yours.

---

### Post by pankajsisodiya on 2010-09-22
@coffeecat No i din't missed out any line or word

@andrewthomas & @coffeecat, please see the output, i generated again

```

livestrong@pritabose:~$ sudo blkid
[sudo] password for livestrong: 
/dev/sda1: TYPE="swap" 
/dev/sda3: UUID="c0eaba67-44d5-4e68-bfe8-408437ce8c01" TYPE="ext2" 
/dev/sda5: UUID="1200167700166251" TYPE="ntfs" 
/dev/sda6: UUID="EA60244760241CB7" TYPE="ntfs" 
livestrong@pritabose:~$ ^C
livestrong@pritabose:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa651a651

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     8819684     4409811   82  Linux swap / Solaris
/dev/sda2        78140160   234436544    78148192+   f  W95 Ext'd (LBA)
/dev/sda3         8819685    78140159    34660237+  83  Linux
/dev/sda5        78140223   143382959    32621368+   7  HPFS/NTFS
/dev/sda6       143383023   234435599    45526288+   7  HPFS/NTFS

Partition table entries are not in disk order
livestrong@pritabose:~$ cat /etc/blkid.tab
<device DEVNO="0x0801" TIME="1285185708" TYPE="swap">/dev/sda1</device>
<device DEVNO="0x0803" TIME="1285185708" UUID="c0eaba67-44d5-4e68-bfe8-408437ce8c01" TYPE="ext2">/dev/sda3</device>
<device DEVNO="0x0805" TIME="1285185708" UUID="1200167700166251" TYPE="ntfs">/dev/sda5</device>
<device DEVNO="0x0806" TIME="1285185708" UUID="EA60244760241CB7" TYPE="ntfs">/dev/sda6</device>
livestrong@pritabose:~$

```

---

### Post by 3Miro on 2010-09-22
This is odd indeed. You can try to install Gparted (which lets you edit partitions under Linux), then open the drive and reformat the swap partition. BE VERY CAREFUL WHAT YOU ARE FORMATTING, YOU CAN DESTROY IMPORTANT DATA IF YOU FORMAT THE WRONG PARTITION.

```
 blkid 
```
will tell you the UUID of the newly formatted swap so you can now edit fstab
```
 gksudo gedit /etc/fstab 
```
to match the UUID from the swap mount line.
```
 # swap was on /dev/sda1 during installation
UUID=(Put the new UUID here) none swap sw 0 0
```

As for going ext2 -> ext3, you will have to reformat the drive, which means reinstalling everything. I wouldn't bother, unless you feel like reinstalling, just for the fun of it.

As for going ext2 -> ext3, you will have to reformat the drive, which means reinstalling everything. I wouldn't bother, unless you feel like reinstalling, just for the fun of it.

---

### Post by Quackers on 2010-09-22
That looks to me like it's trying to boot from /dev/sda1 which is a swap partition.

---

### Post by sisco311 on 2010-09-22
Try to set the UUID of the swap partition:
```
sudo tune2fs -U 00e09251-80bb-43dd-8a11-61e975fa3e09 /dev/sda1
```
Then check if it worked:```
sudo blkid -c /dev/null
```

---

### Post by coffeecat on 2010-09-22
> **3Miro said:**
> This is odd indeed. You can try to install Gparted (which lets you edit partitions under Linux), then open the drive and reformat the swap partition. BE VERY CAREFUL WHAT YOU ARE FORMATTING, YOU CAN DESTROY IMPORTANT DATA IF YOU FORMAT THE WRONG PARTITION.

The OP could simply use the device descriptor '/dev/sda1' instead of a UUID in the first field of the swap line in /etc/fstab. But it's very odd that there is no UUID. I didn't think that was possible.

> **3Miro said:**
> As for going ext2 -> ext3, you will have to reformat the drive, which means reinstalling everything. I wouldn't bother, unless you feel like reinstalling, just for the fun of it.

No, there is a way without reformatting. It would have to be done from the live CD. The OP would have to edit fstab to change 'ext2' to 'ext3' in the root line, and then:

```
sudo tune2fs -j /dev/sda3
```... to add a journal, thus converting ext2 to ext3. Although they would have to be confident enough not to make a mistake, otherwise you'd be right. They would have to reinstall. :-s

---

### Post by 3Miro on 2010-09-22
> **coffeecat said:**
> The OP could simply use the device descriptor '/dev/sda1' instead of a UUID in the first field of the swap line in /etc/fstab. But it's very odd that there is no UUID. I didn't think that was possible.


If changing the fstab to
```
 # swap was on /dev/sda1 during installation
/dev/sda1 none swap sw 0 0 
```
works fine, then thats great. However, I thought that Ubuntu required UUID in the fstab.

> 

No, there is a way without reformatting. It would have to be done from the live CD. The OP would have to edit fstab to change 'ext2' to 'ext3' in the root line, and then:

```
sudo tune2fs -j /dev/sda3
```... to add a journal, thus converting ext2 to ext3. Although they would have to be confident enough not to make a mistake, otherwise you'd be right. They would have to reinstall. :-s

I didn't know that. At any rate, BACKUP EVERYTHING IMPORTANT just in case something goes wrong.

---

### Post by coffeecat on 2010-09-22
> **3Miro said:**
> However, I thought that Ubuntu required UUID in the fstab.

You can use UUID, device descriptor or partition label in the first field. I think the Ubuntu tradition of using UUIDs (which only started around Dapper or Edgy iirc) is to give you flexibilty if you want to swap your physical drives around without editing fstab. The Dapper/Edgy time more-or-less coincides with when SATA drives were becoming common, so I suppose it was a response to that. You're more likely to move SATA drives around than the older PATA. I remember that when UUIDs came into Ubuntu fstab's they caused as much adverse comment on this forum as did window buttons on the left more recently. :)

It's interesting that other distros seem to have followed suit with this UUID business. Fedora used to rely on partition labels. I'm fairly sure I saw the odd UUID in fstab when I last installed it.

> **3Miro said:**
> I didn't know that. At any rate, BACKUP EVERYTHING IMPORTANT just in case something goes wrong.

+1001!

---

