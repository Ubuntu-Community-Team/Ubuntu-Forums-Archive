---
title: "Mounting /dev failed"
date: 2011-04-26
forum: General Help
---

### Post by justincredibal on 2011-04-26
I have been running ubuntu on my laptop through wubi for roughly a month with no problems. After the last reboot my computer gave me this error when trying to boot into ubuntu and nothing I have done has changed it. I have searched the forums and found people with similar problems but not quite the same since they were not wubi installs. Their problems were not solved.

Here is the error.

```
mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)
```


Info I have gathered:

                ```
#Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   156,299,263   156,092,416   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       05d9fbe2-7699-4cc9-93b1-58b1a15e68cd   ext4                                     
/dev/sda1        6AC847F0C847B8D9                       ntfs       System Reserved               
/dev/sda2        BEB015D9B015994B                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 892:  4687 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
loop: can't delete device /dev/loop1: Device or resource busy
umount: /media/BEB015D9B015994B: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))#

```

Thanks for any help in advance!

---

### Post by justincredibal on 2011-04-26
Bump!

---

### Post by justincredibal on 2011-04-26
i r doomed??

---

### Post by TeoBigusGeekus on 2011-04-26
Can you post us the contents of /etc/fstab?

---

### Post by bcbc on 2011-04-26
I would copy the file C:\ubuntu\disks\root.disk to a backup source from Windows first.

Then run fsck on the root.disk:
Boot a current Ubuntu CD in live cd mode (Try without installing), and do the following: 
```
sudo mkdir /win
sudo mount /dev/sda2 /win
sudo fsck /win/ubuntu/disks/root.disk
```

You might also consider running chkdsk on windows (but I don't think this is the issue here):
Right click on Computer, Properties, Tools, Check disk for errors, fix automatically. You'll have to reboot into Windows complete the check.

---

