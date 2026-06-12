---
title: "freedos and grub 2"
date: 2010-03-27
forum: General Help
---

### Post by tjtremor on 2010-03-27
how do you boot freedos with grub 2 ?? I've read some guides but i'm not making progress

i have following files on the root of the second partition (fat16), first partition is ubuntu 9.10 and that boots fine
/memdisk
/fdodin06.144

can anyone tell me what I should have for  '/etc/grub.d/' script



thanks

-edit
finally able to go past grub but system reboots after initrd command
set root=(hd0,3)
linux /memdisk
initrd /fdodin06.144

---

### Post by xcist on 2010-08-11
Not sure if this is the right place to ask, but since a thread already exists... I can't boot to FreeDOS either. With a fresh install and update-grub, selecting *FreeDOS (on /dev/sda7)* from boot menu results in "Loading FreeDOS no KERNEL SYS". I've tried changing boot flags and messing with MBR with Parted Magic, and editing /etc/grub.d/40_custom and even grub.cfg.

I use Xubuntu 10.04 (Lucid Lynx).

```

Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
   partition #6 for /boot/grub.

sda1: _________________________________________________________________________

   File system:       vfat
   Boot sector type:  Windows XP: Fat32
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows XP
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:  Windows XP
   Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

   File system:       Extended Partition
   Boot sector type:  -
   Boot sector info:

sda5: _________________________________________________________________________

   File system:       swap
   Boot sector type:  -
   Boot sector info:

sda6: _________________________________________________________________________

   File system:       ext4
   Boot sector type:  -
   Boot sector info:
   Operating System:  Ubuntu 10.04 LTS
   Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
                      /boot/grub/core.img

sda7: _________________________________________________________________________

   File system:       vfat
   Boot sector type:  Unknown
   Boot sector info:  According to the info in the boot sector, sda7 starts
                      at sector 63.
   Operating System:
   Boot files/dirs:   /COMMAND.COM

sda8: _________________________________________________________________________

   File system:       ntfs
   Boot sector type:  Windows Vista/7
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:
   Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________
_____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  1b Hidden W95 FAT32
/dev/sda2          10,233,405    30,741,217    20,507,813   7 HPFS/NTFS
/dev/sda3          30,742,526   312,580,095   281,837,570   5 Extended
/dev/sda5          30,742,528    34,744,319     4,001,792  82 Linux
swap / Solaris
/dev/sda6          34,746,368    59,158,527    24,412,160  83 Linux
/dev/sda7    *     59,167,458    66,332,384     7,164,927   b W95 FAT32
/dev/sda8          66,332,448   312,576,704   246,244,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE
LABEL

/dev/sda1        0159-6699                              vfat
PQSERVICE
/dev/sda2        CE0C9DE80C9DCBB9                       ntfs
ACER
/dev/sda3: PTTYPE="dos"
/dev/sda5        c9ba41b3-f752-4c8f-81bd-5e6068c74e6f   swap
/dev/sda6        9da465c6-1812-43ae-be6a-1f32190de508   ext4
/dev/sda7        2B3B-1DF2                              vfat
FREEDOS
/dev/sda8        6D96C7C20F653093                       ntfs
/dev/sda: PTTYPE="dos"

============================ "mount | grep ^/dev  output:
===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home
Edition" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9da465c6-1812-43ae-be6a-1f32190de508 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9da465c6-1812-43ae-be6a-1f32190de508

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

title           Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid            9da465c6-1812-43ae-be6a-1f32190de508
kernel          /boot/vmlinuz-2.6.32-21-generic
root=UUID=9da465c6-1812-43ae-be6a-1f32190de508 ro quiet splash
initrd          /boot/initrd.img-2.6.32-21-generic

title           Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid            9da465c6-1812-43ae-be6a-1f32190de508
kernel          /boot/vmlinuz-2.6.32-21-generic
root=UUID=9da465c6-1812-43ae-be6a-1f32190de508 ro  single
initrd          /boot/initrd.img-2.6.32-21-generic

title           Ubuntu 10.04 LTS, memtest86+
uuid            9da465c6-1812-43ae-be6a-1f32190de508
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
 if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then
save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 9da465c6-1812-43ae-be6a-1f32190de508
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 9da465c6-1812-43ae-be6a-1f32190de508
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
 set timeout=-1
else
 set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu
--class gnu-linux --class gnu --class os {
       recordfail
       insmod ext2
       set root='(hd0,6)'
       search --no-floppy --fs-uuid --set 9da465c6-1812-43ae-be6a-1f32190de508
       linux   /boot/vmlinuz-2.6.32-21-generic
root=UUID=9da465c6-1812-43ae-be6a-1f32190de508 ro   quiet splash
       initrd  /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
       insmod fat
       set root='(hd0,1)'
       search --no-floppy --fs-uuid --set 0159-6699
       drivemap -s (hd0) ${root}
       chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
       insmod ntfs
       set root='(hd0,2)'
       search --no-floppy --fs-uuid --set ce0c9de80c9dcbb9
       drivemap -s (hd0) ${root}
       chainloader +1
}
menuentry "FreeDOS (on /dev/sda7)" {
       insmod fat
       set root='(hd0,7)'
       search --no-floppy --fs-uuid --set 2b3b-1df2
       drivemap -s (hd0) ${root}
       chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9da465c6-1812-43ae-be6a-1f32190de508 /               ext4
errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9ba41b3-f752-4c8f-81bd-5e6068c74e6f none            swap    sw
          0       0

=================== sda6: Location of files loaded by Grub: ===================


 26.6GB: boot/grub/core.img
 26.7GB: boot/grub/grub.cfg
 26.6GB: boot/grub/menu.lst
 21.0GB: boot/initrd.img-2.6.32-21-generic
 20.9GB: boot/vmlinuz-2.6.32-21-generic
 21.0GB: initrd.img
 20.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc
=======================

Unknown BootLoader  on sda7

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 08 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 53 6d 00 48 1b 00 00  00 00 00 00 02 00 00 00  |.Sm.H...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  ff 00 29 f2 1d 3b 2b 46  52 45 45 44 4f 53 20 20  |..)..;+FREEDOS  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 5e 5a  |@.^.s........_^Z|
000001c0  c3 4c 6f 61 64 69 6e 67  20 46 72 65 65 44 4f 53  |.Loading FreeDOS|
000001d0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4e 6f  |..............No|
000001f0  20 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  | KERNEL  SYS..U.|
00000200

```

