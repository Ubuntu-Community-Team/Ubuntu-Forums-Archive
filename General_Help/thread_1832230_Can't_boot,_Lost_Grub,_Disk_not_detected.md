---
title: "Can't boot, Lost Grub, Disk not detected"
date: 2011-08-24
forum: General Help
---

### Post by Zanon on 2011-08-24
My dual booting Ubuntu/windows computer is failing to boot and displays the following message:[INDENT]error: no such device e1bce359-b3b5-47b9-859b-74531cd9c746.
grub rescue>
[/INDENT]I used the Ubuntu Secured 64bits live CD  to run “Boot Repair” and this reported:[INDENT]“There is no boot backup nor Linux distribution on this computer.
To repair your boot, it is recommended to use a Windows repair CD for example. It is a non-trivial and risky manipulation, so please backup your data before."  

[/INDENT]I also tried Super Grub2 Disk but this could not find any Grub files. It could identify the Windows OS but not Ubuntu. I can launch Windows OS only from Super Grub2 Disk (but I am not too concerned about my Windows OS). I also tried Rescatux and this failed to reinstall or update Grub.

I entered "sudo fdisk -l" in a terminal and got the following:[INDENT] Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79372110   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

[/INDENT]This command should have identified "Disk /dev/sdb: 500.1 GB" but failed to do so (sdb is where my Ubuntu OS resides).

Also, I got the following results from running the Boot Info Script (which also failed to identify Disk sdb):  
  

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid e1bce359-b3b5-47b9-859b-74531cd9c746 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4244E25B44E250E9                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

This issue appears similar to a recent problem that I had which was solved ([http://ubuntuforums.org/showthread.php?t=1817667](http://ubuntuforums.org/showthread.php?t=1817667)). On the previous occasion I could find Disk sdb but couldn't mount it. My current problem differs in that I am unable to find Disk sdb. 

However, the problems are similar in that they appeared to occur in the same way:- On both occasions Ubuntu was displaying a blank screen having appeared to have gone to, or to be about to go to.  I interrupt this by touching mouse and keyboard and screen remains blank (normally, the login screen would appear). I should add that I do this many times without any problem and have no ideas why this should affect Grub/boot but my feeling is that it does in some way (but it could just be co-incidental). My other feeling is that the issue isn't hardware related (I believe the disk to be sound). However, these are just my feelings and I could be in error.

My assumption is that if my system can detect Disk sdb and mount it that everything would I would be able to be back working normally and I would be able to launch my Ubuntu OS. 

I would be very grateful for any help or advice.

Kind regards,

Adrian

---

### Post by oldfred on 2011-08-24
Is BIOS showing your second drive? It looks like it is not plugged in or totally missing.

Did you do any disk checks after your previous issues. I look with Disk Utility and click on drive and see if SMART status is "healthy".

---

### Post by Zanon on 2011-08-24
Hi Oldfred,

Many thanks for your advice, you appear to have solved the issue.

I had checked Disk sdb with disk utility and this reported that the disk was healthy. And, from using the disk regularly, it did feel sound.

Following your advice I checked BIOS and it did not show the disk!

I opened up my machine and all the cables appeared fitted correctly. I unplugged and replugged the cables to the disk just in case and, when I restarted the machine, it worked normally and launched straight into Ubuntu. 

My machine has been undisturbed, in the same location for many years but, despite this, it would seem that one of the cables had not been securely seated.   

I imagine it is quite embarrassing for the problem to be down to a loose cable! :redface: (Not quite as bad as failing to plug the machine into the power supply! :P)

Many thanks for your response; without your suggestions I would have been spent days (if not weeks) in search of a solution (and still may not have found the answer).

Kind regards,

Adrian

---

### Post by oldfred on 2011-08-24
Glad you found problem.

I have yet to open my case and not knock something out of place, so I always double check & still often have to go back and push on something.:)

---

