---
title: "error on boot &quot;no filesystem could mount root&quot;"
date: 2012-03-19
forum: General Help
---

### Post by pocpoc on 2012-03-19
Hi everybody,

For about 2 weeks my laptop could no more boot on ubuntu (black screen after GRUB2) and yesterday I tried to boot with GRUB command line
```
root=(hd0,msdos2)
linux /boot/vmlinuz-2.6.38-8-generic
initrd /boot/initrd.img-2.6.38-8-generic
boot
```and it comes to this error message
```
no filesystem could mount root  tried: ext3 ext2 ext4 fuseblk
kernel panic not syncing VFS:unable to mount root filesystem on unknownblock (1,0)
```My hard disk is partionned like this

/dev/sda1 windows (ntfs) 
   /dev/sda2 linux (ext4)    
/dev/sda3 data (ext2)    
/dev/sda4 swap

I searched on Google for an answer but I didn't find so I ask you for help because I am tired to use Windows ;)

Thanks you for you patience :)

---

### Post by matt_symes on 2012-03-20
Hi

Try running fsck from a LiveCD/USB.

```
sudo fsck /dev/sda2
```

If you want to see what it thinks of the filling system before hand then 

```
sudo fsck -N /dev/sda2
```

I generally run the second command first anyway.

If it does not think there's a problem then it may be a UUID problem. If it does then run the first command.

Kind regards

---

### Post by pocpoc on 2012-03-20
Thanks for replying the partition is clean I can mount it from a liveCD or windows
here is the output of fsck

```
**[COLOR=Red]root@root[/COLOR]**:~# fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda2 : propre, 172191/1222992 fichiers, 972139/4882432 blocs
**[COLOR=Red]root@root[/COLOR]**:~# fsck -N /dev/sda2
fsck from util-linux-ng 2.17.2
[/sbin/fsck.ext4 (1) -- /dev/sda2] fsck.ext4 /dev/sda2
```So the filesystem is clean :p

---

### Post by matt_symes on 2012-03-20
Hi

From the LiveCD/USB, run the bootinfo script in my signature. The instructions are on the download page.

It's a trusted script used extensively on the forums and will give a lot more information about your hard drive and grub.

Post the results file back here.

Kind regards

---

### Post by pocpoc on 2012-03-20
Hi, 
Thank you for your script I downloaded it but I'll try it tonight cause I'm at school now so I'll give you the result when I got it :p.

EDIT: Here I am I just ran your script it's a very interesting tool and here is the output:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016
    Boot sector info:   Syslinux looks at sector 36064 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the 
                       /boot/syslinux directory. According to the info in the 
                       boot sector, sdb1 starts at sector 0. But according to 
                       the info from fdisk, sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/syslinux/syslinux.cfg /boot/grub/core.img 
                       /boot/syslinux/ldlinux.sys

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 22424 of /dev/sdb2 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 4196352.
    Operating System:  
    Boot files:        /syslinux.cfg /ntldr /NTDETECT.COM /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    41,942,879    41,942,817   7 NTFS / exFAT / HPFS
