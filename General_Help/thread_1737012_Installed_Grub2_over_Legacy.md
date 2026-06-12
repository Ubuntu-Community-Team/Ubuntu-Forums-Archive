---
title: "Installed Grub2 over Legacy"
date: 2011-04-22
forum: General Help
---

### Post by snarlster on 2011-04-22
Hi everyone,

I just came back from a trip around the world... and my server had Ubuntu 9.04 installed on it as well as Windows XP. As I came home, I figured to upgrade to Win7 without looking to see which version of Grub I had installed, for some reason I expected it to be Grub2. I've reinstalled Grub2 before without problems with the following commands:

```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
sudo grub-install --root-directory=/media/sda2 /dev/sda

```So I went ahead and did the same and now when I boot up I get the following error:

> GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like editing is supported. For the first word, TAB listas possible command completions. Anywhere else TAB lists possble device or file completions 

Now the thing is, I need to upgrade my Ubuntu anyway... is there a way to just plain upgrade Ubuntu from the "Live CD" and will that fix my Grub issues? If not, I've been searching for a way to get my grub going again, will I need to get the Legacy Grub going again or can I just upgrade to the GRUB2 somehow now that I seem to have installed both?

Please help me out on this one... I've been spreading Ubuntu around the world for the last while but I got lots of data on the server that's all encrypted and a reinstall would not be so good!

Thanks

---

### Post by Rubi1200 on 2011-04-23
Hi and welcome to the forums :-)

Ubuntu versions before 9.10 use legacy-GRUB. From 9.10 onwards, GRUB2.

The best advice I can give right now is to do the following so we can see what is going on (adjust the instructions to take into account this is a server):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by snarlster on 2011-04-23
Hey there Ruby1200, thanks for your quick reply.

The "server" I was referring to is still just a desktop version of Ubuntu... I just call it my server since its not the PC I use for my personal computing. I am going out of town tomorrow morning and might therefore not be able to reply to your next reply for 48 hours from now. Thanks again for your help! Here's the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
 => Syslinux is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065   146,818,034   146,801,970   7 HPFS/NTFS
/dev/sda2         146,818,035   230,243,579    83,425,545  83 Linux
/dev/sda3         230,243,580   234,436,544     4,192,965  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   390,716,864   390,716,802  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1039 MB, 1039400960 bytes
32 heads, 62 sectors/track, 1023 cylinders, total 2030080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62     2,029,631     2,029,570   c W95 FAT32 (LBA)


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048   976,771,071   976,769,024  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   976,768,064   976,768,002  83 Linux


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1038 MB, 1038614528 bytes
255 heads, 63 sectors/track, 126 cylinders, total 2028544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63     2,024,189     2,024,127   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D898793B987918E8                       ntfs                                     
/dev/sda2        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b   ext3                                     
/dev/sda3        24c71e0e-bf40-4d16-9750-f6bf3ab545d0   swap       Swap                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e9f22211-239e-4b1b-b644-2c9e04b2869c   ext3       200 TÃ³nlist                  
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        be614bff-05c6-42a6-8ebd-6ff77505c788   ext3       200 Forrit Lesa               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        d7cb5e1c-9076-4dcc-841e-027b8c5a6406   ext3       500 Movies 2                  
/dev/sdd: PTTYPE="dos" 
/dev/sde1        66D2-3C39                              vfat                                     
/dev/sde: PTTYPE="dos" 
/dev/sdf1        b5053a6c-4586-4bf3-981d-c4a2b79fe5c6   ext3       500 ÃžÃ¦ttir                  
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        cc0ba3ab-4d4f-4064-a586-779136f6988b   ext2       500 Movies 1                  
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        7EB49DA2B49D5E09                       ntfs       Storage3                      
/dev/sdh: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdh1        /media/Storage3          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdf2 :
UUID=80ac46df-41f2-41dd-80d0-9bd5b3d7bb4b / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdf3 :
UUID=24c71e0e-bf40-4d16-9750-f6bf3ab545d0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sdc1 :
UUID=cc0ba3ab-4d4f-4064-a586-779136f6988b /media/1_Movies1_500GB3 ext2 errors=remount-ro 0 0
# Entry for /dev/sda1 :
UUID=d7cb5e1c-9076-4dcc-841e-027b8c5a6406 /media/2_Movies2_500GB1 ext3 errors=remount-ro 0 0
# Entry for /dev/sdb1 :
UUID=b5053a6c-4586-4bf3-981d-c4a2b79fe5c6 /media/3_Episodes_500GB2 ext3 errors=remount-ro 0 0
# Entry for /dev/sdg1 :
UUID=e9f22211-239e-4b1b-b644-2c9e04b2869c /media/4_Music_200GB4 ext3 errors=remount-ro 0 0
# Entry for /dev/sdh1 :
UUID=be614bff-05c6-42a6-8ebd-6ff77505c788 /media/5_Forrit_Lesa_Myndir_200GB5 ext3 errors=remount-ro 0 0
/dev/sdf1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sde1 /media/200\040#2\040-\040Admin ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda2: Location of files loaded by Grub: ===================


  85.7GB: boot/grub/core.img
  85.6GB: boot/grub/menu.lst
  85.7GB: boot/grub/stage2
  85.6GB: boot/initrd.img-2.6.28-11-generic
  85.7GB: boot/initrd.img-2.6.28-13-generic
  85.7GB: boot/vmlinuz-2.6.28-11-generic
  85.7GB: boot/vmlinuz-2.6.28-13-generic
  85.7GB: initrd.img
  85.6GB: initrd.img.old
  85.7GB: vmlinuz
  85.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  2a 55 8b 53 8b 57 50 76  10 ec aa 57 30 9a 2a fe  |*U.S.WPv...W0.*.|
