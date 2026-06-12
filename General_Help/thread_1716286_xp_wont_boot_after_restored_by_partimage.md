---
title: "xp wont boot after restored by partimage"
date: 2011-03-28
forum: General Help
---

### Post by ManishSR on 2011-03-28
i have two hardisks sda (contains orginal bootable xp) and sdb (contains restored xp that does not boot)

```
fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x007f007f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8387    67368546    7  HPFS/NTFS
/dev/sda2            8387        9729    10781281+   5  Extended
/dev/sda5            8387        9426     8341504   83  Linux
/dev/sda6            9426        9730     2440192   82  Linux swap / Solaris


fdisk  -l /dev/sdb

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9425    75701248    7  HPFS/NTFS
/dev/sdb2            9425       30402   168496128    5  Extended
/dev/sdb5            9425       30402   168495104    7  HPFS/NTFS
```

i used partimage to do backup and restore my old xp partition sda1 to sdb1 .

now cant boot my new xp. there is just white underscore blinking (at least for 15 min).

how can i boot xp !!!

---

### Post by coffeecat on 2011-03-28
Post the output of:

```
sudo fdisk -lu
```... not "fdisk -l". This will give us the starts and ends in sectors rather than cylinders. It's possible your start sector in sdb is different from sda. This is one reason for an unbootable cloned Windows.

Also, you can leave out the /dev/sda and /dev/sdb options when running fdisk. Run the command above and it will give you output for all detectable disks.

Why are you wanting to clone your Windows from one disc to another? Was it your intention to make the sdb drive your main drive? If so, have a look at Macrium Reflect Free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

When you make a Windows C: image with Macrium it takes a note of the start sector and ensures that the partition you restore to has the start sector in the right place.

---

### Post by ManishSR on 2011-03-28
```

sudo fdisk -lu

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   151404543    75701248    7  HPFS/NTFS
/dev/sdb2       151404544   488396799   168496128    5  Extended
/dev/sdb5       151406592   488396799   168495104    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x007f007f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   134737154    67368546    7  HPFS/NTFS
/dev/sda2       134733822   156296384    10781281+   5  Extended
/dev/sda5       134733824   151416831     8341504   83  Linux
/dev/sda6       151418880   156299263     2440192   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03c92cce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953536129   976767041    7  HPFS/NTFS

Disk /dev/sdd: 1004 MB, 1004387840 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1961695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2169

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     1961694      980816    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 28, 1)

```

sdc and sdd are external harddisk and pendrive

---

### Post by ManishSR on 2011-03-28
> **coffeecat said:**
> Post the output of:

```
sudo fdisk -lu
```... not "fdisk -l". This will give us the starts and ends in sectors rather than cylinders. It's possible your start sector in sdb is different from sda. This is one reason for an unbootable cloned Windows.

Also, you can leave out the /dev/sda and /dev/sdb options when running fdisk. Run the command above and it will give you output for all detectable disks.

Why are you wanting to clone your Windows from one disc to another? Was it your intention to make the sdb drive your main drive? If so, have a look at Macrium Reflect Free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

When you make a Windows C: image with Macrium it takes a note of the start sector and ensures that the partition you restore to has the start sector in the right place.

yes my sda hard disk is corrupted (i guess) thats why i am doing all of this

---

### Post by coffeecat on 2011-03-28
This is what I was suspecting:

> **ManishSR said:**
> ```

sudo fdisk -lu

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        [COLOR=Red]2048 [/COLOR]  151404543    75701248    7  HPFS/NTFS
/dev/sdb2       151404544   488396799   168496128    5  Extended
/dev/sdb5       151406592   488396799   168495104    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x007f007f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          [COLOR=Red]63[/COLOR]   134737154    67368546    7  HPFS/NTFS
/dev/sda2       134733822   156296384    10781281+   5  Extended
/dev/sda5       134733824   151416831     8341504   83  Linux
/dev/sda6       151418880   156299263     2440192   82  Linux swap / Solaris
```

I'm a bit vague as to the details, but I believe the Windows boot files reference the absolute location of the boot sector rather than the relative location. So that if the start sector is moved, Windows booting fails. 