/dev/sda2    *     41,943,040    81,004,543    39,061,504  83 Linux
/dev/sda3          81,004,544   232,486,911   151,482,368  83 Linux
/dev/sda4         232,486,912   234,440,703     1,953,792  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     4,196,351     4,194,304   b W95 FAT32
/dev/sdb2           4,196,352    15,663,103    11,466,752   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2E08C42808C3ECC1                       ntfs       WINDOWS
/dev/sda2        ed4a321c-335b-41c8-925d-fb2290f37b7d   ext4       
/dev/sda3        3862b01c-f56a-4e4e-b81a-107f20d57576   ext2       DATA
/dev/sda4        5612c6f6-2018-48bb-a5dc-e72af8f2ff9a   swap       
/dev/sdb1        B6BE-3151                              vfat       MULTISYSTEM
/dev/sdb2        36E9-63E6                              vfat       
/dev/sdc1        183A-497D                              vfat       SWITCH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /mnt/sdc                 vfat       (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
set locale_dir=($root)/boot/grub/locale
set lang=fr_BE
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
menuentry 'Ubuntu, avec Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ed4a321c-335b-41c8-925d-fb2290f37b7d ro  vga=792 splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, avec Linux 2.6.38-8-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ed4a321c-335b-41c8-925d-fb2290f37b7d ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2E08C42808C3ECC1
    drivemap -s (hd0) ${root}
    chainloader +1
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=ed4a321c-335b-41c8-925d-fb2290f37b7d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=3862b01c-f56a-4e4e-b81a-107f20d57576 /home           ext2    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=5612c6f6-2018-48bb-a5dc-e72af8f2ff9a none            swap    sw              0       0

--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  34.136219025 = 36.653486080   boot/grub/core.img                             1
  34.337440491 = 36.869545984   boot/grub/grub.cfg                             1
  21.409862518 = 22.988664832   boot/initrd.img-2.6.38-8-generic               3
  34.233997345 = 36.758474752   boot/vmlinuz-2.6.38-8-generic                  1
  21.409862518 = 22.988664832   initrd.img                                     3
  34.233997345 = 36.758474752   vmlinuz                                        1

=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

timeout 30
default /default
#convert -resize 640x480 -colors 14 /media/multisystem/boot/splash/splash.png /media/multisystem/boot/splash/splash.xpm.gz
splashimage=/boot/splash/splash.xpm.gz
#color blue/green yellow/red white/magenta white/magenta
foreground=0033FF
background=FF3300

#http://diddy.boot-land.net/grub4dos/Grub4dos.htm
#http://www.boot-land.net/forums/index.php?showforum=66
#http://diddy.boot-land.net/grub4dos/files/syntax.htm
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_MENU_DEBUT|16-01-2012-20:47:02-653707647|FD0-konboot-v1.1-2in1.img|multisystem-konboot|1Mio|
title Kon-Boot bypass passwords
find --set-root /FD0-konboot-v1.1-2in1.img
map --mem /FD0-konboot-v1.1-2in1.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot
#MULTISYSTEM_MENU_FIN|16-01-2012-20:47:02-653707647|FD0-konboot-v1.1-2in1.img|multisystem-konboot|1Mio|
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#http://diddy.boot-land.net/grub4dos/files/syntax.htm

title Chainloader into GRUB 2
find --set-root /boot/grub/boot.img
chainloader /boot/grub/boot.img
boot

#title Chainloader into Syslinux
#map (hd0) (hd0)
#map (hd0) (hd0)
#chainloader (hd0,0)+1
#rootnoverify (hd0,0)

##Autre solution pour chainer Syslinux
##faire une copie du mbr de la clé USB
##dd if=/dev/sd?1 of=/media/multisystem/syslinux.mbr bs=512 count=1
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#map (hd0) (hd0)
#map (hd0) (hd0)
#map --rehook
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#chainloader /syslinux.mbr

##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root /boot/syslinux/ldlinux.sys
#chainloader /boot/syslinux/ldlinux.sys

##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /boot/syslinux/redir.img
#kernel /boot/syslinux/memdisk
#initrd /boot/syslinux/redir.img

#http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/
title FreeDos
kernel /boot/syslinux/memdisk
initrd /boot/img/fdboot.img

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA/SEVEN
fallback 2
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies --ignore-cd /cmldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot ubcd.iso
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title reboot
reboot

title halt
halt
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#insmod gpt
#insmod pc
#insmod gfxmenu
#
#insmod videotest
insmod tga
insmod png
insmod gfxterm
insmod lspci
#insmod vbeinfo
insmod vbe
insmod ntfs
insmod chain
insmod biosdisk
insmod font
#http://grub.enbug.org/ThemeFormat
#http://grub.gibibit.com/Theme_format#colors
#http://code.google.com/p/burg/wiki/InstallUbuntu
#http://code.google.com/p/burg/downloads/list
#http://ubuntuforums.org/showthread.php?t=1195275
#pour acces a grub2 du bootloader principal modifier dans fichier: /etc/default/grub
#GRUB_HIDDEN_TIMEOUT=10 #0 par defaut
#GRUB_HIDDEN_TIMEOUT_QUIET=false #true d'origine
#sudo update-grub
#echo -n "Press ESC to see the menu... "
#if sleep --verbose --interruptible 5 ; then
#set timeout=0
#fi
set default=0
set timeout=30
set fallback=1
search --no-floppy --fs-uuid --set=root B6BE-3151
set root=${root}
#http://grub.enbug.org/gfxterm
if loadfont /boot/polices/unicode.pf2 ; then
set gfxmode=640x480
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
#set gfxmode=auto
#set gfxpayload=keep
fi
fi
#set locale_dir=/boot/grub/locale
#set lang=en
#insmod gettext
if background_image /boot/splash/splash.png ; then
#text no sel/fond ecran
set color_normal=white/black #1
#text sel/fond ecran sel
set color_highlight=black/white #1
else
set menu_color_normal=white/black #2
set menu_color_highlight=black/white #2
set color_normal=white/red #2
set color_highlight=black/white #2
fi
#set gfxpayload="1280x1024,1024x768,800x600,640x480"
#set gfxpayload=keep
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_MENU_DEBUT|16-01-2012-20:54:29-568583634|backtrack1|multisystem-backtrack|1957Mio|
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2E08C42808C3ECC1
    drivemap -s (hd0) ${root}
    chainloader +1
}
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, avec Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ed4a321c-335b-41c8-925d-fb2290f37b7d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ed4a321c-335b-41c8-925d-fb2290f37b7d ro  vga=792 splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry "BackTrack i386 Text - Default Boot Text Mode" {
linux /backtrack1/casper/vmlinuz debian-installer/locale=fr_BE.UTF-8 debian-installer/language=fr kbd-chooser/method=fr console-setup/layoutcode=be console-setup/variantcode= console-setup/modelcode=pc105 live-media-path=/backtrack1/casper root=UUID=B6BE-3151 rootfstype=vfat file=/cdrom/backtrack1/preseed/custom.seed boot=casper text splash vga=791--
initrd /backtrack1/casper/initrd.gz
}
menuentry "BackTrack i386 Stealth - No Networking enabled" {
linux /backtrack1/casper/vmlinuz debian-installer/locale=fr_BE.UTF-8 debian-installer/language=fr kbd-chooser/method=fr console-setup/layoutcode=be console-setup/variantcode= console-setup/modelcode=pc105 live-media-path=/backtrack1/casper root=UUID=B6BE-3151 rootfstype=vfat file=/cdrom/backtrack1/preseed/custom.seed boot=casper text splash staticip vga=791--
initrd /backtrack1/casper/initrds.gz
}
menuentry "BackTrack i386 Forensics - No Drive or Swap Mount" {
linux /backtrack1/casper/vmlinuz debian-installer/locale=fr_BE.UTF-8 debian-installer/language=fr kbd-chooser/method=fr console-setup/layoutcode=be console-setup/variantcode= console-setup/modelcode=pc105 live-media-path=/backtrack1/casper root=UUID=B6BE-3151 rootfstype=vfat file=/cdrom/backtrack1/preseed/custom.seed boot=casper text splash vga=791--
initrd /backtrack1/casper/initrdf.gz
}
menuentry "BackTrack i386 noDRM - No DRM Drivers" {
linux /backtrack1/casper/vmlinuz debian-installer/locale=fr_BE.UTF-8 debian-installer/language=fr kbd-chooser/method=fr console-setup/layoutcode=be console-setup/variantcode= console-setup/modelcode=pc105 live-media-path=/backtrack1/casper root=UUID=B6BE-3151 rootfstype=vfat file=/cdrom/backtrack1/preseed/custom.seed boot=casper text splash nomodeset vga=791--
initrd /backtrack1/casper/initrd.gz
}
#MULTISYSTEM_MENU_FIN|16-01-2012-20:54:29-568583634|backtrack1|multisystem-backtrack|1957Mio|
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
menuentry "______________Grub4Dos______________" {
echo
}
#http://grub4dos.sourceforge.net/
#http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial
menuentry "Grub4Dos" {
    linux /boot/grub.exe --config-file=/boot/grub/menu.lst
}
menuentry "______________Syslinux______________" {
echo
}
#solution tordue, mais qui passe partout ...
#menuentry "Syslinux" {
#search --set -f /boot/syslinux/redir.img
#    linux16 /boot/syslinux/memdisk
#    initrd16 /boot/syslinux/redir.img
#}
#http://syslinux.zytor.com
menuentry "Syslinux" {
search --set -f "/boot/syslinux/ldlinux.sys"
drivemap -s (hd0) $root
chainloader +1
}
#Autre solution pour chainer Syslinux via une copie du mbr
#dd if=/dev/sd?1 of=/media/multisystem/syslinux.mbr bs=512 count=1
#menuentry "Syslinux" {
#search --set -f "/syslinux.mbr"
#drivemap -s (hd0) $root
#chainloader /syslinux.mbr
#}
menuentry "______________UTIL______________" {
echo
}
## for debugging set debug=efi
#menuentry "0-testfakebios" {
#    hexdump -s 0xc0000 (mem)
#    fakebios
#    hexdump -s 0xc0000 (mem)
## deliberate error to get wait for key
#    xxx
#}
#How to test GRUB 2 on Macbook
#http://grub.enbug.org/TestingOnMacbook
#chainer un autre grub
#menuentry "grub.cfg auf /dev/sdb1" {
#    configfile (hd1,1)/boot/grub/grub.cfg
#}
#menuentry "Chain other configfile" {
#configfile /boot/grub/grub-xxx.cfg
#}
#
#menuentry "Return default menu" {
#chainloader /boot/grub/boot.img
#}
#chainer win ou autre OS
#menuentry "Chainer UUID de la partition" {
#insmod=ntfs
#set root=(hd0,1)
#search --no-floppy --fs-uuid --set=root xxx-xxx
#    drivemap -s (hd0) $root
#    chainloader +1
#}
#http://www.plop.at/en/bootmanagerdl.html
menuentry "PLoP Boot Manager" {
    linux16 /boot/img/plpbt
}
#http://www.supergrubdisk.org/
#http://developer.berlios.de/project/showfiles.php?group_id=10921
#SG2D (Floppy, CD & USB in one)
#super_grub_disk_hybrid-1.98s1.iso
menuentry "Super Grub2 Disk" {
search --set -f /boot/img/sgdh.iso
    linux16 /boot/syslinux/memdisk
    initrd16 /boot/img/sgdh.iso
}
menuentry "Super Grub Disk" {
search --set -f /boot/img/sgdfr.img
    linux16 /boot/syslinux/memdisk
    initrd16 /boot/img/sgdfr.img
}
menuentry "Smart Boot Manager" {
search --set -f /boot/img/sbootmgr.dsk
    linux16 /boot/syslinux/memdisk
    initrd16 /boot/img/sbootmgr.dsk
}
#Site: http://boot.kernel.org/index.html
#Téléchargement: http://boot.kernel.org/gpxe_images/gpxe.lkrn
menuentry "BKO (boot.kernel.org)" {
    search --set -f /boot/img/gpxe.lkrn
    linux16 /boot/img/gpxe.lkrn
}
#http://www.memtest.org/#downiso
menuentry "memtest86+" {
    linux16 /boot/img/memtest86+.bin
}
menuentry "vbeinfo" {
    vbeinfo
read
}
menuentry "lspci" {
    lspci
read
}
menuentry "gfxpayload 640x480" {
set gfxpayload=640x480
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 800x600" {
set gfxpayload=800x600
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1024x768" {
set gfxpayload=1024x768
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1280x1024" {
set gfxpayload=1280x1024
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "Reboot" {
insmod reboot
reboot
}
--------------------------------------------------------------------------------

======================= sdb1/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
timeout 40
ontimeout 0

MENU TITLE MultiSystem LiveUSB
MENU DEFAULT 0

MENU BACKGROUND /boot/splash/splash.png

#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!

label 0
MENU LABEL PLoP Boot Manager
KERNEL /boot/img/plpbt

label 1
MENU LABEL Grub2
kernel chain.c32 file=/boot/grub/boot.img

label 2
MENU LABEL Grub4Dos
kernel /boot/grub.exe

LABEL 3
MENU LABEL Hardware Detection Tool
KERNEL /boot/syslinux/hdt.c32

#Exemple pour booter un iso avec version recente de memdisk
#label 4
#MENU LABEL boot iso
#KERNEL memdisk
#APPEND iso raw initrd=/g4u.iso

#LABEL 5
#KERNEL memdisk
#APPEND initrd=freebsd.img floppy

#LABEL 6
#MENU LABEL Chainer win
#KERNEL chain.c32 ntldr=/ntldr

#LABEL 7
#MENU LABEL Chainer partition 2
#kernel chain.c32
#append hd0 2

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/grub/menu.lst                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/syslinux/chain.c32                        1
            ?? = ??             boot/syslinux/hdt.c32                          1
            ?? = ??             boot/syslinux/ifplop.c32                       1
            ?? = ??             boot/syslinux/ldlinux.sys                      1
            ?? = ??             boot/syslinux/menu.c32                         1
            ?? = ??             boot/syslinux/reboot.c32                       1
            ?? = ??             boot/syslinux/syslinux.cfg                     1
            ?? = ??             boot/syslinux/vesamenu.c32                     1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/syslinux/chain.c32            :  COM32R module (v4.xx)
 boot/syslinux/hdt.c32              :  COM32R module (v4.xx)
 boot/syslinux/ifplop.c32           :  COM32R module (v4.xx)
 boot/syslinux/menu.c32             :  COM32R module (v4.xx)
 boot/syslinux/reboot.c32           :  COM32R module (v4.xx)
 boot/syslinux/vesamenu.c32         :  COM32R module (v4.xx)

============================== sdb2/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb2: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             vesamenu.c32                                   1

============== sdb2: Version of COM32(R) files used by Syslinux: ===============

 vesamenu.c32                       :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  2d 37 86 26 8e ae 31 5c  c7 8f 81 60 64 b1 ee 4b  |-7.&..1\...`d..K|
00000010  0f 7c 7a 7c d9 c1 3d 9c  15 b9 3a 4c 0c 45 ad 40  |.|z|..=...:L.E.@|
00000020  26 33 f7 b5 94 f5 0d 39  fb 07 52 81 51 89 3d f5  |&3.....9..R.Q.=.|
00000030  ef 1d 7f f3 ee 9b 95 f4  6e 7b 87 ab c8 2d 25 5e  |........n{...-%^|
00000040  1e 64 d0 82 6c 81 ef 61  5e c6 4c e6 9f 7d 99 1d  |.d..l..a^.L..}..|
00000050  7d dd dd 66 6f 7d dd dd  a2 9f 0d 40 9a fa 31 3f  |}..fo}.....@..1?|
00000060  8a ea a6 1a 06 60 4d 9f  fd 3d cf 7e 01 a1 dd 3e  |.....`M..=.~...>|
00000070  48 1b 40 31 a1 04 1b b9  aa 14 ed 9b 88 3b c2 3e  |H.@1.........;.>|
00000080  29 05 1b 45 a3 cb a1 c5  3e b8 47 5b 87 00 d8 9d  |)..E....>.G[....|
00000090  3b 1b c5 04 8f 38 91 a6  d3 33 dd b6 e1 29 23 d0  |;....8...3...)#.|
000000a0  fd c3 e4 36 63 c9 3c 3a  7c 0d 8d 92 82 8d 5c e7  |...6c.<:|.....\.|
000000b0  95 5b 39 c3 a1 54 19 32  78 ac 4a f3 29 79 ff db  |.[9..T.2x.J.)y..|
000000c0  bd 7f f0 07 27 1e f8 72  5c a2 ae bc 42 4e b0 06  |....'..r\...BN..|
000000d0  0f 15 8f 0b bc d3 64 b6  c2 57 b1 94 30 19 82 fb  |......d..W..0...|
000000e0  0c 34 dc 53 08 92 99 3c  45 42 40 30 24 4d 45 3f  |.4.S...<EB@0$ME?|
000000f0  7f ea 26 e5 a4 5e f7 d4  ae 42 de f7 64 b6 e5 a0  |..&..^...B..d...|
00000100  ee 66 0f a7 95 7a 1d 04  5e b0 ea 30 80 ad d0 f3  |.f...z..^..0....|
00000110  84 f2 3d 82 e7 08 91 13  01 8c 02 fe 17 81 8a 04  |..=.............|
00000120  85 e4 cb dd d6 88 59 ca  46 f4 9e a9 55 69 23 ed  |......Y.F...Ui#.|
00000130  ef a4 4d fa 85 f8 2e ac  78 19 18 30 b9 76 7f 27  |..M.....x..0.v.'|
00000140  ff d8 58 db ef bd a7 d7  9c bf a0 6a 03 10 ad ac  |..X........j....|
00000150  c1 7b 7e 5d 44 33 42 68  f1 f1 89 9b de f7 39 b7  |.{~]D3Bh......9.|
00000160  6e 2c 18 dc 2f 73 ad 6b  7b c9 f7 dc 92 d9 f0 e1  |n,../s.k{.......|
00000170  c9 17 4e c8 fa 1d ae 83  9d e1 0c 91 3e 01 b3 3e  |..N.........>..>|
00000180  ac c1 fa b8 cf d6 f8 30  74 d4 45 3d 82 29 4a 0a  |.......0t.E=.)J.|
00000190  2b 2e 10 fc a4 7c ce 02  d8 b2 85 ed e0 9d 74 b9  |+....|........t.|
000001a0  6b 4d 82 bb 41 83 27 ee  4a 44 06 e9 5c 03 36 1a  |kM..A.'.JD..\.6.|
000001b0  78 a4 42 11 92 0f fd cb  60 e4 d3 d3 fb 4c ef f7  |x.B.....`....L..|
000001c0  4b 28 de f5 60 5a 61 0b  c5 b6 73 be ff 50 a2 7f  |K(..`Za...s..P..|
000001d0  de ba 6e 71 e0 4e 23 f2  7c 12 0b a0 e3 a6 e0 ac  |..nq.N#.|.......|
000001e0  52 3f 91 8f f8 b4 17 22  cb 16 ff f0 24 2a d8 b5  |R?....."....$*..|
000001f0  ca c5 89 9b fd ef 45 53  1c c5 06 4f bc 02 dd 00  |......ES...O....|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```Dont mind about sdb and sdc they are my usb sticks. ;)

I hope you can find out the problem with these informations

Thanks for your patience :p

---

### Post by matt_symes on 2012-03-21
Hi

> Thank you for your script I downloaded it but I'll try it tonight cause I'm at school now so I'll give you the result when I got it 

Just to let you know the script is not mine and i did not write it.

If no one else looks at this thread, i will take a look later today for you. I have a busy morning.

Kind regards

---

### Post by matt_symes on 2012-03-22
Hi

Sorry for the late reply. Been a busy couple of days.

I can't see much wrong with the results from the script but i am no expert at grub. I will ask for a second opinion for you.

Kind regards

---

### Post by pocpoc on 2012-03-22
Don't worry it's okay :) Thank you

---

### Post by pocpoc on 2012-03-26
up please :)

---

