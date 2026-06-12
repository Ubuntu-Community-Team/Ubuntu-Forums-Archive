---
title: "grub2 vs grub dual hard drive"
date: 2010-07-21
forum: General Help
---

### Post by vbdanl on 2010-07-21
hi.  i am trying to get an old pc up to date with the latest ubuntu 10.04. the pc previously had ubuntu 8.04 on hd2 and puppy linux on hd1.
this is an old pc i keep around for family/friends to use if theirs goes belly up, and they want to use the internet.  i recently installed ubuntu 10.04 on a 9.1GB hd. no problems with install, but for some reason when i try to do a reboot, it just hangs and never displays the grub menu.  if i do a cold boot, or unplug the power cord and plug it back in, it will boot fine. otherwise, i get a HD failure message (after a minute or two) and never see the grub menu.  this is with just the one drive installed and all it has is ubuntu 10.04 and its default grub2.
when the pc was working fine, it had 2 hd's in it, and puppy on hd1 and ubuntu 8.04 on hd2.  obviously, i was using the older grub.
i installed puppy linux on the smaller 2.4GB hd with old grub, and it has no problems rebooting (unlike ubuntu did because it would just hang on reboot).
puppy boots fine everytime.  now i added ubuntu 9.1GB drive as slave, and added entries in puppy menu.lst file to boot ubuntu.
when i try to boot ubuntu, i get bad file or dir type error 2 message, or error 15 file not found.  i tried various boot entries, including the standard UUID= entry and even tried using chainloader.
my first question is should i be able to boot ubuntu on hd2 that was built using grub2 via a primary drive that uses the legacy grub ?
i tried a 3rd hd that had older linux distros on it.  it acts the same as the ubuntu hd.. it gave the HD failure message and would not boot, but if i unplug the power cord, plug it back in, it boots fine.
i know this is really weird.. and i know i should probably take this old pc out to the dump site and use it for target practice..
i guess i would like to know if anyone has seen anything like this and might know what would cause this behavior and what i can do to resolve it..  thanks for listening, and sorry for the looong post..

---

### Post by oldfred on 2010-07-21
Grub legacy is not grub legacy. It has not been maintained for years and each distribution made minor fixes to work with their distribution.

Ubuntu updated its version of grub legacy to see ext4 partitions with 9.04. Others may or may not have done the same when they add ext4 support.

If you have Ubuntu grub2 in the MBR you should be able to chainload from old grub to the grub 2 in the MBR of the second drive.

This is my entry:

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

Yours may be hd1.

---

### Post by vbdanl on 2010-07-21
> **oldfred said:**
> Grub legacy is not grub legacy. It has not been maintained for years and each distribution made minor fixes to work with their distribution.

Ubuntu updated its version of grub legacy to see ext4 partitions with 9.04. Others may or may not have done the same when they add ext4 support.

If you have Ubuntu grub2 in the MBR you should be able to chainload from old grub to the grub 2 in the MBR of the second drive.

This is my entry:

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

Yours may be hd1.

I will try that tonight.  I actually have a couple of chainloader entries I had tried, but maybe they aren't quite right.  i was wondering why fdisk shows partitions as type 83 even when they are formatted as ext4 ?  doesn't the 83 generally mean they were formatted as ext3 partitions ?

---

### Post by oldfred on 2010-07-21
Partition ext2, ext3, & ext4 all all the same. Ext3 & 4 add journaling and a few underlying changes but are still ext2 based.

---

