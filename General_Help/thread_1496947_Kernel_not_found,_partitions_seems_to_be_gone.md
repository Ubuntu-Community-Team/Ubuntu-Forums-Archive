---
title: "Kernel not found, partitions seems to be gone"
date: 2010-05-29
forum: General Help
---

### Post by surfnsound on 2010-05-29
When i tried to bring my computer out of hibernate this morning, it would not start back up. OK, it happens. I restarted it, but then i got a message that I can not remember, and I got a Grub command prompt. I checked avaiable options and saw boot was one of them, tried that, and got a message that it could not find the kernel. I got a suggeston of how to remount the root on Reddit, but i needed to know the number for the partition. I went into windows to find out, and it seems the partition is now gone. Can anyone tell me if there is anyway to fix this or even some clue how it might have happened?

---

### Post by bildr on 2010-05-29
you can enumerate partitions in the grub cli.  good luck, it isn't something that is easy to explain, once you do it you got it.  or you can boot from live media and fsck all partitions/make sure they exist.

---

### Post by surfnsound on 2010-05-30
It looks like the partition is gone, is there no chance to get my data back from it?

---

### Post by gamblor01 on 2010-05-30
How did you verify that the partitions are gone?  I would boot up with a live cd and check with:

```
sudo fdisk -l
```

