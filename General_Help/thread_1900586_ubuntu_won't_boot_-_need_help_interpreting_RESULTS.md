---
title: "ubuntu won't boot - need help interpreting RESULTS.txt file"
date: 2011-12-26
forum: General Help
---

### Post by matak-attack on 2011-12-26
Hi all,

My computer died on me one day and when I went to restart it, it would not boot.
I'd seen this happen before so I knew to boot with the liveUSB and  download/run the boot info script! So I did, using this:
```
sudo bash ~/Desktop/boot_info_script*.sh
``` and ended up with a results.txt file. 
Below are the  results, if anyone knows what I should do next it would be VERY much  appreciated as I work from home and need this little bugger to come back  to life. Thanks!

Results of boot info script:

             ```
     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>........>.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1119704 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sda1 starts at sector 
                       0. But according to the info from fdisk, sda1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   
sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2013 MB, 2013265920 bytes
62 heads, 62 sectors/track, 1022 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             62     3,928,567     3,928,506   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       ecc9b83b-de12-4661-bd6c-32be7e112569   ext3       
/dev/sda1        DB0C-A468                              vfat       PENDRIVE
/dev/sdb1        94f49a64-208f-46f4-89d8-a896bf529f1e   ext4       
/dev/sdb5        9600d7b9-2256-4264-8078-00fbff910fa5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
/home/ubuntu/Desktop/boot_info_script.sh: line 1997: 14112 Killed                  mount -r -t "${type}" ${part} "${mountname}" 2>> ${Mount_Error}
```

---

### Post by oldfred on 2011-12-26
Script does not show much, it errored out. It may be related to some of the number processing bits that Gert is fixing now. See this thread. Download the newest (start at last post and work to front) and add in the suggested apps (gawk, lzma and/or xz-utils). He has both a file posted and wget direct download versions, so try one or several.

[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

Your system is promoting the flash drive to sda. Does removing the flash drive then let it work as drive order then changes?

---

