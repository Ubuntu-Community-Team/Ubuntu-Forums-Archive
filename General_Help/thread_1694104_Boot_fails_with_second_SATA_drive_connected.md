---
title: "Boot fails with second SATA drive connected"
date: 2011-02-23
forum: General Help
---

### Post by Sauvage on 2011-02-23
having an issue I've been unable to resolve for for a week now. I've 2 drives, SATA1 for OS and operating files, SATA2 for media storage. came home last week to an update manager window present and error in Transmission stating unable to second drive due to "Read Only" status. the drive was never set to read only status but following the update manager a reboot was needed. once rebooted, the GRUB menu came up (dual boot system), selected Ubuntu then booting stopped. blank black screen with blinking cursor. rebooted several times, checked bios recognition of both drives, replaced cables, switched power to drive to separate cables, used different SATA ports but nothing worked. finally removed the second media storage drive and Ubuntu booted normally. now any time i connect the second drive and reboot it fails to boot into ubuntu or XP. i removed the media drive and installed it in another computer and it worked normally. have searched everything i can but no answers have been found so far. wondering if anyone here has had similar trouble or has idea for what to try.

I'm using Ubuntu 10.04 64 bit with current 3.6.32-28 kernel

---

### Post by drs305 on 2011-02-23
Was this drive ever cloned? I was wondering if it might have an identical UUID as a partition on the other drive. And I assume you checked the BIOS boot order with the second drive connected to ensure the Ubuntu/Windows drive is booted first...

We might learn something if you will boot, connect the second drive, then download and run the boot info script from the following site. Please post the RESULTS.txt file contents the script produces.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Sauvage on 2011-02-23
```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,797,952   625,141,759   420,343,808  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        32787DA6787D6A0D                       ntfs       XP                            
/dev/sda2        0eedab90-ceb6-4bde-998c-a9ed244694be   ext4       Ubuntu                        
/dev/sda                                                promise_fasttrack_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/XP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

...wall of text for grub loading menu 

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=0eedab90-ceb6-4bde-998c-a9ed244694be /               ext4    errors=remount-ro 0       1

=================== sda2: Location of files loaded by Grub: ===================

```

---

### Post by enkrypt3d on 2011-02-24
Silly question - check the bios boot order?

---

### Post by drs305 on 2011-02-24
Normally to troubleshoot boot problems we need to see the entire contents of RESULTS.txt.  We know it is a lot of information but if you enclose it within 'code' tags it doesn't take up much screen space. When creating a post, you can generate the tags by pressing the # icon in the post's menubar...

From what you posted, there is a snippet about RAID. I've never used RAID so I can't really offer a solution, but is it possible that when a second drive is connected your system is trying to use RAID (and failing)?

I know there are commands you can use to remove old remnants of RAID setups. Here is one thread that deals with the issue:
[http://ubuntuforums.org/showthread.php?t=1325650]("http://ubuntuforums.org/showthread.php?t=1325650")
I don't know if this might be your issue or not, but it's all I can offer at the moment.

And just to be sure, did you check the BIOS boot order as suggested by both of us who have responded?

---

