---
title: "Use deja dup to backup entire drive"
date: 2011-12-13
forum: General Help
---

### Post by GisliKarl on 2011-12-13
*Is it possible to use Deja Dup to backup the entire root partition /: and restore later if something happen by first reinstalling Ubuntu and then choose restore from Deja Dup?*
> 
UPDATE: After reinstalling my whole computer I tried restoring my entire root partition with Deja Dup. It fails with a kernel panic and an unbootable system. DO NOT TRY THIS.

---

### Post by collisionystm on 2011-12-13
> **GisliKarl said:**
> Is it possible to use Deja Dup to backup the entire root partition /: and restore later if something happen by first reinstalling Ubuntu and then choose restore from Deja Dup?

yes....

---

### Post by seawolf167 on 2011-12-14
There are [a lot of backup methods]("https://help.ubuntu.com/community/BackupYourSystem") you can choose from. I personally like [Clonezilla]("http://www.clonezilla.org") as it creates an image of the entire drive or partition and can be used to restore everything (including the bootloader/MBR) so no re-installation is necessary.

---

### Post by x C0MMAND0 x on 2011-12-14
Does CloneZilla have to run as a live CD or can you install it on your system and run it while being in your standard booted desktop environment?

---

### Post by x C0MMAND0 x on 2011-12-14
Edit - wrong thread

---

### Post by collisionystm on 2011-12-14
> **x C0MMAND0 x said:**
> Does CloneZilla have to run as a live CD or can you install it on your system and run it while being in your standard booted desktop environment?

Clonezilla is something that is ran one time. Its just like Norton Ghost. You run it, make an image and done. There is no live backup system associated with clonezilla ( that I am aware of )

If you want to go that route, make a clonezilla imeage of your system and then just rsync your /home directory to a drive nightly.

If the system fails, restore the clonezilla image and then your /home directory afterwards.

---

### Post by seawolf167 on 2011-12-14
> **x C0MMAND0 x said:**
> Does CloneZilla have to run as a live CD or can you install it on your system and run it while being in your standard booted desktop environment?

The partition being imaged has to be unmounted - so you'll have to run it through a Live environment.

---

### Post by x C0MMAND0 x on 2011-12-14
> **collisionystm said:**
> Clonezilla is something that is ran one time. Its just like Norton Ghost. You run it, make an image and done. There is no live backup system associated with clonezilla ( that I am aware of )

If you want to go that route, make a clonezilla imeage of your system and then just rsync your /home directory to a drive nightly.

If the system fails, restore the clonezilla image and then your /home directory afterwards.

Can you install clonezilla on a separate partion like, /sda7 for example, and then boot to it?  That would have all other partitions that need to be imaged unmounted, and would save the trouble of having to put in a CD every night/week/whatever, because I already have a manual file backup via rsync,but an image backup would be pretty awesome.

I know macrium reflect (windows) can image a system that IS mounted, but I don't want to have to boot into Windows 7 once a night/week just to do a proper image (because Macrium actually DOES image /ext3 and /ext4 file systems)

---

### Post by seawolf167 on 2011-12-14
Take a look at their [how-to ]("http://clonezilla.org/livehd.php")for placing it on a hard drive.

---

### Post by x C0MMAND0 x on 2011-12-14
Awesome, thank you.  In their tutorial the say to make it /sda4 as the mnt point for the image.  What should I use in my case?  Here is my output

```
 sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bdd4a43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   196457471    98125312    7  HPFS/NTFS/exFAT
/dev/sda3       196458494   976771071   390156289    5  Extended
/dev/sda5       196458496   256456703    29999104   83  Linux
/dev/sda6       256458752   272457727     7999488   82  Linux swap / Solaris
/dev/sda7       272459776   976771071   352155648   83  Linux

Disk /dev/mapper/cryptswap1: 8191 MB, 8191475712 bytes
255 heads, 63 sectors/track, 995 cylinders, total 15998976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ef2a02c

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by seawolf167 on 2011-12-14
Did you resize and/or create a new partition for use by the clonezilla partition? If not, you'll want to do that first by using gparted (hit [ALT][F2], type in gparted), once that partition is created where you want to install clonezilla, then use that designation as the mount point

---

