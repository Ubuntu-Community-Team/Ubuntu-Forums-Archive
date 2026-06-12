---
title: "rebooted and now i cannt load either os"
date: 2010-11-24
forum: General Help
---

### Post by skandranon on 2010-11-24
I have been dual booting win7 and unduntu 10.10.

Last night I told windows to reboot. It then loaded to a page that says:

Error: no such devic: "lots of letters and numbers"
Grub rescue>

I have no idea how to load anything but a live cd at this opoint. How do I get grub to work again?

---

### Post by lmarmisa on 2010-11-24
Start your system from an Ubuntu Live CD (or USB stick with Ubuntu), open a terminal and type this command:

```

sudo fdisk -l

```

Please, post the output of this command.

---

### Post by boot_sectorz on 2010-11-24
had those problems for some time now. Only worked by booting Ubuntu live CD and run 
[HTML]sudo fsck /dev/sda5[/HTML]
Replace sda5 with your output of the command on second post. Will repair and you can boot
[http://ubuntuforums.org/showthread.php?t=1624024](http://ubuntuforums.org/showthread.php?t=1624024)

---

### Post by skandranon on 2010-11-24
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02f94d51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19458   156295361    7  HPFS/NTFS

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cb95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8666    69606400   83  Linux
/dev/sdb2            8666        9040     3004417    5  Extended
/dev/sdb5            8666        9040     3004416   82  Linux swap / Solaris

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0195c00b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdd5               2       30401   244187968+   7  HPFS/NTFS
ubuntu@ubuntu:~$



One of my raptors is not showing.. I think it is the one my master boot record and windows was installed on.. sda, I think? Still a ubuntu noob.

During post all 4 of my harddrives pass SMART and show up properly. Just looked I can not see the drive in places either.

To the second poster.. I have no idea what I am supposed to replace that with. I would assume somehting like sda cause thats where the MBR is but I really donno.

Thanks for your help. Let me know what to do next please!

Thanks!!!!!

---

### Post by lmarmisa on 2010-11-24
No information about /dev/sda. This looks odd. How many hard drives have you in your computer?.

---

### Post by wilee-nilee on 2010-11-24
Lets get to the heart of the matter. OP run the bootscript in my signature. With the generated text file come back to the thread open a reply click on the # and paste all the text between the code tags

---

### Post by skandranon on 2010-11-24
> **lmarmisa said:**
> No information about /dev/sda. This looks odd. How many hard drives have you in your computer?.

4


> **wilee-nilee said:**
> Lets get to the heart of the matter. OP run  the bootscript in my signature. With the generated text file come back  to the thread open a reply click on the # and paste all the text between  the code tags

Not quite sure I followed your directions right. Do not understand what # to click on or what code tags, but none the less here is the whole file output.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       312575999 sectors, but according to the info from 
                       fdisk, it has 312590721 sectors.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ?             0            -1                   Unknown
/dev/sdb2     ?             0            -1                   Unknown
/dev/sdb3     ?             0            -1                   Unknown
/dev/sdb4     ?             0            -1                   Unknown


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   312,592,769   312,590,722   7 HPFS/NTFS

/dev/sdc1 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065   488,392,064   488,376,000   f W95 Ext d (LBA)
/dev/sdd5              16,128   488,392,064   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdc1        1ABA7741BA771909                       ntfs       Alpha                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        48D08BAED08BA134                       ntfs       Omega                         
/dev/sdd: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown MBR on /dev/sdb


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sdb1: Input/output error
hexdump: /dev/sdb2: Input/output error
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
```

---

### Post by wilee-nilee on 2010-11-24
Now here is one of mine notice the difference in the text and that yours is missing some stuff. Did you run this script from a live Ubuntu cd?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    83,888,127    83,886,080   7 HPFS/NTFS
/dev/sda2         113,676,001   312,580,095   198,904,095   5 Extended
/dev/sda5         113,676,003   264,669,183   150,993,181  83 Linux
/dev/sda6         308,385,792   312,580,095     4,194,304  82 Linux swap / Solaris
/dev/sda7         264,671,232   308,383,743    43,712,512  83 Linux
/dev/sda3          83,891,430   113,675,939    29,784,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CFB6750453E160C                       ntfs       W7                            
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7D061649158B4024                       ntfs       share                         
/dev/sda5        6f28beba-e464-480e-9d4c-329416a13f3c   ext4       Lucid                         
/dev/sda6        c739a546-bd75-4a85-8a36-dc860c0895d2   swap                                     
/dev/sda7        dadc267d-cff9-4d6f-8551-b4a9c02fbeae   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=5
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro  vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single  vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2cfb6750453e160c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d26066da6066c537
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6f28beba-e464-480e-9d4c-329416a13f3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=05e757f7-cfb0-4edb-b045-f5c46524db5e none            swap    sw              0       0




=================== sda5: Location of files loaded by Grub: ===================


 109.8GB: boot/grub/core.img
  59.3GB: boot/grub/grub.cfg
 110.1GB: boot/initrd.img-2.6.32-24-generic
 110.2GB: boot/vmlinuz-2.6.32-24-generic
 110.1GB: initrd.img
 110.2GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
	echo	'Loading Linux 2.6.35-19-generic ...'
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2cfb6750453e160c
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro vga=758 quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single vga=758
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c739a546-bd75-4a85-8a36-dc860c0895d2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 148.6GB: boot/grub/core.img
 155.1GB: boot/grub/grub.cfg
 140.1GB: boot/initrd.img-2.6.35-19-generic
 149.0GB: boot/vmlinuz-2.6.35-19-generic
 140.1GB: initrd.img
 149.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  18 55 72 6c 50 61 72 61  6d 65 74 65 72 52 65 61  |.UrlParameterRea|
00000010  64 65 72 20 43 6c 61 73  73 95 cf 52 b8 cf 52 d3  |der Class..R..R.|
00000020  cf 52 00 01 2a 07 4d 65  6d 62 65 72 73 00 01 30  |.R..*.Members..0|
00000030  14 55 72 6c 50 61 72 61  6d 65 74 65 72 57 72 69  |.UrlParameterWri|
00000040  74 65 72 28 29 01 01 43  0c 43 6f 6e 73 74 72 75  |ter()..C.Constru|
00000050  63 74 6f 72 73 ad d0 52  00 01 30 0d 47 65 74 52  |ctors..R..0.GetR|
00000060  65 71 75 65 73 74 55 72  6c 01 01 4d 07 4d 65 74  |equestUrl..M.Met|
00000070  68 6f 64 73 d8 d0 52 03  1d 65 63 6d 61 3a 32 34  |hods..R..ecma:24|
00000080  38 32 23 55 72 6c 50 61  72 61 6d 65 74 65 72 57  |82#UrlParameterW|
00000090  72 69 74 65 72 2f 18 55  72 6c 50 61 72 61 6d 65  |riter/.UrlParame|
000000a0  74 65 72 57 72 69 74 65  72 20 43 6c 61 73 73 a2  |terWriter Class.|
000000b0  d0 52 c5 d0 52 e9 d0 52  00 01 2a 07 4d 65 6d 62  |.R..R..R..*.Memb|
000000c0  65 72 73 00 01 30 20 56  61 6c 75 65 43 6f 6c 6c  |ers..0 ValueColl|
000000d0  65 63 74 69 6f 6e 50 61  72 61 6d 65 74 65 72 52  |ectionParameterR|
000000e0  65 61 64 65 72 28 29 01  01 43 0c 43 6f 6e 73 74  |eader()..C.Const|
000000f0  72 75 63 74 6f 72 73 c3  d1 52 00 01 30 0e 47 65  |ructors..R..0.Ge|
00000100  74 49 6e 69 74 69 61 6c  69 7a 65 72 00 01 31 0a  |tInitializer..1.|
00000110  49 6e 69 74 69 61 6c 69  7a 65 00 01 32 2c 49 73  |Initialize..2,Is|
00000120  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000130  2e 52 65 66 6c 65 63 74  69 6f 6e 2e 50 61 72 61  |.Reflection.Para|
00000140  6d 65 74 65 72 49 6e 66  6f 29 00 01 33 3c 49 73  |meterInfo)..3<Is|
00000150  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000160  2e 57 65 62 2e 53 65 72  76 69 63 65 73 2e 50 72  |.Web.Services.Pr|
00000170  6f 74 6f 63 6f 6c 73 2e  4c 6f 67 69 63 61 6c 4d  |otocols.LogicalM|
00000180  65 74 68 6f 64 49 6e 66  6f 29 02 0b 49 73 53 75  |ethodInfo)..IsSu|
00000190  70 70 6f 72 74 65 64 0b  49 73 53 75 70 70 6f 72  |pported.IsSuppor|
000001a0  74 65 64 9a d2 52 ca d2  52 00 01 34 04 52 65 61  |ted..R..R..4.Rea|
000001b0  64 04 01 4d 07 4d 65 74  68 6f 64 73 fa d1 00 fe  |d..M.Methods....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1d f9 ff 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 1f 01  9b 0b 00 08 40 00 00 00  |............@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by skandranon on 2010-11-24
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       312575999 sectors, but according to the info from 
                       fdisk, it has 312590721 sectors.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ?             0            -1                   Unknown
/dev/sdb2     ?             0            -1                   Unknown
/dev/sdb3     ?             0            -1                   Unknown
/dev/sdb4     ?             0            -1                   Unknown


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   312,592,769   312,590,722   7 HPFS/NTFS

/dev/sdc1 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065   488,392,064   488,376,000   f W95 Ext d (LBA)
/dev/sdd5              16,128   488,392,064   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdc1        1ABA7741BA771909                       ntfs       Alpha                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        48D08BAED08BA134                       ntfs       Omega                         
/dev/sdd: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown MBR on /dev/sdb


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sdb1: Input/output error
hexdump: /dev/sdb2: Input/output error
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
 
```EDIT: ok found it made it work. Yes I ran it from a live cd. 10.04

EDIT 2: >  I think at the least you need to run a chkdsk /r on XP 

I am running win7, and I am not sure how to run a chkdsk without being able to boot it.

---

### Post by wilee-nilee on 2010-11-24
Not sure where to go from here to tell you the truth, the script if you compare it with mine is really devoid of any clues as to what is going on for me at least. If you can or are backed up if it was me I would just reinstall, but maybe waiting for other help might help.

Is this a raid setup? Not that I would know anything about that but others do.

---

### Post by Quackers on 2010-11-24
AFAIK you need to run it before bootup so that nothing is mounted.
Press the Windows key and R and in the run dialogue box type chkdisk /r and hit enter, Then reboot and it will run. The general wisdom is to keep running it until it reports no errors.
I would backup any important stuff immediately, just in case.

---

### Post by skandranon on 2010-11-24
> **wilee-nilee said:**
> Not sure where to go from here to tell you the truth, the script if you compare it with mine is really devoid of any clues as to what is going on for me at least. If you can or are backed up if it was me I would just reinstall, but maybe waiting for other help might help.

Is this a raid setup? Not that I would know anything about that but others do.

Not raid. Thank you for your help!

I keep no important data on either OS drive. I would have just reinstalled but a few weeks back when I first started to learn ubuntu and decided to dual boot I had a nightmare week trying to get them to boot correctly together. Pissed me off so much I almost gave up on ubuntu. Prolly would have but my girl had me install it on her pc. I wanted to be able to be her tech support and actually know wtf I was talking about so I stuck to it and made it work with help on the forum.

The problem is, I am not really learning much. I can follow directions, but I am lacking basic understanding on Linux commands and such. My own fault for not devoting more time to it.

Beside the point really... 

I just got COD black ops and I just want to play the D*#N thing atm, so if a reinstall is what it takes then so be it. Just dont want to spend a huge amount of time making dual boot work again.

More importantly I am starting to think I have a problem with on of my raptors. 

The first time I loaded the live cd I went into system -admin - disk ultility and it showed all four drives with SMART running and green, good to go. Poked around in the bois, didnt change anything, but did poke around.. Restarted with the live cd, and now the disk ultility is showing SMART unsupported. I have no idea why.

Uh, so I guess to sum up, I dont mind reinstalling, but I would like to make sure my drives are ok first. I dont want to have to keep reinstalling.

---

### Post by wilee-nilee on 2010-11-25
> **Quackers said:**
> AFAIK you need to run it before bootup so that nothing is mounted.
Press the Windows key and R and in the run dialogue box type chkdisk /r and hit enter, Then reboot and it will run. The general wisdom is to keep running it until it reports no errors.
I would backup any important stuff immediately, just in case.

Short of scripts that show nothing I must say thats the weirdest one I have seen, but it just may be due to not recognizing any clues, been kown to happen in my camp.;)

