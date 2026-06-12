---
title: "fall into grub-rescue after install / reboot"
date: 2012-05-16
forum: General Help
---

### Post by kotoro on 2012-05-16
I don't know why this is happening. Install drive is 3TB. Machine is HP xw8600. Grub has not been happy with several attempted installs, may require manual partitioning.

Please advise.

---

### Post by wilee-nilee on 2012-05-16
A drive that big is most likely a gpt setup, run these commands in ubuntu or on a live cd, look for results.txt in home and copy and paste all the text to a reply.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by kotoro on 2012-05-16
tried to reinstall again using a separate /boot partition and the rest set as root "/", but no dice. 

I DO have a smaller drive I could use, but I would prefer to use the large one if possible.

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2's core.img
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       585,971       585,938 Data partition (Windows/Linux)
/dev/sda2         585,972    64,585,972    64,000,001 Swap partition (Linux)
/dev/sda3      64,585,973 2,639,305,813 2,574,719,841 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34 3,907,029,134 3,907,029,101 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7aea0d7b-6119-44f3-adae-97962a538d99   ext2       
/dev/sda2        cf4da95c-9680-4aa6-9fcf-1781c97b38b0   swap       
/dev/sda3        0e0d4c12-b4c0-412c-8691-55f491974d94   ext4       
/dev/sdb1        CC50F9A050F99206                       ntfs       
/dev/sdc1        B81EB88F1EB84860                       ntfs       Data
/dev/sdd1        f247e0df-3ffe-410a-b145-4d0ca5ac8369   ext4       data
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                initrd.img-3.2.0-23-generic                   82
               =                vmlinuz-3.2.0-23-generic                      21

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=0e0d4c12-b4c0-412c-8691-55f491974d94 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=7aea0d7b-6119-44f3-adae-97962a538d99 /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=cf4da95c-9680-4aa6-9fcf-1781c97b38b0 none            swap    sw              0       0
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by wilee-nilee on 2012-05-16
Some of what is needed is there, but we need all the text from that results.txt 

So do this edit the original above by removing what is there, hit the advanced button in the edit click on this symbol # in the panel of the edit.
This generates code tags that look like this [ code][/code] Paste al the text inbetween. This makes it much easier to read.

I wont be helping you fix this but there are some regulars who will be on later that will. Looks like a basic fix.

That may all of it though as you are missing associated stuff with it in the sda3 partition.

---

### Post by kotoro on 2012-05-16
suspecting the drive might not be totally supported on the system I tried a 750GB drive as the boot drive and that works. Something was very off with the way the 3TB drive was being handled, so I'm probably better off leaving things as they are now.

---

### Post by wilee-nilee on 2012-05-16
> **kotoro said:**
> suspecting the drive might not be totally supported on the system I tried a 750GB drive as the boot drive and that works. Something was very off with the way the 3TB drive was being handled, so I'm probably better off leaving things as they are now.

Probably is but who needs the hassle eh, mark the thread as solved if you're all cool.

---

