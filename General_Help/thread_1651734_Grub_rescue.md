---
title: "Grub rescue"
date: 2010-12-23
forum: General Help
---

### Post by Onda on 2010-12-23
Allright, I dual booted ubuntu with vista a while back, but I was running out of space on both partitions. So I thought I'd install ubuntu on another slightly smaller HDD from an old laptop. I thought all the ubuntu and grub stuff were on that one partition, so I thought if I just deleted it, all would be good. I isn't. Now when I boot up, I get a message saying 'Error, no such partition exists' and then 'Grub rescue:' and an input. So what I want now, is well, basically to be able to boot windows. I'm guessing I either have to remove grub, or just make it forget I ever had Ubuntu. If you need any extra info, let me know.

---

### Post by wilee-nilee on 2010-12-23
> **Onda said:**
> Allright, I dual booted ubuntu with vista a while back, but I was running out of space on both partitions. So I thought I'd install ubuntu on another slightly smaller HDD from an old laptop. I thought all the ubuntu and grub stuff were on that one partition, so I thought if I just deleted it, all would be good. I isn't. Now when I boot up, I get a message saying 'Error, no such partition exists' and then 'Grub rescue:' and an input. So what I want now, is well, basically to be able to boot windows. I'm guessing I either have to remove grub, or just make it forget I ever had Ubuntu. If you need any extra info, let me know.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

This will tell us what is where notice the code tags instructions for posting the text.

We can reload the mbr with the Vista bootloader or a compatible linux version, we just need to see what's there now.

Do you have a Vista recovery disc? if not download this one.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by Onda on 2010-12-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   218,596,446   218,596,384   7 HPFS/NTFS
/dev/sda2         218,596,455   234,438,590    15,842,136   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C470ACFB70ACF4F8                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/C470ACFB70ACF4F8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

Here you go, sorry it took a while.

---

### Post by wilee-nilee on 2010-12-23
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs: /bootmgr /Boot/BCD **/Windows/System32/winload.exe**

For some reason the highlighted part is not showing, but on occasion I have not seen this be a problem, but 90% of the time is a show stopper.

Down load the recovery vista from the link and burn it boot it to the repair section and open the terminal and run these two commands and see if it works. here some more instructions and a W7 forum link for a visual look at getting to the command line.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:

BootRec.exe /fixmbr 

BootRec.exe /FixBoot

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Onda on 2010-12-23
Works, big thanks man.

---

### Post by wilee-nilee on 2010-12-23
> **Onda said:**
> Works, big thanks man.

Cool that's what we hope for.:)

---

### Post by garvinrick4 on 2010-12-23
Hey wilee-nilee that worked out great where do you think the Windows/system 32/files
came from? Would be nice to know.

---

