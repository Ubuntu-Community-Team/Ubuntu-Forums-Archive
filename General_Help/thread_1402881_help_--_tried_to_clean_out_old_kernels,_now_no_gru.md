---
title: "help -- tried to clean out old kernels, now no grub entries left"
date: 2010-02-09
forum: General Help
---

### Post by ray field on 2010-02-09
in an attempt to whittle away some of the cruft, so as to be able to backup with remastersys, I performed the following as recommended somewhere (running Jaunty here):

```
sudo apt-get remove --purge 2.6.24-11-*
```

when it ran, it seemed to encounter all sorts of errors.  now when I try to boot, the only grub entry is memtest.  help!

---

### Post by arrange on 2010-02-09
Could you download the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") and post its output here?

---

### Post by ray field on 2010-02-09
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /IO.SYS /io.sys /MSDOS.SYS /msdos.sys /COMMAND.COM 
                       /command.com

sda6: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda14: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda15: _________________________________________________________________________

    File system:       hpfs
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda16: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda17: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda17 and 
                       looks at sector 154072026 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #17 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda18: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda19: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4982

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        16,064        16,002   a OS/2 Boot Manager
/dev/sda2              16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sda5    *         16,128     4,112,639     4,096,512   7 HPFS/NTFS
/dev/sda6    *      4,112,703     5,140,799     1,028,097   7 HPFS/NTFS
/dev/sda7    *      5,140,863     6,168,959     1,028,097   7 HPFS/NTFS
/dev/sda8    *      6,169,023    10,265,534     4,096,512   7 HPFS/NTFS
/dev/sda9    *     10,265,598    12,321,854     2,056,257   6 FAT16
/dev/sda10   *     12,321,918    14,378,174     2,056,257   7 HPFS/NTFS
/dev/sda11   *     14,378,238    18,474,749     4,096,512   7 HPFS/NTFS
/dev/sda12   *     18,474,813    22,571,324     4,096,512   7 HPFS/NTFS
/dev/sda13   *     22,571,388    24,627,644     2,056,257   7 HPFS/NTFS
/dev/sda14   *     24,627,708    32,820,794     8,193,087   7 HPFS/NTFS
/dev/sda15   *     32,820,858    94,269,419    61,448,562   7 HPFS/NTFS
/dev/sda16   *    135,187,038   153,629,594    18,442,557  82 Linux swap / Solaris
/dev/sda17   *    153,629,658   155,685,914     2,056,257  83 Linux
/dev/sda18   *    155,685,978   771,971,444   616,285,467  83 Linux
/dev/sda19   *    771,971,508   976,768,064   204,796,557  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ffe4391

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10                                              hpfs                                     
/dev/sda11                                              hpfs                                     
/dev/sda12                                              hpfs                                     
/dev/sda13                                              hpfs                                     
/dev/sda14                                              hpfs                                     
/dev/sda15                                              hpfs                                     
/dev/sda16       661f8d6d-ba39-48b5-b0fb-65eb0b3a160b   swap                                     
/dev/sda17       1b24c94e-3744-424b-b840-58c4aee3f0fc   ext3                                     
/dev/sda18       08478e3e-49bd-4991-9a60-bfd7d405e948   ext3                                     
/dev/sda19       553b909b-6b9b-49d2-a495-362e9a7c0364   ext3                                     
/dev/sda5                                               hpfs                                     
/dev/sda6                                               hpfs                                     
/dev/sda7                                               hpfs                                     
/dev/sda8                                               hpfs                                     
/dev/sda9        59EE-E414                              vfat                                     
/dev/sdc1        20E87C4FE87C2566                       ntfs       SimpleDrive                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /media/cdrom             iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SimpleDrive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda15       /media/disk-1            hpfs       (rw,nosuid,nodev,uhelper=hal)
/dev/sda18       /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda5        /media/dosdisk           hpfs       (rw,nosuid,nodev,uhelper=hal)


============================= sda17/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=08478e3e-49bd-4991-9a60-bfd7d405e948 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b24c94e-3744-424b-b840-58c4aee3f0fc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, memtest86+
uuid		1b24c94e-3744-424b-b840-58c4aee3f0fc
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda17: Location of files loaded by Grub: ===================


  78.8GB: grub/menu.lst
  78.8GB: grub/stage2

