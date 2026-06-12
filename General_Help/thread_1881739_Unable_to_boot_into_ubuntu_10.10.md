---
title: "Unable to boot into ubuntu 10.10"
date: 2011-11-16
forum: General Help
---

### Post by karthick87 on 2011-11-16
I am unable to boot into ubuntu 10.10 all of a sudden, Please find the results attached below

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/core.img /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 30580 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             978,942   488,280,063   487,301,122   5 Extended
/dev/sda5             978,944     1,976,319       997,376  82 Linux swap / Solaris
/dev/sda6           1,978,368     2,975,743       997,376  82 Linux swap / Solaris
/dev/sda7           2,977,792   248,737,791   245,760,000  83 Linux
/dev/sda8         248,739,840   488,280,063   239,540,224  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a4d87872-3791-48d6-aec5-1971e02c65fa   ext4       
/dev/sda5        19e0a91f-91bd-4026-8f72-1fd2de5952a4   swap       
/dev/sda6        12dc4732-2c08-4389-a933-2401ceedbc56   swap       
/dev/sda7        4bbfe615-f899-4048-97fc-d376e126bb8a   ext4       
/dev/sda8        b26580d1-4838-4582-83e1-33d50bb58cbf   ext4       Datas
/dev/sdb1        13FD-2C64                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt/karthick/boot       ext4       (rw)
/dev/sda7        /mnt/karthick            ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda1/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
kernel /vmlinuz-2.6.18-128.1.1.el5 ro root=LABEL=/ console=tty0 console=ttyS1,19200n8
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.143443108 = 0.154020864    boot/grub/core.img                             1
   0.260124207 = 0.279306240    grub/core.img                                  1
   0.262209892 = 0.281545728    grub/menu.lst                                  1
   0.046393394 = 0.049814528    initrd.img-2.6.35-22-generic                   2
   0.026704788 = 0.028674048    vmlinuz-2.6.35-22-generic                      2

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
kernel /vmlinuz-2.6.18-128.1.1.el5 ro root=LABEL=/ console=tty0 console=ttyS1,19200n8
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4bbfe615-f899-4048-97fc-d376e126bb8a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a4d87872-3791-48d6-aec5-1971e02c65fa /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=19e0a91f-91bd-4026-8f72-1fd2de5952a4 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=12dc4732-2c08-4389-a933-2401ceedbc56 none            swap    sw              0       0
/dev/sda8 /media/Datas ext4 user,auto 0 0

--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.679069519 = 1.802887168    boot/grub/core.img                             1
   1.681155205 = 1.805126656    boot/grub/menu.lst                             1
   1.465338707 = 1.573395456    boot/initrd.img-2.6.35-22-generic              2
   1.445650101 = 1.552254976    boot/vmlinuz-2.6.35-22-generic                 2
  25.546592712 = 27.430445056   grub/core.img                                  1
   1.465338707 = 1.573395456    initrd.img                                     2
   1.445650101 = 1.552254976    vmlinuz                                        2

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```


Can someone help me pls?

---

### Post by raja.genupula on 2011-11-16
Hi karthick , its good to see you again.
 have you installed any thing previously or did any software upgrades ? 

do you have any old kernels in your system , if so have you tried to boot from them ? 

could you please provide the output of ```
dmesg
```

---