### Post by vbdanl on 2010-07-22
> **oldfred said:**
> Partition ext2, ext3, & ext4 all all the same. Ext3 & 4 add journaling and a few underlying changes but are still ext2 based.
thanks for the replies oldfred.
making some progress, but still having some problems..
i used your advice and it booted into ubuntu, but when i rebooted, it goes back to the black screen and hangs.  i don't know but i am wondering if the pc is confused with having grub on both drives ?
here are the different options i tried, and the results (from the menu.lst file on the primary drive (puppy linux):
# Linux bootable partition config begins
  title Pup420 (on /dev/sda1)
  rootnoverify (hd0,0)
  kernel /puppy420/vmlinuz pmedia=atahd psubdir=puppy420
  initrd /puppy420/initrd.gz
** the puppy option boots fine as long as the grub menu appears

# Linux bootable partition config continues
  title Ubuntu 10.04 using uuid and 32.23 files
  root (hd1,0)
  kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=6c4aada9-1c61-4bb9-bcea-83d5bc570f7a ro splash
  initrd /boot/initrd.img-2.6.32-23-generic
  quiet
** the above option gives "Error 2: Bad file or Dir Type"
 
# Linux bootable partition config continues
  title Ubuntu 10.04 opt 3 using /dev/sdb1 and vmlinuz
  root (hd1,0)
  kernel /vmlinuz root=/dev/sdb1 ro splash
  initrd /initrd.img
  quiet
** the above option gives "Error 2: Bad file or Dir Type"
 
# Linux bootable partition config continues
  title Ubuntu using chainloader hd1
  root (hd1)
  chainloader +1
** the above option (from oldfred) works once, but if i reboot, it hangs and the only way out is to pull the power cord
 
# Linux bootable partition config continues
  title Ubuntu using chainloader hd1,0
  root (hd1,0)
  chainloader +1
** the above fails "Error 13 Invalid or unsupported executable format"
# Linux bootable partition config continues
  title Ubuntu using chainloader with mapping
  root (hd1,0)
  savedefault
  makeactive
  map		(hd0) (hd1)
  map		(hd1) (hd0)
  chainloader +1
** above fails with "Error 15: File not found"

I think it flashed an error about unknown filesystem but went ahead and booted into ubuntu when i selected oldfred's option.  it flashed the error too fast to read it all.

when it hangs, the pc shows the 32mg ram message, then the Mainboard bios screen, then just a black screen with flashing cursor for about a minute, then it shows the disk mapping and pci device listing and shows boot from cd.  stays there for about a minute, then gives disk boot failure, insert system disk error message.
it doesn't matter if i press ctrl-alt-del, the reset button, or even the power button, all result in going back to the same sequence as just described.  only thing that seems to work is pulling the power cord. when i replug it in, it immediately starts booting.  when it boots successfully, i don't see the minute pause and black screen.. i still see the 32mb ram, mainboard bios, then a quick flash of disk mapping and pci listing and right into the grub menu within 2 or 3 seconds.
any ideas?

---

### Post by oldfred on 2010-07-22
Post this as it shows all the installs. What is the RAM that you have in this system?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by vbdanl on 2010-07-24
> **oldfred said:**
> Post this as it shows all the installs. What is the RAM that you have in this system?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2559 MB, 2559836160 bytes
255 heads, 63 sectors/track, 311 cylinders, total 4999680 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,658,849     4,658,787  83 Linux
/dev/sda2           4,658,911     4,996,214       337,304   5 Extended
/dev/sda5           4,658,913     4,996,214       337,302  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 9115 MB, 9115361280 bytes
255 heads, 63 sectors/track, 1108 cylinders, total 17803440 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     8,984,575     8,982,528  83 Linux
/dev/sdb2           8,986,622    17,803,263     8,816,642   5 Extended
/dev/sdb5           8,986,624    15,849,471     6,862,848  83 Linux
/dev/sdb6          15,851,520    17,803,263     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop1       99768970-2d37-4249-97d5-0513306838f5   ext2                                     
/dev/sda1        73579a8f-f9a8-49a8-b3e8-31fdd7d44dd6   ext3                                     
/dev/sda5        42747b26-4bac-4651-ab5a-7722d428aadd   swap                                     
/dev/sdb1        6c4aada9-1c61-4bb9-bcea-83d5bc570f7a   ext3                                     
/dev/sdb5        0de2f183-822e-4931-9349-9d095e6e63d6   ext3                                     
/dev/sdb6        a14d0524-317a-4c7d-98b4-05ea3c48dc5f   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
unionfs          /                        aufs       (rw,si=cf9c1942,xino=/initrd/pup_rw/.aufs.xino,diropq=w,dirs=/initrd/pup_rw=rw:/initrd/pup_ro2=ro)
/dev/sda1        /initrd/mnt/dev_save     ext3       (rw,noatime,errors=continue,data=ordered)
/dev/loop1       /initrd/pup_rw           ext2       (rw,noatime,errors=continue)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Mon Jul 19 03:19:49 2010
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.6841'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.6841 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section
# Linux bootable partition config begins
  title Pup420 (on /dev/sda1)
  rootnoverify (hd0,0)
  kernel /puppy420/vmlinuz pmedia=atahd psubdir=puppy420
  initrd /puppy420/initrd.gz
  
# Linux bootable partition config continues
  title Ubuntu 10.04 via chainloader
  root (hd1)
  chainloader +1
  
# Linux bootable partition config continues
  title Ubuntu 10.04 uuid and 2.6.32-23 DoesNotWork
  root (hd1,0)
  kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=6c4aada9-1c61-4bb9-bcea-83d5bc570f7a ro splash
  initrd /boot/initrd.img-2.6.32-23-generic
  quiet
  
# Linux bootable partition config continues
  title Ubuntu 10.04 /dev/sdb1 vmlinuz DoesNotWork
  root (hd1,0)
  kernel /vmlinuz root=/dev/sdb1 ro splash
  initrd /initrd.img
  quiet
  
# Linux bootable partition config continues
  title Ubuntu using chainloader hd1,0 DoesNotWork
  root (hd1,0)
  chainloader +1
  
# Linux bootable partition config continues
  title Ubuntu using chainloader mapping DoesNotWork
  root (hd1,0)
  savedefault
  makeactive
  map		(hd0) (hd1)
  map		(hd1) (hd0)
  chainloader +1
  
# Linux bootable partition config ends
title Install GRUB to Linux partition (on /dev/sda1)
root (hd0,0)
setup (hd0,0)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)