=============================== sda18/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# / was on /dev/sda18 during installation
UUID=08478e3e-49bd-4991-9a60-bfd7d405e948  /                ext3         relatime,errors=remount-ro  0  1  
# /boot was on /dev/sda17 during installation
UUID=1b24c94e-3744-424b-b840-58c4aee3f0fc  /boot            ext3         relatime                    0  2  
# /home was on /dev/sda19 during installation
UUID=553b909b-6b9b-49d2-a495-362e9a7c0364  /home            ext3         relatime                    0  2  
# swap was on /dev/sda16 during installation
UUID=661f8d6d-ba39-48b5-b0fb-65eb0b3a160b  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
# /dev/sda5                                  /dosdisc        hpfs         

# /dev/sda5                                  /media/dosdisk_  hpfs        users,user,owner            0  0  
# /dev/sda5                                    /media/dosdisk_  ntfs-3g     utf8,umask=007,uid=1000,gid=46 0 0
/dev/sda5                                  /media/dosdisk_  hpfs         umask=007,uid=1000,gid=46   0  0  
# /dev/sdb1                                  /media/Externale  vfat         defaults                    0  0  
/dev/sdb1                                  /media/SD_BAK    vfat         rw,user,noauto 0 0    
# /dev/sdc1                                  /media/sdc1      ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0  
# /dev/sdd1                                  /media/SD_BAK    vfat         defaults                               0  0  
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 82 3e 00 80 00 28 14  14 41 6a 00 00 00 00 00  |..>...(..Aj.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda6

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 10 01 00  |.N.IBM 4.50.....|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  01 b0 0f 00 80 00 28 14  54 30 6a 00 00 00 00 00  |......(.T0j.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda7

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 10 01 00  |.N.IBM 4.50.....|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  01 b0 0f 00 80 82 28 15  5c 71 6a 4d 41 49 4e 54  |......(.\qjMAINT|
00000030  45 4e 41 4e 43 45 48 50  46 53 20 20 20 20 00 00  |ENANCEHPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda8

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 82 3e 00 80 00 28 14  a4 60 6a 00 00 00 00 00  |..>...(..`j.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda10

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 20 01 00  |.N.IBM 4.50.. ..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  41 60 1f 00 80 85 28 14  04 2f 6a 56 4f 4c 55 4d  |A`....(../jVOLUM|
00000030  45 20 37 20 20 20 48 50  46 53 20 20 20 20 00 00  |E 7   HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda11

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 82 3e 00 80 00 28 14  b4 75 6a 00 00 00 00 00  |..>...(..uj.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda12

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 82 3e 00 80 00 28 14  94 37 6a 00 00 00 00 00  |..>...(..7j.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda13

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 20 01 00  |.N.IBM 4.50.. ..|
00000010  00 00 02 00 00 f8 fb 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  41 60 1f 00 80 00 28 14  a4 3d 6a 57 41 52 50 34  |A`....(..=jWARP4|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda14

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 f5 01  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  3f 04 7d 00 80 00 28 14  2c 3d 6a 00 00 00 00 00  |?.}...(.,=j.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda15

00000000  eb 4e 90 49 42 4d 20 34  2e 35 30 00 02 40 01 00  |.N.IBM 4.50..@..|
00000010  00 00 02 00 00 f8 a7 0e  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  72 a1 a9 03 80 00 28 14  7c 7d 6a 00 00 00 00 00  |r.....(.|}j.....|
00000030  00 00 00 00 00 00 48 50  46 53 20 20 20 20 00 00  |......HPFS    ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 a1 24  |.3.....|.......$|
00000060  00 a3 4d 00 cd 12 2d 4c  00 25 f0 ff c1 e0 06 a3  |..M...-L.%......|
00000070  4b 00 68 00 30 0f a1 64  66 81 3e 00 00 49 31 33  |K.h.0..df.>..I13|
00000080  58 75 05 c6 06 4f 00 01  c7 06 3e 00 00 00 c7 06  |Xu...O....>.....|
00000090  40 00 00 00 c7 06 45 00  14 00 a1 4b 00 8e c0 2b  |@.....E....K...+|
000000a0  db e8 23 00 ff 36 4b 00  68 82 02 a1 4d 00 26 a3  |..#..6K.h...M.&.|
000000b0  4d 00 26 a2 24 00 66 a1  1c 00 26 66 a3 1c 00 a0  |M.&.$.f...&f....|
000000c0  4f 00 26 a2 4f 00 cb 50  53 51 52 06 a1 3e 00 8b  |O.&.O..PSQR..>..|
000000d0  16 40 00 03 06 1c 00 13  16 1e 00 80 3e 4f 00 01  |.@..........>O..|
000000e0  74 6c 50 a1 1a 00 f6 26  18 00 8b c8 58 f7 f1 a3  |tlP....&....X...|
000000f0  42 00 8b c2 f6 36 18 00  fe c4 88 26 44 00 a2 25  |B....6.....&D..%|
00000100  00 a1 18 00 2a 06 44 00  40 3b 06 45 00 76 03 a1  |....*.D.@;.E.v..|
00000110  45 00 50 b4 02 8b 16 42  00 b1 06 d2 e6 0a 36 44  |E.P....B......6D|
00000120  00 8b ca 86 e9 8b 16 24  00 cd 13 58 72 5d 01 06  |.......$...Xr]..|
00000130  3e 00 83 16 40 00 00 29  06 45 00 76 0b c1 e0 05  |>...@..).E.v....|
00000140  8c c2 03 d0 8e c2 eb 84  07 5a 59 5b 58 c3 57 8b  |.........ZY[X.W.|
00000150  3e 24 00 8b 0e 45 00 8d  36 72 02 c7 04 10 00 89  |>$...E..6r......|
00000160  5c 04 8c 44 06 89 4c 02  89 44 08 89 54 0a 66 c7  |\..D..L..D..T.f.|
00000170  44 0c 00 00 00 00 b4 42  8b d7 cd 13 5f 72 ad eb  |D......B...._r..|
00000180  c7 be 7e 08 eb 08 be 02  02 eb 03 be ab 01 e8 09  |..~.............|
00000190  00 be 3e 02 e8 03 00 fb  eb fe ac 3c 00 74 09 b4  |..>........<.t..|
000001a0  0e bb 07 00 cd 10 eb f2  c3 1d 00 41 20 64 69 73  |...........A dis|
000001b0  6b 20 72 65 61 64 20 65  72 72 6f 72 20 6f 63 63  |k read error occ|
000001c0  75 72 72 65 64 2e 0d 0a  00 07 4f 53 32 4b 52 4e  |urred.....OS2KRN|
000001d0  4c 06 4f 53 32 4c 44 52  07 4f 53 32 42 4f 4f 54  |L.OS2LDR.OS2BOOT|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by arrange on 2010-02-10
Could you post the contents of the */boot* directory on your Ubuntu */dev/sda18* partition (accessible e.g. from a LiveCD)?

---

### Post by mal on 2010-02-10
> **ray field said:**
> in an attempt to whittle away some of the cruft, so as to be able to backup with remastersys, I performed the following as recommended somewhere (running Jaunty here):

```
sudo apt-get remove --purge 2.6.24-11-*
```

when it ran, it seemed to encounter all sorts of errors.  now when I try to boot, the only grub entry is memtest.  help!

Ray,

I don't consider myself a linux expert, so you probably should wait to see what other advice you get, but it seems to me that the command you ran here was pretty dangerous and probably had lots of unintended consequences, including apparently removing all of your kernel images.

It might be possible to recover your system by booting the LiveCD, finding the mount point for your main Jaunty partition and creating a chroot environment:

```
$ sudo chroot /path/to/jaunty/partition
```

Then reinstall the missing files, probably by installing the ubuntu-desktop package:

```
$ sudo apt-get update
$ sudo apt-get install ubuntu-desktop
```

Then type exit to leave the chroot environment and try to reboot your system.  Hopefully, this will install the latest kernel and any other missing packages.

Good luck.

Mal

---

### Post by Claus7 on 2010-02-10
Hello,

also when the next time you want to free some space by removing old kernels, do so with *great care* from synaptic. Just remove the headers and the images of the version you want to get rid of. That way you will free space from the /boot folder and /usr/src/ folders.

Regards!

---

### Post by ray field on 2010-02-10
I'm afraid I reached the same conclusion late last night, Mal, so I'm in the process of reinstalling from scratch.  I don't know exactly how I managed to glarp the kernel, guess maybe I mistyped something, but it sure would be nice if there was a simpler way to clear out old kernels.  

But I think there may be something off about the disk geometry as well, and since I've pretty well moved off OS/2, re-installing and setting up the partitions from scratch will let me set things up a little more cleverly.

---

### Post by Claus7 on 2010-02-10
Hello,

> **ray field said:**
> but it sure would be nice if there was a simpler way to clear out old kernels.  


from synaptic things are pretty harmless as long as you are careful on wiping out only those kernel versions you want to get rid of. Since Karmic's alpha releases I have tried it multiple times without any problem at all.

Regards!

---

