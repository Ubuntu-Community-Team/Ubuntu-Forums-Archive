---
title: "/home UUID missing"
date: 2010-03-01
forum: General Help
---

### Post by leeden on 2010-03-01
Since Friday, I have not been able to boot up my system. I get stuck with the message,

"One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=37f2248d-5830-428d-b9dd-beed064b7441"

I have a dual boot system, Vista and Ubuntu 9.10. Two hard disks with an encrypted logical volume spanning both disks. It seems the system cannot find the UUID for my encrypted /home partition.

I searched and found the boot info script. The output is below. Any help would be appreciated.

NOTE:
/dev/sdc1 is the USB thumbdrive I used to run the script.
/dev/sda4 and /dev/sdb1 is the encrypted logical volume.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    105115644 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #5 for /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'

sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type 'crypto_LUKS'

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 56.
    Operating System:  
    Boot files/dirs:   

UltraMagnus-root: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

UltraMagnus-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

UltraMagnus-home: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

UltraMagnus-multimedia: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81b367f9

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,903,935    20,901,888  27 Hidden HPFS/NTFS
/dev/sda2    *     20,903,936   104,790,015    83,886,080   7 HPFS/NTFS
/dev/sda3         104,791,995   105,579,179       787,185   5 Extended
/dev/sda5         104,792,058   105,579,179       787,122  83 Linux
/dev/sda4         105,579,180   976,768,064   871,188,885  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9160c88

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders, total 512000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e565ddf

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  56       511,559       511,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/UltraMagnus-home: ambivalent result (probably more filesystems on the device)
/dev/mapper/UltraMagnus-multimedia ac1569f0-e405-4879-8d6a-2c9f73f91a1e   ext3                                     
/dev/mapper/UltraMagnus-root 61355732-277e-4da7-8699-9572f3708f2a   ext3                                     
/dev/mapper/UltraMagnus-swap af2ba4c6-36f3-4260-ad7a-b00a1c50777e   swap                                     
/dev/mapper/sda4_crypt 3PJ2Kn-NbG0-Qx5v-yHi9-NqkK-mDeU-cHCC4l LVM2_member                               
/dev/mapper/sdb1_crypt FlF0Ya-ymME-6Se4-SU5A-iDqQ-RSzK-fzPDnq LVM2_member                               
/dev/sda1        68A65FA8A65F7592                       ntfs       Recovery                      
/dev/sda4        4ef692c7-f614-45b3-b92c-1fb542678bb0   crypto_LUKS                               
/dev/sda5        d26902e0-cefb-4681-a1b2-8dbc56f5ae3f   ext3                                     
/dev/sdb1        bf925581-d88b-4490-a85e-9c56b8c465c1   crypto_LUKS                               
/dev/sdc1        E2FE-9E41                              vfat                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
UltraMagnus-home
UltraMagnus-multimedia
UltraMagnus-root
UltraMagnus-swap
control
sda4_crypt
sdb1_crypt

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/UltraMagnus-root /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdc1        /mnt                     vfat       (rw)


============================= sda5/grub/menu.lst: =============================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=/dev/mapper/UltraMagnus-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d26902e0-cefb-4681-a1b2-8dbc56f5ae3f

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

title		Ubuntu 9.10, kernel 2.6.32-02063202-generic
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.32-02063202-generic root=/dev/mapper/UltraMagnus-root ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
initrd		/initrd.img-2.6.32-02063202-generic
quiet

title		Ubuntu 9.10, kernel 2.6.32-02063202-generic (recovery mode)
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.32-02063202-generic root=/dev/mapper/UltraMagnus-root ro  crashkernel=384M-2G:64M,2G-:128M single
initrd		/initrd.img-2.6.32-02063202-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-19-generic root=/dev/mapper/UltraMagnus-root ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
initrd		/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-19-generic root=/dev/mapper/UltraMagnus-root ro  crashkernel=384M-2G:64M,2G-:128M single
initrd		/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-17-generic root=/dev/mapper/UltraMagnus-root ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
initrd		/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-17-generic root=/dev/mapper/UltraMagnus-root ro  crashkernel=384M-2G:64M,2G-:128M single
initrd		/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-15-generic root=/dev/mapper/UltraMagnus-root ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
initrd		/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/vmlinuz-2.6.31-15-generic root=/dev/mapper/UltraMagnus-root ro  crashkernel=384M-2G:64M,2G-:128M single
initrd		/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, memtest86+
uuid		d26902e0-cefb-4681-a1b2-8dbc56f5ae3f
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (Recovery)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn
root		(hd0,1)
savedefault
makeactive
chainloader	(hd0,4)/truecrypt.mbr
boot