00000010  c1 e2 32 1f f7 dc b0 cc  82 14 09 f4 fe f7 02 85  |..2.............|
00000020  46 0b 13 e8 08 f6 e5 cc  bd 16 e4 50 68 4a 72 8e  |F..........PhJr.|
00000030  92 04 5d 9c e0 93 90 b3  6b e4 e7 d1 5c 5a fb b8  |..].....k...\Z..|
00000040  0b ce e0 d2 90 db 4e c2  db 8a 4c 30 6b 80 95 d5  |......N...L0k...|
00000050  67 a6 6c fc b3 1a 17 c0  c0 ae 40 60 78 a4 87 49  |g.l.......@`x..I|
00000060  54 09 b6 af cd 5c 0b 52  66 2f 4d 1b 19 70 84 53  |T....\.Rf/M..p.S|
00000070  bf 6f bc fe 99 a9 fe 79  89 1b 0a fb ad f7 fb 6f  |.o.....y.......o|
00000080  e4 bb b4 bb a4 ff 3d 1a  9a c4 0f 18 ac 23 3c 6f  |......=......#<o|
00000090  28 3a 87 51 24 83 17 4e  1a c7 44 88 da cf 5b 09  |(:.Q$..N..D...[.|
000000a0  60 55 b6 18 e8 a1 cb 01  b1 96 a3 1f f9 eb 26 2c  |`U............&,|
000000b0  05 93 3f a5 7f 96 71 9f  98 be ed 04 09 0a 47 b0  |..?...q.......G.|
000000c0  b2 c5 78 3c 7c 05 33 18  fe c7 f7 e0 3c 61 3e 57  |..x<|.3.....<a>W|
000000d0  02 1c a2 5f 76 79 31 dd  9c 33 a1 06 d0 98 7e d1  |..._vy1..3....~.|
000000e0  0d 44 c3 c3 d3 0c 35 ea  6e 0e 3a 27 cd 7a 78 14  |.D....5.n.:'.zx.|
000000f0  61 40 4d 29 b8 f5 8a 0c  0d cc ba 8a 16 ed 82 9f  |a@M)............|
00000100  1f 50 29 08 a0 f6 ff 0a  2f 88 8f db 9d b0 cd 5b  |.P)...../......[|
00000110  24 98 63 88 39 12 62 33  5a f4 4e 63 5a a5 45 f2  |$.c.9.b3Z.NcZ.E.|
00000120  db 7f c4 0c 13 e2 cb a3  49 78 c0 d6 6e a3 ce 18  |........Ix..n...|
00000130  56 5c 51 24 49 a9 75 5f  e5 b1 61 0a c5 53 4b 78  |V\Q$I.u_..a..SKx|
00000140  d1 3e 6b 27 f9 72 0d de  9c 2b a2 ed 7a 88 92 aa  |.>k'.r...+..z...|
00000150  eb 1f b6 55 93 00 72 d5  4b 6a dc bc 51 e4 62 2d  |...U..r.Kj..Q.b-|
00000160  36 15 79 30 9a b5 42 7f  86 3b eb 0b b7 6c ae ae  |6.y0..B..;...l..|
00000170  fb b8 64 c3 b9 9f 9a 81  72 33 9f 84 a4 fa 96 aa  |..d.....r3......|
00000180  f0 9d 46 59 f6 d6 3a b3  8b 15 34 f3 5c 63 19 81  |..FY..:...4.\c..|
00000190  fa 40 38 ff 79 b1 04 a8  a8 1f 03 b2 44 a6 2d 57  |.@8.y.......D.-W|
000001a0  3a c4 ce a4 ad f6 55 28  80 3a bd 25 d4 3f 8d 2e  |:.....U(.:.%.?..|
000001b0  01 d1 50 99 fa d4 e1 ba  54 68 b2 f5 79 7f 47 c4  |..P.....Th..y.G.|
000001c0  c8 3f 5a dd 51 2f 1d 84  18 a1 89 7c 9b 22 82 95  |.?Z.Q/.....|."..|
000001d0  a1 7d 26 99 f6 3c 0e 01  58 2c 98 ab e3 1f db 50  |.}&..<..X,.....P|
000001e0  ec 89 7f 5e 53 e8 07 62  56 8e 6c c3 bb e8 c1 e2  |...^S..bV.l.....|
000001f0  ba 52 4a fa e1 b6 9d 0b  0c 36 26 3d 32 53 dc 32  |.RJ......6&=2S.2|
00000200
```

---

### Post by Rubi1200 on 2011-04-24
Thanks for posting the results.

Well, you seem to have a mix of 2 different versions of GRUB. Let me do some checking and I will get back to you with a solution.

Thanks.

---

### Post by Rubi1200 on 2011-04-24
Hi,
okay, after consulting with another forum member, drs305, who really knows his stuff about GRUB, this is what I/we suggest you try:

First off, do you have a LiveCD for 9.04 (which is what you have installed)?

You could try and do a chroot from that or perhaps a 9.10 CD, but you may need to configure the sources.list to do so.

So, the chroot method can be found here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

when you get to the part about removing packages, you need to purge/reinstall grub-common and grub (not grub-pc).

Again, the version of CD is important.

From a 9.10 CD (but only within the next couple of days since it's about  EOL) or open the CD's /etc/apt/sources.list and change "main jaunty" to  "main karmic". 

From a jaunty CD you could also change to the archived jaunty repositories by changing the addresses in sources.list to:
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

e.g.
> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe 			 		

If this seems too much, you might want to consider backing up the data using the LiveCD and then do a fresh install of a more recent version such as 10.04 which is an LTS release. The other advantage being that versions from 9.10 onwards all use GRUB2.

---

### Post by snarlster on 2011-04-26
Hi again Rubi1200

Thanks for that solution, I will this tonight when I get home from work. Im still curious about my versions of the solutions that I asked in my first post since this seems a little more heavy duty than my original ideas.

1. Is it possible to upgrade Ubuntu from a live CD (not a fresh install) and have my GRUB2 fixed that way?

2. Is it possible to upgrade my legacy GRUB to GRUB2?

and one more idea, if I boot from a Live CD (I have 9.04 as well as 10.10 on USB), could I just delete all files within the BOOT/Grub directory and then do a fresh install of my Grub?

Thanks again for your help, I'll let you know how the chroot attempt goes when I try it.

---

### Post by Rubi1200 on 2011-04-26
Yes, you could upgrade to GRUB2:
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading) to GRUB 2

You might want to try this first before the other suggestions. But at least you have other information available if needs be.

As to the other questions, no and probably not a good idea.

---

### Post by snarlster on 2011-04-26
Hey, so my problem was solved by simply booting off a 9.04 live cd (usb actually) and setting up Legacy grub. Left the Grub2 stuff right the way it was. Simply followed the instructions here:

[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)

Which basically just sets up the old legacy grub, I couldnt do that from the 10.10 Live CD... have to run the "sudo grub" from a 9.04 CD.

Sorry I didnt go ahead and try the Chroot idea, it just seemed a little overdoing a simple grub problem - then I got some assistance on Efnet... I should have just tried booting from 9.04 right away!

Anyway, problem Solved! Thanks for your help :)

---

### Post by Rubi1200 on 2011-04-27
Excellent! I am pleased you got this sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

