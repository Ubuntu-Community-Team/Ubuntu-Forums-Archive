---
title: "Help!....Error:file not found Grub Rescue"
date: 2012-08-16
forum: General Help
---

### Post by DuncanL on 2012-08-16
Hey guys, my laptop has a dualboot of windows 7 and Ubuntu (installed through windows WUBI) on 1 hard drive. 

Recently my ubuntu crashed and ended up having missing /sbin/int.

So I used the Boot repair and it told me that it has been repaired so it rebooted and gave me the result "missing bootmgr".

Then I got my bootmgr back using the Windows 7 CD.
But afterwards, I didnt have the option to select ubuntu on bootup.

I decided to reinstall grub by using the Ubuntu live CD by following the instructions here [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I wasnt sure which partition it was so I just chose sda1.

And now I have the Grub Rescue when i boot and i cant even go to windows.

**How can I fix this and get my original dualboot options back?**

and heres my bootinfoscript  

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30942959 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        411,648 1,369,847,807 1,369,436,160   7 NTFS / exFAT / HPFS
/dev/sda2       1,369,847,808 1,434,206,207    64,358,400   f W95 Extended (LBA)
/dev/sda5       1,369,849,856 1,434,206,207    64,356,352   7 NTFS / exFAT / HPFS
/dev/sda3       1,434,206,208 1,465,149,167    30,942,960  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C014315F1431599C                       ntfs       
/dev/sda3        0600377B003770B3                       ntfs       LENOVO_PART
/dev/sda5        6CDA7D16DA7CDDB0                       ntfs       LENOVO
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1



```Thanks!

*UPDATE*
Ok used the windows 7 cd to get my boot into windows back.

Is there still any chance to get dual boot to boot into ubuntu as an option?


*UPDATE*
Problem solved using easyBCD 2.0.

---

### Post by YannBuntu on 2012-08-16
Hello
In order to understand why Boot-Repair failed, please could you indicate your log history (run Boot-Repair, click "Advanced options", click the "Backup partition table..." button, save the ZIP file somewhere, then attach it to your reply in this thread).

---

### Post by Jt00 on 2012-08-16
Since you have fixed the problem, please mark the thread as solved under the thread tools menu so others can find the thread if they have this problem.

---

### Post by xianbei on 2012-08-16
it sounds like you got a boot loader back, but only for win7.

if this is the case, you may be able to search around to find instructions on getting your grub back to get back into your ubuntu.

one approach may be to boot to a live disk to change the boot partition on your comp's harddrive (gparted).

---

### Post by DuncanL on 2012-08-17
Thanks for the reply guys, I have got my boot menu back for both win 7 and ubuntu using easyBCD 2.0.

But is there a easier way to fix 'missing /sbin/int' next time, without having to lose my windows bootmgr?

@YannBuntu:
I have attached the Backup Partition Table if it helps.

---

### Post by YannBuntu on 2012-08-17
> **DuncanL said:**
> I have attached the Backup Partition Table if it helps.

Thanks. Looks like the problem was inside your Windows bootsector, so it had to be fixed via Windows/EasyBCD.

FOr your future reference: currently your Ubuntu is installed INSIDE Windows (via the Wubi installer), which is ok to try Ubuntu, but less reliable than a [standard install]("https://help.ubuntu.com/community/GraphicalInstall").

---