=================== sda5: Location of files loaded by Grub: ===================


  53.8GB: grub/menu.lst
  53.8GB: grub/stage2
  53.6GB: initrd.img-2.6.31-15-generic
  53.7GB: initrd.img-2.6.31-17-generic
  53.7GB: initrd.img-2.6.31-19-generic
  53.7GB: initrd.img-2.6.32-02063202-generic
  53.6GB: vmlinuz-2.6.31-15-generic
  53.7GB: vmlinuz-2.6.31-17-generic
  53.7GB: vmlinuz-2.6.31-19-generic
  53.7GB: vmlinuz-2.6.32-02063202-generic

========================= UltraMagnus-root/etc/fstab: =========================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/UltraMagnus-root
UUID=61355732-277e-4da7-8699-9572f3708f2a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d26902e0-cefb-4681-a1b2-8dbc56f5ae3f /boot           ext3    relatime        0       2
# /dev/mapper/UltraMagnus-home
UUID=37f2248d-5830-428d-b9dd-beed064b7441 /home           ext3    relatime        0       2
# /dev/mapper/UltraMagnus-multimedia
UUID=ac1569f0-e405-4879-8d6a-2c9f73f91a1e /media/multimedia ext3    relatime        0       2
# /dev/mapper/UltraMagnus-swap
UUID=af2ba4c6-36f3-4260-ad7a-b00a1c50777e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# VirtualBox
none  /proc/bus/usb  usbfs  auto,busgid=126,busmode=0775,devgid=126,devmode=0664  0  0

# NAS
#192.168.1.201/public\040disk	/media/NAS200	cifs	auto,username=leeden,password=anonymous,uid=leeden,gid=leeden,workgroup=CYBERTRON,file_mode=0777,dir_mode=0777,rw	0	0


============= UltraMagnus-root: Location of files loaded by Grub: =============


  35.4GB: boot/initrd.img-2.6.27-11-generic
  35.5GB: boot/initrd.img-2.6.28-11-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  7f ed 9d c1 d9 05 56 b3  c1 44 aa c4 e6 19 7c 58  |......V..D....|X|
00000010  6e 11 93 b1 03 fa 1d 90  15 6e f6 59 04 36 19 a2  |n........n.Y.6..|
00000020  59 fa ba 23 d3 46 88 60  34 af 68 24 31 5a 31 f2  |Y..#.F.`4.h$1Z1.|
00000030  85 26 5a f1 a4 01 9a 64  a0 b1 86 23 4c 22 d9 0d  |.&Z....d...#L"..|
00000040  c2 97 bf 6c 22 f9 cc 78  c7 bb c7 d5 ea 1a 96 37  |...l"..x.......7|
00000050  6f fb 70 ac 6b 83 cc 71  f7 f7 bf 52 36 49 9f 27  |o.p.k..q...R6I.'|
00000060  19 10 ce c4 7c 1c a0 5d  1e 34 d4 e0 4a 91 a3 37  |....|..].4..J..7|
00000070  2f 6f 37 c3 86 07 a7 45  02 b7 ba 97 9f 95 ed d1  |/o7....E........|
00000080  a4 3a e2 34 ed 7a 5a ec  c2 eb 99 69 4b 29 bb a7  |.:.4.zZ....iK)..|
00000090  9b 3e 1f 83 b3 fd 03 1d  c8 6a 00 64 5e 49 97 4e  |.>.......j.d^I.N|
000000a0  6c 8b 29 78 5b cc 00 72  d5 d4 7d b4 4a 6c 3b 0e  |l.)x[..r..}.Jl;.|
000000b0  b2 16 07 29 e6 70 47 6c  f7 30 62 c4 08 e9 e3 51  |...).pGl.0b....Q|
000000c0  86 29 08 d2 fe 88 3c 7d  9a ec 36 ff 38 a8 55 de  |.)....<}..6.8.U.|
000000d0  93 37 e4 fa 44 d6 cd 37  53 c3 cf fc 33 ae b4 1e  |.7..D..7S...3...|
000000e0  4f 01 8b 7c e6 c4 c2 9b  23 6a 46 68 f5 95 8e 85  |O..|....#jFh....|
000000f0  86 91 c9 ae cb 59 d8 ed  45 09 f3 48 3d e5 88 3d  |.....Y..E..H=..=|
00000100  a9 a1 4f 6d 5a 98 ab 83  32 dc c5 0f 60 4b 7d 56  |..OmZ...2...`K}V|
00000110  a2 6c 22 ce 31 9e 4a ac  c4 f4 76 81 7a 47 e9 73  |.l".1.J...v.zG.s|
00000120  00 eb a3 0f 05 5f 69 a0  00 9f 73 f8 a4 74 4e 28  |....._i...s..tN(|
00000130  fd df cc fd fb 00 eb df  42 19 5f bf 48 b1 94 a9  |........B._.H...|
00000140  0c f0 6f 15 44 bc 70 e8  07 f8 5e 11 5a 33 8c 26  |..o.D.p...^.Z3.&|
00000150  c7 17 47 ea 18 53 9f 22  8e d1 a6 e6 78 9d 8d 62  |..G..S."....x..b|
00000160  69 8e e4 e7 a8 75 64 d3  c0 f6 20 2a d9 1c 9e a5  |i....ud... *....|
00000170  18 05 0e 9a 32 dd 30 49  46 b9 7c f3 53 aa 2f 8b  |....2.0IF.|.S./.|
00000180  20 d1 0e 11 3b cc 21 2d  44 12 f6 a8 34 24 fb 08  | ...;.!-D...4$..|
00000190  62 a4 4c 6e c1 c2 b6 9b  fc b6 3c 6a ea 76 89 af  |b.Ln......<j.v..|
000001a0  66 63 e6 c6 81 43 7e 6f  cc d2 ed 63 a6 f2 6d bf  |fc...C~o...c..m.|
000001b0  c1 7e 28 1e 7a 66 dc fc  75 a0 d4 79 6c 7a 00 ae  |.~(.zf..u..ylz..|
000001c0  10 bb c6 2d 5e 81 2f fe  ba 04 95 e2 eb 54 fe 65  |...-^./......T.e|
000001d0  db f0 36 63 8e 58 fb 6f  83 cc 7f 8b a4 ef 25 ed  |..6c.X.o......%.|
000001e0  dc 56 3f 8d 04 55 4d 49  78 72 bf e8 5e e6 c7 48  |.V?..UMIxr..^..H|
000001f0  e3 09 cc 5c 30 e7 e5 c8  b9 45 cb 7e ba 60 f3 55  |...\0....E.~.`.U|
00000200

