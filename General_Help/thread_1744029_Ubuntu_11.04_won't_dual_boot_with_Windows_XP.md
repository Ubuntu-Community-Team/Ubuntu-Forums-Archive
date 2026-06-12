---
title: "Ubuntu 11.04 won't dual boot with Windows XP"
date: 2011-04-30
forum: General Help
---

### Post by LukeSweet08 on 2011-04-30
Hey everybody. So I upgraded to Ubuntu 11.04 and now I can no longer find my Windows XP installation in GRUB. I have two hard drives in my computer. One is a 40 GB HD, is the master, and has just Ubuntu 11.04 on it. The second is a 10 GB HD, is the slave, and has Windows XP on it. Before the upgrade, it recognized both and I could boot between the two. Now, however, it doesn't recognize my XP hard drive anymore. I found someone with a similar problem, and everyone told them to put the results of boot_info_script.sh in here to help. I've also tried "sudo update-grub, but that still doesn't show my XP hard drive in GRUB. Please help! Here are my results from the boot_info_scripts.sh

 Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    75,094,015    75,091,968  83 Linux
/dev/sda2          75,096,062    78,163,967     3,067,906   5 Extended
/dev/sda5          75,096,064    78,163,967     3,067,904  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 10.3 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders, total 20044080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    20,016,989    20,016,927   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5d451889-a772-4b83-94cb-d20ca334571d   ext4       
/dev/sda5        8b06ed0f-c123-4fce-ac6a-6e53539f9b4b   swap       
/dev/sdb1        A2A0815AA0813637                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

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
# kopt=root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d451889-a772-4b83-94cb-d20ca334571d

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

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.35-28-generic
uuid        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 11.04, kernel 2.6.35-28-generic (recovery mode)
uuid        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro  single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Chainload into GRUB 2
root        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        5d451889-a772-4b83-94cb-d20ca334571d
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5d451889-a772-4b83-94cb-d20ca334571d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5d451889-a772-4b83-94cb-d20ca334571d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=8b06ed0f-c123-4fce-ac6a-6e53539f9b4b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.165870667 = 13.063004160   boot/grub/core.img                             1
   8.846332550 = 9.498677248    boot/grub/grub.cfg                             1
   8.858924866 = 9.512198144    boot/grub/menu.lst                             1
   1.079101562 = 1.158676480    boot/initrd.img-2.6.35-28-generic              2
   0.663288116 = 0.712200192    boot/initrd.img-2.6.38-8-generic               2
  12.267871857 = 13.172527104   boot/vmlinuz-2.6.35-28-generic                 1
   3.774719238 = 4.053073920    boot/vmlinuz-2.6.38-8-generic                  1
   0.663288116 = 0.712200192    initrd.img                                     2
   1.079101562 = 1.158676480    initrd.img.old                                 2
   3.774719238 = 4.053073920    vmlinuz                                        1
  12.267871857 = 13.172527104   vmlinuz.old                                    1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  6f 61 82 af bd 42 60 b5  45 0c 6e 33 f2 3b df e0  |oa...B`.E.n3.;..|
00000010  01 d1 da b6 55 4e 3a f4  cb 7d ef e5 20 2c 9a 54  |....UN:..}.. ,.T|
00000020  db f4 5c 9c ae 8d d9 49  91 44 49 90 e5 f4 7d a7  |..\....I.DI...}.|
00000030  22 be 83 5c 19 40 f5 5f  13 fb 31 72 81 c7 3e ec  |"..\.@._..1r..>.|
00000040  5e ca b6 91 e4 1c 25 57  9c 60 62 cb 9e b3 84 bf  |^.....%W.`b.....|
00000050  20 3c 71 44 2a be 34 da  9c 8b bd 73 8c 34 72 1d  | <qD*.4....s.4r.|
00000060  c7 8f ce 3a 34 e5 d7 c2  d2 e2 bc bf a8 ca d8 3d  |...:4..........=|
00000070  89 d4 af 08 93 df d5 14  d3 02 f5 92 a4 50 cc a7  |.............P..|
00000080  da fa 11 2f b2 0e 33 8e  45 45 77 ce 48 a3 29 eb  |.../..3.EEw.H.).|
00000090  34 d0 9c fe 38 27 14 e7  a4 33 6a 7b d0 3d c1 16  |4...8'...3j{.=..|
000000a0  df 8a 47 c4 e1 37 f8 99  91 6d bd 39 96 15 59 be  |..G..7...m.9..Y.|
000000b0  d5 ed bf f0 a0 67 9d f1  63 02 9c f7 a1 f0 c4 1f  |.....g..c.......|
000000c0  d5 06 d9 47 73 61 a7 c7  8c 8a dd 4f c6 b7 7e 3a  |...Gsa.....O..~:|
000000d0  9e 90 34 2c 59 10 99 34  bf 2f 6c b4 63 84 24 dc  |..4,Y..4./l.c.$.|
000000e0  88 8f e5 b7 be 26 56 d6  64 4c aa 30 76 c2 04 ea  |.....&V.dL.0v...|
000000f0  d6 0c 64 47 ba 18 05 76  0c 9c 98 1e af 4d bc fd  |..dG...v.....M..|
00000100  2f 81 8e 8f 51 57 c5 6e  4e 56 b3 c1 b3 c7 ea a7  |/...QW.nNV......|
00000110  0b cf b4 43 e3 1b 9c cd  18 2f 47 13 21 7a 3d 87  |...C...../G.!z=.|
00000120  6a c0 b0 cd 0e 0b 1b b6  84 94 1d bb 20 87 3d 4a  |j........... .=J|
00000130  e6 9a b3 b7 e8 dc 09 c3  72 6c 56 16 c3 ea 72 29  |........rlV...r)|
00000140  ee c4 52 e0 49 71 36 a7  85 fc 36 c4 0e 70 b1 ac  |..R.Iq6...6..p..|
00000150  c3 d3 6c ae c4 ca 03 a7  22 bd 82 a2 87 83 a9 27  |..l....."......'|
00000160  43 e7 62 43 8f 35 e3 22  5a 32 4c 12 5a b9 8d 52  |C.bC.5."Z2L.Z..R|
00000170  4d 21 8b e5 e3 1b 9c cd  18 2f 47 13 21 7a 3d 87  |M!......./G.!z=.|
00000180  6a c0 b0 cd e3 1b 9c cd  18 2f 47 13 21 7a 3d 87  |j......../G.!z=.|
*
000001a0  6a c0 b0 cd 98 81 5c 22  99 72 76 91 d0 08 88 ea  |j.....\".rv.....|
000001b0  d2 1c 33 8a 71 8b 71 f4  a1 5d 13 fb 96 17 00 fe  |..3.q.q..]......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 2e 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Hedgehog1 on 2011-04-30
I have studied and studied the script output, and for he life of me I just don't see when the XP isn't getting pulled into the grub menu.