---

### Post by skandranon on 2010-11-25
> **Quackers said:**
> AFAIK you need to run it before bootup so that nothing is mounted.
Press the Windows key and R and in the run dialogue box type chkdisk /r and hit enter, Then reboot and it will run. The general wisdom is to keep running it until it reports no errors.
I would backup any important stuff immediately, just in case.

Seeing as windows + r does nothing on the live cd I am going to assume this only works if I can load windows. I can not load windows. Correct me if I am wrong here.

---

### Post by Quackers on 2010-11-25
Lol, it's certainly not a pretty sight :-)

Edit: Yes from within Windows only.

---

### Post by skandranon on 2010-11-25
I am happy to share I appear to be a l33t tard!

Decided to start over and reinstall. Opened my case and pulled the sata cables on my storage drives (something I always do JIC when reinstalling). Out of habit I pushed the other two drives cables back in. Turned the pc on (forgot to throw in a cd) and grub loaded. Everything works just as it did before.

Honestly I am baffled. Plugged my other drives back in and everything is still working fine. 

This seems like it can only mean the cable was slightly loose on one of the OS drives. But that really doesnt make any since because the computer was running for at least two days before I rebooted it. 

Ah, well... I have no idea. In any case, it works now! Back to black ops ;)

Thanks for everyones help!

---