Unknown BootLoader  on sda4

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  96 3c 45 8d 0f 90 34 45  51 7d bf 5e 1e 3e dc 8b  |.<E...4EQ}.^.>..|
00000080  81 0f 45 f0 0d 9e 25 6c  05 89 14 7d 96 fa 94 d4  |..E...%l...}....|
00000090  a8 d2 cb d1 b6 21 11 5c  9b dc 93 33 22 5b 4c 0e  |.....!.\...3"[L.|
000000a0  40 bd b1 28 00 00 00 0a  34 65 66 36 39 32 63 37  |@..(....4ef692c7|
000000b0  2d 66 36 31 34 2d 34 35  62 33 2d 62 39 32 63 2d  |-f614-45b3-b92c-|
000000c0  31 66 62 35 34 32 36 37  38 62 62 30 00 00 00 00  |1fb542678bb0....|
000000d0  00 ac 71 f3 00 06 10 b9  30 a2 47 f9 c6 34 56 cb  |..q.....0.G..4V.|
000000e0  95 bf 71 90 4e b6 fe 9a  a3 99 53 1c 1a 37 f6 34  |..q.N.....S..7.4|
000000f0  8a 7e ce 37 26 30 3c 71  00 00 00 08 00 00 0f a0  |.~.7&0<q........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdb1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  a9 52 67 a8 39 92 a0 00  d1 96 a2 5f 44 72 74 d6  |.Rg.9......_Drt.|
00000080  8a 89 c8 87 c1 2d 68 07  68 e7 93 96 5b 8a e4 c9  |.....-h.h...[...|
00000090  8d 8a 4d f9 e6 23 4c 24  ff 81 49 e9 22 da b7 4e  |..M..#L$..I."..N|
000000a0  be d9 f2 9e 00 00 00 0a  62 66 39 32 35 35 38 31  |........bf925581|
000000b0  2d 64 38 38 62 2d 34 34  39 30 2d 61 38 35 65 2d  |-d88b-4490-a85e-|
000000c0  39 63 35 36 62 38 63 34  36 35 63 31 00 00 00 00  |9c56b8c465c1....|
000000d0  00 ac 71 f3 00 05 f6 77  81 b2 64 6f 53 83 d0 0b  |..q....w..doS...|
000000e0  3a 57 f9 fc 4b 82 6e 36  ac 1a 28 16 1b f0 06 08  |:W..K.n6..(.....|
000000f0  7a 2d 7d 29 1e ce 3e d1  00 00 00 08 00 00 0f a0  |z-})..>.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by leeden on 2010-03-02
I solved the problem by hitting ESC after the error message.

Then manually mounting the home partition and rebooting.

```

sudo mount -t ext3 /dev/mapper/UltraMagnus-home /home

```

For some reason, upon reboot the UUID for the home partition reappeared and the system continued by running fsck.

---