What does it list?  Another alternative would be to enter into cfdisk (but don't make any changes).

I haven't heard of this type of thing happening unless the drive itself was going bad.  As bildr suggested, if you can, you will probably want to run fsck on your partitions.  You might also consider getting a new hard drive.  I would try to back everything up as soon as possible.  Alternatively, you can use the dd command to clone one hard drive to another.

For example, suppose you only have one drive (/dev/sda) and you put a new one into your system (/dev/sdb).  Then you can boot up in a live cd and clone the drive exactly by issuing the command:

```
sudo dd if=/dev/sda of=/dev/sdb bs=32256
```

At that point you can detach the "old" drive and leave the new one in.  It will now be seen as /dev/sda and the system will function with the new drive as if nothing ever happened.

Get the output of "sudo fdisk -l" from a live cd and post it here.  Hopefully you can salvage the data.

---

### Post by ryan858 on 2010-05-30
if the partition table is corrupted then that would explain the missing partition. You can use Testdisk to recover files regardless of the partition table. It will also find deleted files, but that's not likely to be the case. Another possibility is to just remake the partition table the way it should be, and that might just restore it back to how it was.

For example, if you make a partition and put some files on it, then use fdisk to delete the partition (and don't write anything else to the disk while its deleted) then you can add a new partition the same size and it will have the same files as the deleted one did, because its the same data in the table, pointing to the same locations on disk. Like if you make a 10240 MB partition and add files, then delete it, and make a new 10240 MB partition, then it will be an exact clone of the old one, and all the files will still be there.

---

### Post by yetiman64 on 2010-05-30
Definitely use 
```
sudo fdisk -l
```to check if its missing 1st (grub errors can cause all sorts of problems).

I personally have had to recover hard drive partitions from corrupted partition tables in the past using testdisk (booted the partitions using GAG bootloader- yet the very bootdrive gparted was being run from was being seen as unallocated by gparted). You can scan a drive completely with testdisk and provided its results are as you set it up, you can have it rewrite the partition tables and fix the partition access for grub to use etc.

Good luck.

---

### Post by surfnsound on 2010-05-30
Ran fdisk, here is the output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c09973a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9730    76612604    7  HPFS/NTFS

sda1 I think is a system partition that was on there from Toshiba. sda2 has all my windows files on it.

---

### Post by dino99 on 2010-05-30
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by yetiman64 on 2010-05-31
> **surfnsound said:**
> Ran fdisk, here is the output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c09973a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9730    76612604    7  HPFS/NTFS

sda1 I think is a system partition that was on there from Toshiba. sda2 has all my windows files on it.

NO linux partitions shown here at all. Possibly corrupted partition table. Can you still boot into Windows? (I'm assuming that's where you're currently working from).

What Ubuntu OS and grub version are you using? If 9.10 or later and grub 2 - Next step would be to download and run the bootinfo script from sourceforge.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

To use this, boot up a live cd to a desktop, open firefox and download the script, make it executable, run the script and post the results.txt file here either in quote tags or as an attachment (this script will output quite a lot of detail at times).

Edit: A good guide to using the bootinfo script is [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

This will give much more detail as to your setup and any problems. If your Ubuntu partitions still  aren't found testdisk may be one way to recover them.

---

### Post by surfnsound on 2010-05-31
I just ran TestDisk in Windows, it did find the old partition, and asked if I wanted to recreate the partition. I selected Yes, rebooted, and now I can't start up at all except for with the Live CD. Running Gparted from the LiveCd wont come up with anything, even though it reads an 80 GB storage device, but tat's all it says,, no longer Toshiba.... like it used to.

---

### Post by yetiman64 on 2010-05-31
> What Ubuntu OS and grub version are you using? If 9.10 or later and grub 2 - Next step would be to download and run the bootinfo script from sourceforge.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

To use this, boot up a live cd to a desktop, open firefox and download the script, make it executable, run the script and post the results.txt file here either in quote tags or as an attachment (this script will output quite a lot of detail at times).

Edit: A good guide to using the bootinfo script is [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

This will give much more detail as to your setup and any problems. If your Ubuntu partitions still aren't found testdisk may be one way to recover them.Firstly it would've payed to check out the boot_info_script from sourceforge before touching testdisk (sounds like a bit late now though). My suggestion above was to look further into booting and partition details before recovery attempts. Also my only experience with testdisk is the linux version and I have no idea regarding the Windows equivalent. 

I would tend to still try out the boot_info_script as its very detailed and may possibly still be of some use even if Windows testdisk use has done further partition table damage. Even though it appears further damage is done to the partition tables/MBR. Your data should still be in place on the drive and be recoverable. Good luck with further attempts -try out the boot info script first and let us know if it shows anything (post results back here).

---

### Post by surfnsound on 2010-05-31
Wish I had tried your post first. Everyone seemed to be mentioning Testdisk, so I figured if anything would work, that would be it. I did your suggestion, here is the output:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c09973a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        109A-010E                              vfat       &#139;Ò-R¶hÚ"r&#139;è                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


Looks like it changed my windows file system, which could explain my boot issues with that now. The rest is kind of greek to me, I coudln't tell you if my old partition for Ubuntu recoverable or not.

Thanks for all your help.

---

### Post by yetiman64 on 2010-05-31
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
This looks like your Ubuntu install may have been a wubi install, was it ??
 
With wubi installs, ubuntu is actually installed into a file/folder structure on the NTFS filesystem and there would be no ext partitions visible on the main drive sda, that it seems everyone has been looking for.

As compared to separate partitioning installs where grub is in the MBR of the boot drive, eg on my current install the same entry is 
> ============================= Boot Info Summary: ==============================

 => Grub 1.96 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #13 for /boot/grub.The boot_info_script output you've just posted would've immediately got me to steer you away from using testdisk (even though I'd previously mentioned it - with no mention of wubi, "normal" dual booting was assumed sorry).
 
Your next step is to wait for someone with experience in undoing the damage to the Windows partition table by testdisk, and if that is successful (ie you get to boot Windows again) focus your original problem to those with more knowledge of wubi installs.

Feel free to "bump" your thread once every 24 hours if it takes a while to get a reply (forum guidelines for bumping is once every 24 hours btw).

Good luck, I'll stay subscribed to this thread out of interest, and hope someone can help you out further soon.

---

### Post by surfnsound on 2010-05-31
Ugh. Well thanks for the help. When you run the wubi it does some typeof allocation for a partition, but I guess this sin't a true partition? That's the whole reason I went on this quest to find it whe my kernel went missing.

I have almost all my info backed up on a flash drive except my bookmarks and a few large pdfs, so worst (best?) case scenario I start from scratch, load Lucid Lynx and and say to hell with Windows.

---

### Post by surfnsound on 2010-06-02
Any chance by running Testdisk under my Ubuntu Live Cd I'd be able to undo whatever it is I did running it in windows? I created a log when running it, but sadly can'y access it now.

---

### Post by yetiman64 on 2010-06-02
It is possible to install packages to the live cd environment (you obviously will lose them each reboot you do). When installed it would need to be launched in the terminal. Did the windows version use a GUI?

---

### Post by surfnsound on 2010-06-02
> **yetiman64 said:**
> It is possible to install packages to the live cd environment (you obviously will lose them each reboot you do). When installed it would need to be launched in the terminal. Did the windows version use a GUI?
 
No. I'm rpetty sure they all run the same way, but it looks just like the example ont he Testdisk website. I'm more ust wondering if it is possible to undo whatever change to the partition I did, since following your instructions before shows I still have Windows installed in the MBR, I just don't know what I did that it wont boot. Is it possible it just changed my NTFS to FAT32 and that's why?

---

### Post by yetiman64 on 2010-06-02
**Post #7**
> **  Re: Kernel not found, partitions seems to be gone**             
                                                                Ran fdisk, here is the output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c09973a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9730    76612604    7  HPFS/NTFSShows sda1 as unknown, and sda2 as NTFS.

However the boot info script (run after last testdisk) is only finding sda1 (as fat32 - probably correct as it seems to be more thorough than fdisk in its info)
> sda1: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   > Is it possible it just changed my NTFS to FAT32 and that's why?      No.
Testdisk more than likely fudged the partition table entries for sda2, and this is what now needs "finding"

Note I'm no expert in this, but logically I'd say testdisk's last attempt may have come undone because of  > Partition 1 does not end on cylinder boundary.and failed to correctly write the entry for sda2 (The NTFS partition)

---

### Post by surfnsound on 2010-06-03
Does the search deeper option allow me to do anythting once I run it? I somehow missed this option the first time I saw it. I ran it thus time, and it seems to have found the old partition that was on there before I ran Testdisk in windows. Also it shows two warnings saying Incorrect number of heads/cylinder 2 (FAT) != 62 (HD) and Incorrect number of sectors per track 18 (FAT) != 63 (HD). Someone earlier mentioned they only heard of problems like this happening when the Drive is starting to go bad. This drive is approx. 3 years old. Think it's just time to call it quits on it?

---

### Post by surfnsound on 2010-06-03
OK, I have managed to get my Vista back. Now I am back to the original state I was looking for an answer to when all this began. When I tried to boot into Ubuntu, it takes me to a grub command prompt and when i type in boot it tells me kernel must me present. I know this was a wubi install, but any idea what I can do now?

---

### Post by yetiman64 on 2010-06-03
Definitely good to hear you got Vista access back, you've obviously worked well with Testdisk this time. 
> I know this was a wubi install, but any idea what I can do now?      Sorry but I know very little (only some very basic background reading etc.) on wubi as I never use it (only full partition dual booting here). If I where you I'd bump the thread daily untill someone with wubi knowledge helps you out.

Once again, I'll stay subscribed out of interest. Bye for now, and good luck, Nev.

---

### Post by surfnsound on 2010-06-08
Solved! I had to go back to running chkdsk in windows. There is a hidden folder Found.000 that contained the boot folder and root.dsk file. Moving them back into /ubuntu/disks solved the problem. Thanks for all the help. I'm going to attempt a true install once I back up what I want off this wubi install, so I'm sure I'll be back on here soon!

---