================================ sda1/menu.lst: ================================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
default		0

## timeout sec
timeout		10

## hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
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
# kopt=root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

#title		Ubuntu 8.04, kernel 2.6.24-27-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro splash
#initrd		/boot/initrd.img-2.6.24-27-generic

#title		Ubuntu 8.04, kernel 2.6.24-26-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro splash
#initrd		/boot/initrd.img-2.6.24-26-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-24-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-24-generic
#quiet

#title		Ubuntu 8.04.1, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Puppy Linux 4.0 frugal (on /dev/sda1)
rootnoverify	(hd0,0)
kernel		/vmlinuz pmedia=idehd 
initrd		/initrd.gz


=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .0GB: initrd.gz
    .7GB: menu.lst
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  56 76 0c 83 0b cb 85 f1  72 f0 58 e1 9e fb 51 9d  |Vv...Ë.ñrðXá.ûQ.|
00000010  77 f1 ef 97 6a ab 81 d1  fb 0a ba a5 56 1c 26 27  |wñï.j«.Ñû.º¥V.&'|
00000020  de 5c 57 72 db e7 9d 88  69 cc b1 2f e1 ce 97 ea  |Þ\WrÛç..iÌ±/áÎ.ê|
00000030  73 56 15 fc 6b d9 12 c6  57 df e0 bb a5 e4 85 29  |sV.ükÙ.ÆWßà»¥ä.)|
00000040  94 db e6 99 73 56 10 9f  4b 22 ab 17 7d 6a 1b 6c  |.Ûæ.sV..K"«.}j.l|
00000050  3c a8 be f8 2d 62 61 35  76 d5 12 56 1f d3 77 a7  |<¨¾ø-ba5vÕ.V.Ów§|
00000060  16 36 77 33 05 59 e7 75  f7 a6 2b 1e bf f7 ac c1  |.6w3.Yçu÷¦+.¿÷¬Á|
00000070  16 31 3e 3d 23 de b7 d1  d8 31 0e ed 7e 60 e2 f8  |.1>=#Þ·ÑØ1.í~`âø|
00000080  2e b1 f3 8b 19 8b a6 c2  de 8b ee 9e 25 fc 9a c1  |.±ó...¦ÂÞ.î.%ü.Á|
00000090  c4 d8 45 f7 6e 77 6c 8b  eb 73 8f f0 66 f8 f5 26  |ÄØE÷nwl.ës.ðføõ&|
000000a0  6d 76 e6 7f 2d b1 f2 86  27 ef 3f 75 73 56 6c ba  |mvæ.-±ò.'ï?usVlº|
000000b0  87 4f 9a e3 c7 6c d2 37  37 7d d6 64 b0 58 0e 7f  |.O.ãÇlÒ77}Öd°X..|
000000c0  7a 68 3c 33 10 ec be 53  1c 45 c0 c7 69 91 99 96  |zh<3.ì¾S.EÀÇi...|
000000d0  d8 3e f8 ff 11 f6 dd 81  31 65 ef df cf cc 24 93  |Ø>øÿ.öÝ.1eïßÏÌ$.|
000000e0  99 c9 04 ab 77 69 a2 84  68 41 48 10 44 4b 22 5a  |.É.«wi¢.hAH.DK"Z|
000000f0  44 27 22 a2 47 44 74 6b  75 d1 ad ce ea 8b c5 ea  |D'"¢GDtkuÑ*Îê.Åê|
00000100  ab af b6 16 ab 97 5d bd  f7 1a 75 f5 fa 7e ce dc  |«¯¶.«.]½÷.uõú~ÎÜ|
00000110  e7 9e 7b 67 be f6 f7 fe  41 e6 dc 72 ce d3 db 29  |ç.{g¾ö÷þAæÜrÎÓÛ)|
00000120  57 c7 93 37 80 e5 07 5c  ab 0d fa ad 43 1f 93 01  |WÇ.7.å.\«.ú*C...|
00000130  e7 31 35 ce 01 dc 0f a1  cb d3 f1 de 11 f0 be 24  |ç15Î.Ü.¡ËÓñÞ.ð¾$|
00000140  60 cb 8b fe 97 00 c7 da  68 d7 87 cc 9a 00 63 21  |`Ë.þ..ÇÚh×.Ì..c!|
00000150  96 95 58 c0 53 8b e5 28  27 e7 aa 66 5c db a7 b3  |..XÀS.å('çªf\Û§³|
00000160  85 39 85 8e eb 68 ba 81  ed de 1e f4 95 8b f9 5c  |.9..ëhº.íÞ.ô..ù\|
00000170  95 f9 74 05 f4 c9 01 b8  5e b8 f0 64 aa 88 5f f0  |.ùt.ôÉ.¸^¸ðdª._ð|
00000180  bc 85 af 07 80 ce dd 80  73 56 d8 90 b9 e2 7b 90  |¼.¯..ÎÝ.sVØ.¹â{.|
00000190  b0 07 c5 d4 b3 6b 74 39  cc 7b 9d 7c 6d 83 9c ff  |°.ÅÔ³kt9Ì{.|m..ÿ|
000001a0  a1 f3 e1 1f c0 db ee 1c  e7 f9 00 3f 33 64 e6 24  |¡óá.ÀÛî.çù.?3dæ$|
000001b0  ae 4d 01 7e b9 75 b6 79  2e cb 9e 95 f3 c5 00 01  |®M.~¹u¶y.Ë..óÅ..|
000001c0  41 22 82 fe 7f 36 02 00  00 00 96 25 05 00 00 00  |A".þ.6.....%....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............Uª|
00000200

Unknown BootLoader  on sdb2

00000000  10 63 c5 24 48 8c e1 06  27 d2 12 42 00 43 49 11  |.cÅ$H.á.'Ò.B.CI.|
00000010  9b 4c f2 44 c2 46 87 cd  50 1c 93 e4 8a 96 a9 93  |.LòDÂF.ÍP..ä..©.|
00000020  14 0e 29 44 c1 81 e4 d2  a9 de ab ba ce 22 7a 66  |..)DÁ.äÒ©Þ«ºÎ"zf|
00000030  60 ff fb b2 00 2a 80 04  5f 49 4f 0f 6e 20 00 8b  |`ÿû².*.._IO.n ..|
00000040  09 2a 00 ed bc 00 11 65  2d 40 2d 3d 6b d2 23 a5  |.*.í¼..e-@-=kÒ#¥|
00000050  e8 85 a7 a5 78 66 44 50  4d cb c7 8a 42 95 30 2c  |è.§¥xfDPMËÇ.B.0,|
00000060  b3 9b 24 99 a9 f4 da 62  6b 5d 94 ec f7 75 3b eb  |³.$.©ôÚbk].ì÷u;ë|
00000070  a2 71 36 51 a9 c9 c2 fa  32 a2 29 55 d0 3e 92 6a  |¢q6Q©ÉÂú2¢)UÐ>.j|
00000080  44 e1 a1 c3 85 00 16 68  4c a3 db 1c 2a 40 70 f1  |Dá¡Ã...hL£Û.*@pñ|
00000090  a6 28 66 70 e2 82 10 25  8a 38 14 e7 bc cc 46 41  |¦(fpâ..%.8.ç¼ÌFA|
000000a0  bd 4f 49 20 87 7e 94 dc  26 03 94 f8 53 9c ce a0  |½OI .~.Ü&..øS.Î |
000000b0  2b a3 d9 28 a4 83 d9 f7  35 9b 37 12 f1 74 9d 8e  |+£Ù(¤.Ù÷5.7.ñt..|
000000c0  e1 ac db 4d da 6c 85 4f  88 13 6e da c6 f7 f1 8d  |á¬ÛMÚl.O..nÚÆ÷ñ.|
000000d0  c7 bc 90 62 76 37 90 cf  18 0f e3 b1 3a 5d 0c 57  |Ç¼.bv7.Ï..ã±:].W|
000000e0  8b f3 6d f4 68 6e 2e e1  d3 4f 62 fc ef 58 de b7  |.ómôhn.áÓObüïXÞ·|
000000f0  4d ee d7 de b5 9f 58 11  e2 59 95 ab c8 ce f7 4a  |Mî×Þµ.X.âY.«ÈÎ÷J|
00000100  8a c6 f8 c6 37 48 f6 be  22 c9 10 e1 c2 80 0b 34  |.ÆøÆ7Hö¾"É.áÂ..4|
00000110  26 50 d3 4c 8e fb 10 01  23 11 d3 ec 67 67 9c 51  |&PÓL.û..#.Óìgg.Q|
00000120  01 80 51 b4 5a 48 14 69  73 8c 88 b6 44 ab 21 8e  |..Q´ZH.is..¶D«!.|
00000130  71 2e 8c 1f 08 6a 08 1d  61 5a 26 00 5c 1c e3 1c  |q....j..aZ&.\.ã.|
00000140  0b 87 01 ce 79 b6 b9 aa  92 49 f9 ab 48 ec 10 e8  |...Îy¶¹ª.Iù«Hì.è|
00000150  c9 54 e3 23 0f a2 7d 5c  84 3f 6c 8a 68 0d e3 70  |ÉTã#.¢}\.?l.h.ãp|
00000160  8e 03 60 38 10 04 f2 41  04 1e 07 60 78 2c 7b 1e  |..`8..òA...`x,{.|
00000170  fd 05 d0 3e 3f 28 a3 d0  41 e6 45 c7 78 39 26 ed  |ý.Ð>?(£ÐAæEÇx9&í|
00000180  98 de f5 1b 54 ce ad cc  74 57 7f d4 f1 6c 59 04  |.Þõ.TÎ*ÌtW.ÔñlY.|
00000190  ed ae 7b 9b 15 db 6f fa  ed eb 5c b5 cb 95 18 30  |í®{..Ûoúíë\µË..0|
000001a0  df 91 00 96 f1 c3 c4 62  47 89 22 6e 0b 06 18 44  |ß...ñÃÄbG."n...D|
000001b0  ba ea 72 83 ef 43 66 b9  de 3c ce 42 e0 a9 00 63  |ºêr.ïCf¹Þ<ÎBà©.c|
000001c0  b5 2f 83 94 fa da 02 00  00 00 00 b8 68 00 00 94  |µ/..úÚ.....¸h...|
000001d0  fb da 05 fe ff ff 02 b8  68 00 00 d0 1d 00 00 00  |ûÚ.þÿÿ.¸h..Ð....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............Uª|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 


```

---

### Post by oldfred on 2010-07-24
You seem to have something wrong with sdb.

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

You can try these suggestions:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

### Post by vbdanl on 2010-07-26
> **oldfred said:**
> You seem to have something wrong with sdb.

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

You can try these suggestions:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

i tried the instructions from the first link (using PartMagic), but the fsck command did not return errors.  when i ran testdisk the only thing that looked wrong was when i try to list the files on sdb1, it doesn't show any and says it might be corrupt.
a little frustrated, i decided to try reformat, partition, and install ub again.  basically same problem, except maybe worse.  now i have to unplug between every reboot.  i let ub put its grub2 on sda, which of course replaced the puppy grub.  i added puppy to the 40* file and rebuilt the menu and was able to boot into puppy. i can boot into ub also, just can't reboot into anything without first unplugging the pc.  fdisk now does not show any bootable partition on sdb, which i think is correct, since grub2 was installed on sda.

---

### Post by oldfred on 2010-07-26
Try this on sdb1 and maybe on the other sdb partitions:

Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.


From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by vbdanl on 2010-07-26
> **oldfred said:**
> Try this on sdb1 and maybe on the other sdb partitions:

Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.


From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

I will try it tonight. i did run a couple variations of the e2fsck command last night.  tried to recover the superblock from several backup copies, but none seemed to work.  i can't remember what the other parms i used were, but i don't think i ran it with -CO -p -f -v.. i think after all the unsuccessful attempts is when i decided maybe just reformatting and starting over might fix the problem..  there isn't anything on either drive that needs saving, so i am open to any type of formatting and starting over type solutions.  since the sda drive is only 2.5GB and the sdb is 9.1, i figured it made sense to have puppy on the 2.5 and ubuntu on the larger.  i think u asked earlier about the ram.. this pc has 512mb ram.  not sure if it matters, but i am sure these drives had w95 or w98 on them originally, and i reformatted them to use as linux.  not sure if i did something wrong along the way or not, or if thats a possibility..

---

### Post by oldfred on 2010-07-26
If drive is old that may be that it is just old.

You may do better with a lighter weight install.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

---

### Post by vbdanl on 2010-07-26
> **oldfred said:**
> If drive is old that may be that it is just old.

You may do better with a lighter weight install.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

probably right.  i was wondering if i should have installed ubuntu grub2 on sdb or sda ?  this time i installed it on sda, because that is where it wanted to install it.  i could unplug sda and make sdb be the only drive in system (now sda) and install it there, then repin it as slave, and go that route, in which case both drives show a bootable partition, and both drives should have the ability to be installed as primary and work alone.  is that the "norm" on a dual boot system?  i would really like to understand why unplugging the power cord allows the system to boot, and what is it doing when it fails to boot (the minute or so pause before it displays the disk map and tables)..

---

### Post by oldfred on 2010-07-26
Not quite sure what you mean.

Older computers only booted from primary master (hardware jumpers) as that is all BIOS would work with. New computers with SATA do the selection in BIOS (software), mine still calls it primary master but in BIOS I can select any SATA drive as the boot drive.

You have grub legacy (0.97) in sda and grub2 in sdb.

---

### Post by vbdanl on 2010-07-26
> **oldfred said:**
> Not quite sure what you mean.

Older computers only booted from primary master (hardware jumpers) as that is all BIOS would work with. New computers with SATA do the selection in BIOS (software), mine still calls it primary master but in BIOS I can select any SATA drive as the boot drive.

You have grub legacy (0.97) in sda and grub2 in sdb.
not sure about grub legacy in sda.. i think it used to be until i reinstalled  ubuntu the last time.  here is the output from the bootinfo script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2559 MB, 2559836160 bytes
255 heads, 63 sectors/track, 311 cylinders, total 4999680 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,658,849     4,658,787  83 Linux
/dev/sda2           4,658,911     4,996,214       337,304   5 Extended
/dev/sda5           4,658,913     4,996,214       337,302  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 9115 MB, 9115361280 bytes
255 heads, 63 sectors/track, 1108 cylinders, total 17803440 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048     9,606,869     9,604,822  83 Linux
/dev/sdb2           9,606,870    17,419,369     7,812,500  83 Linux
/dev/sdb3          17,420,286    17,801,215       380,930   5 Extended
/dev/sdb5          17,420,288    17,801,215       380,928  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop1       99768970-2d37-4249-97d5-0513306838f5   ext2                                     
/dev/sda1        73579a8f-f9a8-49a8-b3e8-31fdd7d44dd6   ext3                                     
/dev/sda5        42747b26-4bac-4651-ab5a-7722d428aadd   swap                                     
/dev/sdb1        acbfdce0-3d69-4f49-be70-5a89567db92b   ext3                                     
/dev/sdb2        cf53478e-2450-4148-8edd-733b941c9580   ext3                                     
/dev/sdb5        e1f2d0b4-0328-457a-beb4-25d97654c3c1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
unionfs          /                        aufs       (rw,si=a499b5c9,xino=/initrd/pup_rw/.aufs.xino,diropq=w,dirs=/initrd/pup_rw=rw:/initrd/pup_ro2=ro)
/dev/sda1        /initrd/mnt/dev_save     ext3       (rw,noatime,errors=continue,data=ordered)
/dev/loop1       /initrd/pup_rw           ext2       (rw,noatime,errors=continue)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Mon Jul 19 03:19:49 2010
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.6841'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.6841 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section
# Linux bootable partition config begins
  title Pup420 (on /dev/sda1)
  rootnoverify (hd0,0)
  kernel /puppy420/vmlinuz pmedia=atahd psubdir=puppy420
  initrd /puppy420/initrd.gz
  
# Linux bootable partition config continues
  title Ubuntu 10.04 via chainloader
  root (hd1)
  chainloader +1
  
# Linux bootable partition config continues
  title Ubuntu 10.04 uuid and 2.6.32-23 DoesNotWork
  root (hd1,0)
  kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=6c4aada9-1c61-4bb9-bcea-83d5bc570f7a ro splash
  initrd /boot/initrd.img-2.6.32-23-generic
  quiet
  
# Linux bootable partition config ends
title Install GRUB to Linux partition (on /dev/sda1)
root (hd0,0)
setup (hd0,0)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)

================================ sda1/menu.lst: ================================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
default		0

## timeout sec
timeout		10

## hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
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
# kopt=root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

#title		Ubuntu 8.04, kernel 2.6.24-27-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro splash
#initrd		/boot/initrd.img-2.6.24-27-generic

#title		Ubuntu 8.04, kernel 2.6.24-26-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro splash
#initrd		/boot/initrd.img-2.6.24-26-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-24-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=70c9b61e-e093-49bd-9178-54d852f3604a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-24-generic
#quiet

#title		Ubuntu 8.04.1, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Puppy Linux 4.0 frugal (on /dev/sda1)
rootnoverify	(hd0,0)
kernel		/vmlinuz pmedia=idehd 
initrd		/initrd.gz


=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .0GB: initrd.gz
    .7GB: menu.lst
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  56 76 0c 83 0b cb 85 f1  72 f0 58 e1 9e fb 51 9d  |Vv...Ë.ñrðXá.ûQ.|
00000010  77 f1 ef 97 6a ab 81 d1  fb 0a ba a5 56 1c 26 27  |wñï.j«.Ñû.º¥V.&'|
00000020  de 5c 57 72 db e7 9d 88  69 cc b1 2f e1 ce 97 ea  |Þ\WrÛç..iÌ±/áÎ.ê|
00000030  73 56 15 fc 6b d9 12 c6  57 df e0 bb a5 e4 85 29  |sV.ükÙ.ÆWßà»¥ä.)|
00000040  94 db e6 99 73 56 10 9f  4b 22 ab 17 7d 6a 1b 6c  |.Ûæ.sV..K"«.}j.l|
00000050  3c a8 be f8 2d 62 61 35  76 d5 12 56 1f d3 77 a7  |<¨¾ø-ba5vÕ.V.Ów§|
00000060  16 36 77 33 05 59 e7 75  f7 a6 2b 1e bf f7 ac c1  |.6w3.Yçu÷¦+.¿÷¬Á|
00000070  16 31 3e 3d 23 de b7 d1  d8 31 0e ed 7e 60 e2 f8  |.1>=#Þ·ÑØ1.í~`âø|
00000080  2e b1 f3 8b 19 8b a6 c2  de 8b ee 9e 25 fc 9a c1  |.±ó...¦ÂÞ.î.%ü.Á|
00000090  c4 d8 45 f7 6e 77 6c 8b  eb 73 8f f0 66 f8 f5 26  |ÄØE÷nwl.ës.ðføõ&|
000000a0  6d 76 e6 7f 2d b1 f2 86  27 ef 3f 75 73 56 6c ba  |mvæ.-±ò.'ï?usVlº|
000000b0  87 4f 9a e3 c7 6c d2 37  37 7d d6 64 b0 58 0e 7f  |.O.ãÇlÒ77}Öd°X..|
000000c0  7a 68 3c 33 10 ec be 53  1c 45 c0 c7 69 91 99 96  |zh<3.ì¾S.EÀÇi...|
000000d0  d8 3e f8 ff 11 f6 dd 81  31 65 ef df cf cc 24 93  |Ø>øÿ.öÝ.1eïßÏÌ$.|
000000e0  99 c9 04 ab 77 69 a2 84  68 41 48 10 44 4b 22 5a  |.É.«wi¢.hAH.DK"Z|
000000f0  44 27 22 a2 47 44 74 6b  75 d1 ad ce ea 8b c5 ea  |D'"¢GDtkuÑ*Îê.Åê|
00000100  ab af b6 16 ab 97 5d bd  f7 1a 75 f5 fa 7e ce dc  |«¯¶.«.]½÷.uõú~ÎÜ|
00000110  e7 9e 7b 67 be f6 f7 fe  41 e6 dc 72 ce d3 db 29  |ç.{g¾ö÷þAæÜrÎÓÛ)|
00000120  57 c7 93 37 80 e5 07 5c  ab 0d fa ad 43 1f 93 01  |WÇ.7.å.\«.ú*C...|
00000130  e7 31 35 ce 01 dc 0f a1  cb d3 f1 de 11 f0 be 24  |ç15Î.Ü.¡ËÓñÞ.ð¾$|
00000140  60 cb 8b fe 97 00 c7 da  68 d7 87 cc 9a 00 63 21  |`Ë.þ..ÇÚh×.Ì..c!|
00000150  96 95 58 c0 53 8b e5 28  27 e7 aa 66 5c db a7 b3  |..XÀS.å('çªf\Û§³|
00000160  85 39 85 8e eb 68 ba 81  ed de 1e f4 95 8b f9 5c  |.9..ëhº.íÞ.ô..ù\|
00000170  95 f9 74 05 f4 c9 01 b8  5e b8 f0 64 aa 88 5f f0  |.ùt.ôÉ.¸^¸ðdª._ð|
00000180  bc 85 af 07 80 ce dd 80  73 56 d8 90 b9 e2 7b 90  |¼.¯..ÎÝ.sVØ.¹â{.|
00000190  b0 07 c5 d4 b3 6b 74 39  cc 7b 9d 7c 6d 83 9c ff  |°.ÅÔ³kt9Ì{.|m..ÿ|
000001a0  a1 f3 e1 1f c0 db ee 1c  e7 f9 00 3f 33 64 e6 24  |¡óá.ÀÛî.çù.?3dæ$|
000001b0  ae 4d 01 7e b9 75 b6 79  2e cb 9e 95 f3 c5 00 01  |®M.~¹u¶y.Ë..óÅ..|
000001c0  41 22 82 fe 7f 36 02 00  00 00 96 25 05 00 00 00  |A".þ.6.....%....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............Uª|
00000200

Unknown BootLoader  on sdb3

00000000  de ed 92 9d b1 4b 73 66  79 a0 0d 16 f1 9d 8d 29  |Þí..±Ksfy ..ñ..)|
00000010  ff 6e 20 5c fa c4 2c bf  86 05 2e ef 71 f4 b5 c6  |ÿn \úÄ,¿...ïqôµÆ|
00000020  84 5b 4d 91 f9 ac 4a 73  82 f7 36 f7 26 1e 8e c6  |.[M.ù¬Js.÷6÷&..Æ|
00000030  d8 a5 8f cd f2 eb c8 1d  6e 4e 45 ff 9e 88 4d 95  |Ø¥.ÍòëÈ.nNEÿ..M.|
00000040  42 cf 23 a5 b4 b1 d5 f1  3b ec 7f 57 ea f2 d2 a0  |BÏ#¥´±Õñ;ì.WêòÒ |
00000050  5a 1c b7 3f 33 6e 70 3b  c6 48 6f f1 a5 56 81 83  |Z.·?3np;ÆHoñ¥V..|
00000060  71 44 a3 16 6c 80 e9 c5  3b eb f1 b5 13 05 d5 6b  |qD£.l.éÅ;ëñµ..Õk|
00000070  cf f5 d0 4e ed 4c bd 55  03 18 be b5 e0 07 e3 be  |ÏõÐNíL½U..¾µà.ã¾|
00000080  31 d3 ce 02 2c ee 59 13  dc 8d ac 12 c5 0a 9b 0c  |1ÓÎ.,îY.Ü.¬.Å...|
00000090  fb f1 d2 46 5d a2 bf 88  03 18 0e 26 78 eb 57 2f  |ûñÒF]¢¿....&xëW/|
000000a0  95 a1 d5 bb 0b 82 93 69  24 88 62 1d 80 8c 37 ae  |.¡Õ»...i$.b...7®|
000000b0  77 5b e5 cb 62 6f 76 e3  98 28 5a ac 10 b9 47 6c  |w[åËbovã.(Z¬.¹Gl|
000000c0  f6 29 d6 8c eb f4 c5 76  c1 6e e7 ed e5 01 01 97  |ö)Ö.ëôÅvÁnçíå...|
000000d0  a8 86 e1 f5 99 b5 08 23  5d 56 85 eb b3 d0 09 82  |¨.áõ.µ.#]V.ë³Ð..|
000000e0  8a d4 c2 2b e0 7c c1 6e  ab 14 b0 c2 ae 0f 8e 31  |.ÔÂ+à|Án«.°Â®..1|
000000f0  02 23 80 91 bc 35 4c af  68 4f 39 82 c8 e3 3d 8d  |.#..¼5L¯hO9.Èã=.|
00000100  83 13 4a 7c 41 be d6 04  23 00 5b 58 38 84 1b b4  |..J|A¾Ö.#.[X8..´|
00000110  5c 72 0a 68 61 65 1e 71  d9 10 e2 88 0a f8 b9 37  |\r.hae.qÙ.â..ø¹7|
00000120  87 01 3f 17 0e c5 e0 e5  2f 4a be 0b 2f 03 ca af  |..?..Åàå/J¾./.Ê¯|
00000130  6e a2 37 ce c2 67 b1 be  0c 45 e2 37 c9 1b 71 19  |n¢7ÎÂg±¾.Eâ7É.q.|
00000140  f2 0e 50 3b 58 e2 52 1f  bf 5b 2c 06 d8 27 8b cf  |ò.P;XâR.¿[,.Ø'.Ï|
00000150  8c 3b 90 17 aa 8d 29 0a  32 c0 ca b5 8d 76 9c 99  |.;..ª.).2ÀÊµ.v..|
00000160  9b b8 2c e2 67 3a 40 fd  7a 0b c4 42 9c 13 99 61  |.¸,âg:@ýz.ÄB...a|
00000170  c1 ad d4 6f 0c 8c 9c c9  7c d2 39 9f 54 c0 4d 0d  |Á*Ôo...É|Ò9.TÀM.|
00000180  84 ca ca 0c 4b eb 27 be  44 b0 3b 01 cb eb 57 49  |.ÊÊ.Kë'¾D°;.ËëWI|
00000190  06 fd e5 c9 e0 89 e9 b2  01 6a 6c 9a 1a c3 4f 60  |.ýåÉà.é².jl..ÃO`|
000001a0  5a a2 a0 07 7b 0e bb 20  96 b9 d5 f6 6d 62 11 9a  |Z¢ .{.» .¹Õömb..|
000001b0  22 46 fc 94 02 f7 2b 91  79 32 63 3f ee 29 00 fe  |"Fü..÷+.y2c?î).þ|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 05 00 00 00  |ÿÿ.þÿÿ.....Ð....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............Uª|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 

```
i booted from part magic cd, and ran e2fsck -c -p -f -v /dev/sdb1
i tried to use the -c0 -option, but it complained about invalid option.
it ran for a few minutes, then displayed:
/dev/sdb1 updating bad block inode 138022/300736 files (0.1% non-contiguous) 593531/1200602 blocks
not sure what it is supposed to return, but i don't see the errors..
i then ran testdisk on sdb1.  only error i see is when i try to select "P" to list files, it just returns: no file found, filesystem seems damaged.

---

### Post by vbdanl on 2010-08-01
guess maybe its just a flaky hd.  reloaded ubuntu and grub on both drives (grub 2 on ub sdb drive and legacy grub via puppy on sda).  same results. it will boot puppy over and over without any problem, but if i boot into ubuntu on sdb, the next boot won't come up in anything (don't get grub menu). decided to just leave it for now, and keep the old pc as just a single drive puppy that will get on the internet just fine.  works as a spare.. thanks again for all your help.

---