If you have a Microsoft XP install disc (rather than an OEM manufacturer's restore disc) you could try running fixboot from the recovery console of the CD. That might work. Apart from that I can only suggest starting over with Macrium which you run from inside Windows itself.

---

### Post by ManishSR on 2011-03-28
> **coffeecat said:**
> This is what I was suspecting:



I'm a bit vague as to the details, but I believe the Windows boot files reference the absolute location of the boot sector rather than the relative location. So that if the start sector is moved, Windows booting fails. 

If you have a Microsoft XP install disc (rather than an OEM manufacturer's restore disc) you could try running fixboot from the recovery console of the CD. That might work. Apart from that I can only suggest starting over with Macrium which you run from inside Windows itself.

i dont have xp cd and also my original bootable xp is extremely slow (that because of hard disk) and macrium does not work in ubutnu so i cant use macrium either.

is there any other option. cant this problem be fixed from ubuntu ?

---

### Post by coffeecat on 2011-03-28
> **ManishSR said:**
> i dont have xp cd and also my original bootable xp is extremely slow (that because of hard disk) and macrium does not work in ubutnu so i cant use macrium either.

is there any other option. cant this problem be fixed from ubuntu ?

I very much doubt it. In theory you could move the start sector with a partitioning tool but that might cause more problems than it solves. And besides, I'm sure the start sector issue is the problem, but not 100% sure, tbh.

Apologies for missing that you believe the sda disc is corrupted. If you mean that the disc is failing then I can see why Macrium may not be an option for you. But if you believe the XP partition filesystem is corrupted then there's no point in cloning it. You'll just end up with a faulty clone.

Can you boot Windows from sda at all, even if slowly? If you can it might be worth trying out Macrium. Or what is the problem? If it just a corrupted filesystem you might be able to repair it with chkdsk from one of a number of available bootable CDs.

I'll pm a couple of others to have a look at this thread. They may have some other ideas.

---

### Post by ManishSR on 2011-03-28
> **coffeecat said:**
> I very much doubt it. In theory you could move the start sector with a partitioning tool but that might cause more problems than it solves. And besides, I'm sure the start sector issue is the problem, but not 100% sure, tbh.

Apologies for missing that you believe the sda disc is corrupted. If you mean that the disc is failing then I can see why Macrium may not be an option for you. But if you believe the XP partition filesystem is corrupted then there's no point in cloning it. You'll just end up with a faulty clone.

Can you boot Windows from sda at all, even if slowly? If you can it might be worth trying out Macrium. Or what is the problem? If it just a corrupted filesystem you might be able to repair it with chkdsk from one of a number of available bootable CDs.

my sda is starting slow down, now matter how many time i reinstall xp , it stutter. so annoying it is, i am facing this problem for three month now. and there is also high pitch sound coming out of my cpu. i first doubted motherboard and ram (and also i was quite sure so i replaced them) but now i doubt sda hard disk (my 80 gb, older hard disk) so to confirm i removing sda for a while and thats why i am cloning xp.

original xp ( of sda) is very very slow and worst of all it stutter. so even moving pointer take ages. so doing something macrium is completely out of question.

however ubuntu seem to work fine (while residing in sda). what i can do, can do only from ubuntu. thats why i used partimage.

as u saying it might creates problems rather then solving any. then only thing that i can do is start over. so what backup tools should i use now to clone xp from sda1 to sdb1.

> **coffeecat said:**
> 
I'll pm a couple of others to have a look at this thread. They may have some other ideas.
thanks a lot

---

### Post by Quackers on 2011-03-28
I use clonezilla. The full disk image can then be restored to the second hard drive (if they are the same size, or sdb is bigger than sda).
[http://clonezilla.org/](http://clonezilla.org/)

It may work for your circumstances.

---

### Post by Rubi1200 on 2011-03-28
As Quackers suggested, make a backup using Clonezilla.

Then, you must try and run chkdsk to see if there are errors. If yes, keep running it until there are no more.

You also want to use the Disk Utility from an Ubuntu LiveCD to check the health of the hard-drive.

Oh, and if there are funny noises you should definitely either open up and check and clean or take the computer to a technician who can do it.

Then, and only then, if you are sure things are in order should you attempt to restore the backup.

That's my opinion at least.

---

### Post by oldfred on 2011-03-28
How full is your NTFS partition? Windows NTFS partitions like to have lots of room, like 30% free. At 20% free it starts to slow down and at 10% free will run really slow if at all.

Testdisk also has a rebuild boot sector function that should work with XP,

Rebuilding An NTFS Boot Sector On An NTFS Partition
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by LostFarmer on 2011-03-28
Posted by "[coffeecat]("http://ubuntuforums.org/member.php?u=129087")" post #5
> but I believe the Windows boot files reference the absolute location of  the boot sector rather than the relative location. So that if the start  sector is moved, Windows booting fails. 
  That is correct the XP registry stores the HDD ID and the absolute volume boot sector for the system disk.  XP will correct that data IF there are no other FAT32/NTFS that it can see on first boot.  Some times only removing the cloned from hdd will work. Some cloning programs will also fix the registry.  With care one can edit the registry from a different booted XP.

---

### Post by srs5694 on 2011-03-28
I have two suggestions that I haven't noticed thus far in this thread:


[list]
[*]You can delete your current /dev/sdb1, create a new /dev/sdb1 that begins on sector 63, and copy /dev/sda1 to /dev/sdb1 again. In theory, this new copy should be bootable, although you might need to swap the hard disks or use GRUB options to make Windows think it's booting from the first physical disk. Also, if /dev/sdb is an Advanced Format drive, this option is inadvisable, since performance will suffer. You can create a partition that's aligned in this way by setting alignment to cylinder mode in GParted or by enabling "DOS compatibility" mode in fdisk. There have been changes in alignment policies in recent months with both tools, so you may need to experiment to find the right settings for whatever versions you're using.
[*]I once ran across instructions on how to modify the boot sector of an NTFS partition to fix the bootability issue that occurs when you move the partition. Unfortunately, I can't seem to find those instructions (I thought I'd saved them to my own hard disk, but if so I'm not sure where they are now....). You could try a Web search to find those instructions yourself.
[/list]


Beyond these options, Windows-native backup/restore utilities generally do a better job with this issue than do Linux tools. Thus, you could use a Windows backup/restore utility, as other have already suggested, to do the job.

---

