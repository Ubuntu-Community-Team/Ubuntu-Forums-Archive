---
title: "Possibly a unique screwup here. HELP?"
date: 2010-07-28
forum: General Help
---

### Post by firebug7734 on 2010-07-28
I think that by copying part of the XP Install disk to C: as an .iso, I inadvertently changed the way my system boots permanently.

I am running LUBUNTU on a 1GB flash drive these days. I decided to back-up my Windows XP Professional Service Pack 2 CD from terminal. When I did so, I dd'ed the CD to /media/<HardDriveName(a bunch of numbers)>.iso and the computer seemed to freeze. I rebooted and now have a plethora of problems.

1) XP won't boot on the main computer. I get a corrupt/missing hal.dll error.

2) When running XP Disk itself, boot sequence fails...calling it a corrupt harddrive or viral. It advises chkdsk /f. Error code is 0x0000007B (0xF78D2524,0X00000034,0X00000000,0X00000000).

3) I can run my LUBUNTU flash disk just fine, but cannot seem to delete the iso file from my HDD. For that matter, I cannot delete any files form the HDD from the bootable LUBUNTU disk.

     a) I did successfully run a shred on the .iso file, but 
        cannot delete it.

I'm considering installing UBUNTU from a LiveCD onto my com as a dual-boot in the hopes that I will be able to access and delete the iso in question. Will this be the case? Or will all the stuff on my HDD be write-protected still? Also, this is not my computer, but a work one, so mods to things like boots sequences and partitions are very frowned upon. In essence, I would need to get the com back to an XP Service Pack 3 single-boot when it was all said and done. 

Thank you in advance for your help!

---

### Post by prodigy_ on 2010-07-28
Use Boot Info Script from my sig to diagnose the problem and post the results here.

---

### Post by firebug7734 on 2010-07-28
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,575,759   312,575,697   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,964,283     1,964,222   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bc411f1d-e219-4c63-9206-812127ecb2be   ext3                                     
/dev/sda1        24B88A60B88A2FFA                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        32F2-9A61                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/bc411f1d-e219-4c63-9206-812127ecb2be ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/24B88A60B88A2FFA  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/VX2PFPP_EN        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by prodigy_ on 2010-07-28
Since you don't have any non-Windows partitions, you should boot from your Windows XP installation CD and use the repair option. You don't need Ubuntu for that.

[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
[http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx)

---

### Post by firebug7734 on 2010-07-28
I tried that, but my XP installation disk returns the error message shown above. It won't load to the screen where I could select repair.

Also, (and I'm not sure about this) since this is a work computer, wouldn't I need the admin password to run repair?

---

### Post by prodigy_ on 2010-07-28
Did you try to run **chkdsk /f C:** from Windows recovery console?

---

### Post by firebug7734 on 2010-07-28
Well, I can't access the recovery console at all. From my XP disk, I get the following error message:

[FONT="Courier New"]A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:

*** STOP: 0x0000007B (0xF78D25524,0xC0000034,0x00000000,0x00000000)[/FONT]

At this point I can type nothing, do nothing. All I can seem to do is hold down the power button to shut down, then press again to restart the headache. 

Is there a way that I'm not seeing to run CHKDSK /F?

---

### Post by prodigy_ on 2010-07-28
Wait. Do you get this BSOD when trying to boot from a CD? If so, either the CD or the CD drive must be broken.

---

### Post by firebug7734 on 2010-07-28
I get it from booting from the CD. Hmmmm...troubling. I got this copy of XP years ago for cheap at my university bookstore. I don't fancy buying XP again...especially at full price. 

I don't think it's the CD drive, because I can run UBUNTU 10.04 live cd from it without a problem. All other disks seem to work just fine. Crap.

---

### Post by prodigy_ on 2010-07-28
You can you download an ISO image of XP (possibly even with integrated Service Pack 3) and make a bootable flash drive out of it. See [this HOWTO](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html). Just don't download any custom builds, get a copy of the original MSDN ISO.

But if you have hardware issues, a reinstallation won't fix them by itself. See [this MS help article](http://support.microsoft.com/kb/324103) for more info.

---

### Post by firebug7734 on 2010-07-28
Not sure where to find such a thing. Everywhere I've looked, I see "file removed for copyright infringement" etc. This is a work computer, so I *really* need anything I do to it to be on the up-and-up (i.e., no illegal software, etc.). 

Like I said, I'm pretty sure it has something to do with my placing that iso in the C: folder via my lubuntu live usb. It seems that if I can write things to another partition/hdd, then there should be a way to remove them too.

---

### Post by dino99 on 2010-07-28
if you cant resolve this xp issue, i let you know that ubuntu run smootly mostly each exe prog via wine (winhq) as i do since 2001 on my end

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

*** all my systems are windoz free *** :D

---

### Post by prodigy_ on 2010-07-28
> **firebug7734 said:**
> no illegal software
Then, if you're sure that your hardware is ok, you have two options:

1) Install a free OS (e.g. Ubuntu). Keep in mind that the support for Windows applications will be limited.
2) Buy a retail copy of Windows 7. It should allow you to downgrade to Windows XP legally. (Call Microsoft and discuss the details with their support. They have tool-free phone numbers and you can get the info you need about licensing.)

---

