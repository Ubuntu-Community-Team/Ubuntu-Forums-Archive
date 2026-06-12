---
title: "Help! - Accidentally deleted Windows 7 during Wubi recovery?"
date: 2011-03-08
forum: General Help
---

### Post by kaishan on 2011-03-08
Hi, all.  I need help figuring out what exactly I did here to aid in attempting to recover my Windows system.  My laptop was dual Wubi-boot with Windows 7 and Ubuntu, and after encountering issues booting into my Wubi Ubuntu, I went in to recover important files to do a reinstall.  Using an Ubuntu livecd, I created a directory called "win" (sudo mkdir /win) and then mounted my Windows 7 partition (sudo mount /dev/sda1 /win) to that folder name.  However, after encountering some issues there, I made the mistake of removing the "win" folder without unmounting the Windows 7 partition using "rm -rf /win".  After that, my Windows system appears to be missing.  Can anyone tell me what exactly I did?  Did I delete the partition?  Any assistance would be greatly appreciated, as I am hoping that I can recover from this rather than reinstalling everything.  Thanks so much!!

---

### Post by kaishan on 2011-03-20
Anyone know what I did here?  Thanks!

---

### Post by MrRichard on 2011-03-20
Have you tried looking at your hard disk with Gparted? It should give you a graphical layout of partitions on your hard drive. The original Windows partition (if any) would show up as NTFS format.

---

### Post by WorMzy on 2011-03-20
If that command executed, you have indeed deleted all the data from your Windows partition.

Not all hope is lost though, it may be recoverable.

Stop using the hard drive immediately, then look at this: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by kaishan on 2011-03-20
Hi, Mr. Richard.  Thanks for the reply!  Via Gparted the partitions (primary Windows 7 partition and a recovery partition) are visible, but all the folders are empty of files.  When I tried the Windows recovery disk, it doesn't find the Win OS so it doesn't really do anything.  I've also tried using Testdisk to see if it can aid in recovery, but it keeps generating a "disk too small" error and suggests that I confirm that the BIOS sees the HD (which appears to be fine).  I can access the drive and move around, but everything is missing.  I removed it from the laptop and used Recuva to do a deep scan, and that has found some files but am having issues getting it to let me recover the files without locking up on me.  Did that command essentially delete the partition or the necessary tables?  Thanks so much!!

---

### Post by WorMzy on 2011-03-20
It would have just deleted all the files. It wouldn't have modified the partition itself.

---

### Post by Rubi1200 on 2011-03-20
Hi,

please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kaishan on 2011-03-20
Hi, WorMzy.  Thanks for responding!  Ugh...that was my fear.  Did I basically delete the partition?  RE Testdisk, I've been trying to recover with that but it keeps giving me "disk too small" errors after I try to fix whatever it suggests.  Also, I attempted a run with the Windows system recovery disk but I have a feeling that an attempted repair there may have overwritten something that is preventing Testdisk from easily fixing the issue (that or I'm not using it correctly, which is totally possible.)  For example, when I browse the HD I see empty folders, which seems unusual if everything was deleted, so I am wondering if the system recovery added those folders before it failed to recover.  I connected the drive to my other Win7 machine and have been trying to recover files via Recuva, but it seems to be having trouble handling the simple viewing of the large numbers of files that come back.  Thanks!

---

### Post by WorMzy on 2011-03-20
No, the partition itself should be fine, it'll just be empty*. I've never used Testdisk myself, but I would guess that the "disk too small" error is produced when trying to recover more data than the disk is capable of holding. If that's the case, then I would guess that you're either trying to recover data to a different, smaller partition, or testdisk is trying to copy the files to unused space on the partition, in an attempt to avoid overwriting currently unrecovered files. I assume you're following this tutorial: [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

If so, do you have any other (preferably larger) partitions where you can write the recovered data temporarily?


*In the sense that the filesystem is reporting that there's no files on it, the data should still be there, more or less, the filesystem just doesn't know about it.

---

### Post by kaishan on 2011-03-21
Hi, Rubi1200.  Sorry for the delay in responding.  I had the computer offline trying to use Recuva to recover files but without much luck.  I think the Win7 System Recovery disk may have written some empty folders to the HD given that some of the files appeared overwritten even though I haven't written to it.  Anyway, I ran that script and pasted the results below.  Thanks so much to everyone for helping me!  Look forward to your analysis.    

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   948,195,327   948,193,280   7 HPFS/NTFS
/dev/sda2         948,195,328   976,766,975    28,571,648   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        48C84BB277B05936                       ntfs                                     
/dev/sda2        C4ECA04AECA03916                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by oldfred on 2011-03-22
The command you ran is the classic delete everything including the force & recursive options.

you should unmount with the umount command. And if you want to remove the directory you can use rmdir command. See man rm or man rmdir.

While photorec may recovery some files, you will not be able to recover a bootable system as any one file missing will cause issues. Time to reinstall from your windows recovery disk and restore backups. 

If you do have any data files that you did not backup, use photorec, but immediately stop writing anything to the drive.

---

### Post by kaishan on 2011-03-22
Hi.  Thanks!  Yeah, I'm thinking that it'll probably be an Ubuntu only laptop now.  :)  I managed to recover a few key files with Recuva, but have been holding off on installing Ubuntu until I was sure I was out of luck.  A lesson was definitely learned from this fiasco!

---

### Post by kaishan on 2011-03-23
Hi, all.  Just a quick update...  First, thanks for all the help!  I managed to recover the most critical files using a Recuva deep scan, and after trying several runs with Testdisk and other software, I decided to call it quits and just completely install Ubuntu.  I'm sure I'll never look back...  :)  Again, thanks so much for all the help.

---

### Post by Rubi1200 on 2011-03-24
Glad to hear you managed to get some data back and go for a fresh install.

Good luck and don't forget to come here if/when you need help with anything.

---