---

### Post by oldfred on 2010-08-11
I have not done it but saved this:
# This method applies to Windows and to FreeDOS
menuentry &#8220;Windows XP on sda1, by chainloader&#8221;  {
set root=(hd0,1)
chainloader +1
 }


FreeDos is like windows in that you have additional boot code in the partition boot sector or PBR. sys is the command to load the boot code to a drive with dos. Freedos mentions the same command.

xcist - your boot stanza looks ok as it is like the one I saved. Did you sys and install all the boot code? The boot_info script is not set up to parse freedos so we cannot tell if your boot code is present and all the boot files are in your partition.

[http://wiki.fdos.org/Installation/HomePage](http://wiki.fdos.org/Installation/HomePage)

---

### Post by xcist on 2010-08-12
To get the installer to start from a USB flash drive, you have to uncompress contents of ISO to drive, rename ISO to fdbootcd.iso and copy that too. I just ran it again, but forgot step 2 so it failed and defaulted to a command prompt.

Now *sys d:* worked (before, it couldn't find kernel.sys no matter what drive I was on). [_Everything looks the same though._](http://i174.photobucket.com/albums/w108/fartigo/fdos.jpg) And it still says "Loading FreeDOS no KERNEL SYS".

I've tried these two

```
root (hd0,7)
chainloader +1

root (hd0,7)
chainloader /kernel.sys
```

So, this is probably a FreeDOS boot issue and can't be overridden with Grub?

---

