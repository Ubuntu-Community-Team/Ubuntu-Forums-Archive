---
title: "Cannot boot XP, after installing Ubuntu 9.10"
date: 2009-12-08
forum: General Help
---

### Post by Ferrari69 on 2009-12-08
Hello,

I had 2 partitions with 2 XP. I selected the 1st partition, i formatted it, and i installed Ubuntu 9.10 on it.

Now i cant boot into XP cz is showing me the XP loader of the XP that i deleted..
i tried fixmbr,fixboot but nothing.

In the beggining XP couldnt boot, but at least i could browse the folders from Linux.
Now in the Disk Utility its written Unrecognised, Unkown or unused.

Screenshots:


[http://img690.imageshack.us/i/screen1di.jpg/](http://img690.imageshack.us/i/screen1di.jpg/)

[http://img38.imageshack.us/i/screen2rj.jpg/](http://img38.imageshack.us/i/screen2rj.jpg/)





here it is:

    ~# fdisk -l
    
    
    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    
    255 heads, 63 sectors/track, 30401 cylinders
    
    Units = cylinders of 16065 * 512 = 8225280 bytes
    
    Disk identifier: 0xb7e61057
    
    
       Device Boot      Start         End      Blocks   Id  System
    
    
    /dev/sda1   *           1       22508   180795478+  83  Linux
    
    /dev/sda2           22509       30400    63392490    f  W95 Ext'd (LBA)
    
    /dev/sda5   *       22752       30400    61440592+   7  HPFS/NTFS
    
    /dev/sda6           22509       22751     1951834+  82  Linux swap / Solaris

 

        ~#
        ~# ntfsfix /dev/sda5
        Mounting volume... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        Failed to startup volume: Input/output error.
        FAILED
        Attempting to correct errors... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        FAILED
        Failed to startup volume: Input/output error.
        Volume is corrupt. You should run chkdsk.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

update view, after playing with some partition boot CDS:

```

root@ubuntu-tower:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22508   180795478+  83  Linux
/dev/sda3           22752       30400    61440592+   7  HPFS/NTFS

```


preparing now screenshot of GParted and Disk Utility:

[http://i46.tinypic.com/4hvdyc.jpg](http://i46.tinypic.com/4hvdyc.jpg)


wat should i do? any ideas?

Thanks.

---

### Post by lidex on 2009-12-08
I think the first order of business is to get windows to boot. Try booting from your windows disk and repairing:
[http://michaelstevenstech.com/XPrepairinstall.htm]("http://michaelstevenstech.com/XPrepairinstall.htm")
[http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx]("http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx")
[http://www.techspot.com/vb/topic8356.html]("http://www.techspot.com/vb/topic8356.html")
[http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm]("http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm")

---

### Post by Ferrari69 on 2009-12-08
> **lidex said:**
> I think the first order of business is to get windows to boot. Try booting from your windows disk and repairing:
[http://michaelstevenstech.com/XPrepairinstall.htm]("http://michaelstevenstech.com/XPrepairinstall.htm")
[http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx]("http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx")
[http://www.techspot.com/vb/topic8356.html]("http://www.techspot.com/vb/topic8356.html")
[http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm]("http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm")

i did all the fixmbr, fixboot, bootcfg.exe, etc commands..
using xp cd, and vista recovery cd

---

### Post by RedRat on 2009-12-08
I could be really off-base here, but I was under the impression that Windows likes being on the first bootable drive, in your case sda1, not sda2 or sda5. Maybe someones else has some insight here.

---

### Post by lidex on 2009-12-08
> **RedRat said:**
> I could be really off-base here, but I was under the impression that Windows likes being on the first bootable drive, in your case sda1, not sda2 or sda5. Maybe someones else has some insight here.

That is correct. I'm thinking the best option at this point may be re-installing windows to first partition, recovering data from 2nd install, backing up ubuntu data and then re-installing ubuntu using this guide: [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

The first partition windows install should be left intact. All other partitions can be overwritten/formatted at that point.

---

### Post by Leppie on 2009-12-08
Windows does **not have** to be on the first partition of a disk. I've got mine booting of the 2nd, and I've other systems booting windows off higher partitions.
You may need to have to reconfigure the boot.ini file in your windows partition. It should look something like this:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

You could also use the bootcfg.exe in combination with the recovery console to modify the boot.ini file. bootcfg.exe is not present in every version of xp.

---

### Post by Ferrari69 on 2009-12-08
> **Leppie said:**
> Windows does **not have** to be on the first partition of a disk. I've got mine booting of the 2nd, and I've other systems booting windows off higher partitions.
You may need to have to reconfigure the boot.ini file in your windows partition. It should look something like this:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

You could also use the bootcfg.exe in combination with the recovery console to modify the boot.ini file. bootcfg.exe is not present in every version of xp.

i did all the fixmbr, fixboot, bootcfg.exe, etc commands..
using xp cd, and vista recovery cd

and i cannot edit the boot.ini, as i dont have access to the C drive files.

---

### Post by lidex on 2009-12-08
> **Leppie said:**
> Windows does **not have** to be on the first partition of a disk.
That is correct, but it sure does "play with others" better if it is. Therefore a better option for the uninitiated.

---

### Post by Leppie on 2009-12-08
> **Ferrari69 said:**
> i did all the fixmbr, fixboot, bootcfg.exe, etc commands..
using xp cd, and vista recovery cd

and i cannot edit the boot.ini, as i dont have access to the C drive files.

Did you also run the chkdsk /f command as suggested in gparted?

---

### Post by Ferrari69 on 2009-12-08
> **Leppie said:**
> Did you also run the chkdsk /f command as suggested in gparted?

yes, but is not working at all. the command doesnt execute at all

---

### Post by Leppie on 2009-12-08
> **Ferrari69 said:**
> yes, but is not working at all. the command doesnt execute at all

It may be the /f option. I just had a look at [this page]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/recovery_console_cmds.mspx?mfr=true") and apparently there is no /f option for chkdsk. Try the /P option instead.

---

### Post by Ferrari69 on 2009-12-08
> **Leppie said:**
> It may be the /f option. I just had a look at [this page]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/recovery_console_cmds.mspx?mfr=true") and apparently there is no /f option for chkdsk. Try the /P option instead.

i tried /f /r but werent recognised..ill try the /P

---

### Post by lisati on 2009-12-08
> **Ferrari69 said:**
> i tried /f /r but werent recognised..ill try the /P

Could be that it's changed with Vista. (/me rushes off to check)

edit: back in Ubuntu now. I started my copy of Vista in safe mode with command prompt. "chkdsk /?" reports that there's a "/F" option. <aside>Mrs Lisati now wants some attention......</aside>

---

### Post by Leppie on 2009-12-08
> **Ferrari69 said:**
> i tried /f /r but werent recognised..ill try the /P

fingers crossed...

---

### Post by Ferrari69 on 2009-12-08
> **Leppie said:**
> fingers crossed...

parameter not recognised.. but i tried all the valid NTFS parameters and nothing..

it doesnt let me start cz there is not an assigned letter "C:" or something..

---

### Post by Leppie on 2009-12-08
> **Ferrari69 said:**
> parameter not recognised.. but i tried all the valid NTFS parameters and nothing..

it doesnt let me start cz there is not an assigned letter "C:" or something..

do you have the fdisk command available? fdisk may be able to fix the partition table.

---

### Post by oldfred on 2009-12-08
leppie is correct that windows does not have to be on the first partition, but it just about has to be on a primary partition. The exception is if you boot another copy of windows from a primary partition then you can boot the copy in an extended/logical partition via the copy in the primary. If your windows is in an extended you can reinstall a copy of windows in a primary or just reinstall. You may be able to move it to another primary partition or boot from a floppy or CD.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

HOWTO: Moving/Copying Windows XP to another Partition 
[http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146)

Microsoft XP boot disk
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

---

### Post by lidex on 2009-12-08
Can TestDisk be of use here? I know it can be used to fix partition tables and MBR.
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