I am going to ask someone who really knows **'The Grub Stuff'** to take a look, but in the meantime let me give you a solution so you can use XP right away while we figure out what is going on.

```
gksudo gedit /etc/grub.d/40_custom
```

Then cut and paste the text in red (This text is only for your PC, it is based on the script output you posted):

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[COLOR="Red"]menuentry "Windows XP  (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root A2A0815AA0813637
	chainloader +1
}[/COLOR]

```

Then do your normal:

```
sudo update-grub
```

This **should** allow you to boot into XP.

***The Hedge***

:KS

**p.s. Thanks for posting the script output - that helps a lot!**

---

### Post by metalous on 2011-04-30
Can I use the same "script" to make the dual boot with windows 7 ? (Ubuntu and Win 7)

---

### Post by LukeSweet08 on 2011-04-30
So I did all the things you said, copied the text, pasted it into mine, saved, the did the 

sudo update-grub

and still nothing!

This might shed some light on the situation. I previously had Ubuntu installed on the hard drive it's on now, but XP was on a different, 30 GB hard drive, and it dual booted great. I updated to 11.04 in Linux, and my 30 GB hard drive with XP dies on me (makes weird grinding noises, so its dead and can't be read). So, I take a spare hard drive I have, reinstall windows on it, and set it as the slave drive again, because that's what I did last time and it found it and could boot. So is there something from my old drive that's preventing it from booting? Like, is it still hard wired to boot from my old XP drive, and I somehow need to fix that? Also, is there a way to just set GRUB to it's old defaults, so that all previous info stored (like in my situation) is gone? 

Thanks again for the quck post!

---

### Post by LukeSweet08 on 2011-04-30
Not sure if this helps, but this is what I get when I run 

sudo update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/vmlinuz-2.6.35-28-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by LukeSweet08 on 2011-04-30
And another small tidbit....in Ubuntu 10.10, the GRUB would always load automatically by default. That is, I never had to hold Shift when it was booting, it would always just go there automatically....now it doesn't do that. Does that help?

---

### Post by LukeSweet08 on 2011-05-01
Problem solved! I basically reverted to GRUB, the reinstalled GRUB2 and I think it forced it to recompile and finally see Windows XP Pro. Thanks for the help everyone! I'm not sure how to change the header to [SOLVED] though.....

---

### Post by Zac280 on 2011-05-02
For a linux noob such as myself having the same issue, would you please list the steps to repair grub? Is it just sudo apt-get remove grub2, then reinstall from the repositories? Does any of this need to be done from live cd or can it be done from the install?

---

