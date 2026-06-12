---
title: "Can't boot windows 7 - An old GRUB is on it's boot partition."
date: 2011-01-05
forum: General Help
---

### Post by silkworm2.5 on 2011-01-05
Hi all.
Recently I had some troubles with Ubuntu which I sorted out with a re-install. The problem I'm having is that when I installed the problematic Ubuntu, I installed Grub to my Windows 7 booting partition. A measure I took so that if I ever had to delete the Ubuntu partition, GRUB would remain intact.
I didn't specify this on this new install though, and so GRUB is on my Ubuntu partition. However, I think the old GRUB is still on the Windows 7 boot partition, as whenever I try to boot it, it just displays a black screen with an underscore on it.
I don't know how to fix this so could someone help please?

---

### Post by sohlinux on 2011-01-05
you can restore your windows boot loader with the windows installation cd

---

### Post by silkworm2.5 on 2011-01-05
Is that the only way? I re-installed before and it wiped my entire hard drive...

---

### Post by sohlinux on 2011-01-05
> **silkworm2.5 said:**
> Is that the only way? I re-installed before and it wiped my entire hard drive...

do you have 1 hard drive?

you dont need to re install windows you can just fix the boot loader using the windows install disk

in ubuntu you can try sudo update-grub

and you can install startup manager from the ubuntu software manager which will allow you to choose the default OS to boot

---

### Post by silkworm2.5 on 2011-01-05
> **sohlinux said:**
> do you have 1 hard drive?

you dont need to re install windows you can just fix the boot loader using the windows install disk

in ubuntu you can try sudo update-grub

and you can install startup manager from the ubuntu software manager which will allow you to choose the default OS to boot

Yes I have one drive.
I don't have a standard recovery disk. I have one from CompaQ, with no options to reinstall bootloader or anything. Just re-install, backup, system recovery, or CMD.

I tried Sudo ubdate-grub, and it made no difference.

I have startup manager, but I don't want to change the default OS.

So, what should I do? Is there a CMD command I can type in?

---

### Post by sohlinux on 2011-01-05
> **silkworm2.5 said:**
> Yes I have one drive.
I don't have a standard recovery disk. I have one from CompaQ, with no options to reinstall bootloader or anything. Just re-install, backup, system recovery, or CMD.

I tried Sudo ubdate-grub, and it made no difference.

I have startup manager, but I don't want to change the default OS.

So, what should I do? Is there a CMD command I can type in?

restoring a windows bootloader in linux is tricky but entering into CMD from the windows restore disk will allow you to do it, then when you are back in windows use EasyBCD to restore linux to your boot up options

windows fixmbr command will do it but best you look on some windows forums on how to restore the windows bootloader using CMD

---

### Post by silkworm2.5 on 2011-01-05
I tried fixmbr, but it did nothing but delete GRUB from the MBR (Luckily I made a backup today ^^) Any other ideas on what to try? I tried all of what this guy said:

> [CENTER][** [COLOR=#996600]billdo[/COLOR]**]("http://www.sevenforums.com/member.php?u=14503") [/CENTER]
 
 
  [CENTER] [CENTER] Windows 7 x64 rtm
 [83 posts]("http://www.sevenforums.com/search.php?do=finduser&u=14503")
 [/CENTER]
  [/CENTER]
  [CENTER]   
    
 
 [/CENTER]
                                                                                    
 
   
      These  were commands used for vista, but should still hold true for Windows 7.  I've just never needed to use them yet......knock on wood[IMG]http://cdn.sevenforums.com/images/smilies/smile.gif[/IMG]
 
after selecting repair>cmd prompt, enter:
 [I][B]BootRec.exe /fixmbr
 
 [/B][/I]you can also substitue the*** /fixmbr ***with thes commands:[I][B]
 
/FixBoot[/B]. Writes a boot sector onto the system partition to start Windows
 [/I][I][B]
/ScanOs[/B]. Scans all disks for Windows installations and displays them to you. 
 [/I][I][B]
/RebuildBcd[/B]. Scans all disks for Windows installations and prompts you to pick the ones you want to add to the BCD.[/I]



EDIT: I should have mentioned that /ScanOS reports that there are no Windows OS's on the drive.

---

### Post by sohlinux on 2011-01-05
you could try ms-sys but it didnt work for me when I had the same problem as you

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)


failing that then fixmbr should work

---

### Post by schwabdale on 2011-01-05
You could try to make an image of the Windows 7 installation using something like macrium, or driveimagexml....Then formatting the drive, and restoring from the image. 
I'm not sure though if the image would carry the Grub information over.

---

### Post by silkworm2.5 on 2011-01-05
Nope. No joy with either. FixMbr says it's worked but does nothing, and ms-sys just couldn't be found.

---

### Post by drs305 on 2011-01-05
I'm jumping in a bit late but if you would run the boot info script from the following site and post the contents of the RESULTS.txt we will know the status of your boot files:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

You can easily restore the MBR to point to Windows, but that may not be what you need if your partition boot files have been altered. In that case, you would need to repair them with a Windows repair disk.

Also back to your original post. Are you sure the blinking cursor is the result of booting Windows and not Ubuntu? This may or may not be a boot issue. If you are in fact booting into Ubuntu and have an nvidia card you may simply need to reinstall the video driver. We can tell you how to do that if necessary.

It's also possible that even though you installed Grub to the partition, it is still using Grub2 from the MBR. The boot info script will give us some information.

---

### Post by silkworm2.5 on 2011-01-05
Ok, Here is what the script came back with:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: ************************************************************************_

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: ************************************************************************_

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: ************************************************************************_

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sda4: ************************************************************************_

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: ************************************************************************_

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: ************************************************************************_

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: ************************************************************************_

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ******************_ ************************************_________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   358,811,774   358,402,175   7 HPFS/NTFS
/dev/sda3         358,811,775   420,244,334    61,432,560  83 Linux
/dev/sda4         420,245,502   976,773,119   556,527,618   5 Extended
/dev/sda5         420,245,504   954,144,767   533,899,264  83 Linux
/dev/sda6         954,146,816   976,773,119    22,626,304  82 Linux swap / Solaris


Drive: sdb ******************_ ************************************_________________

Disk /dev/sdb: 518 MB, 518520832 bytes
16 heads, 62 sectors/track, 1020 cylinders, total 1012736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  62     1,011,839     1,011,778   c W95 FAT32 (LBA)


blkid -c /dev/null: ******************************************************______

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24D2084CD20824A0                       ntfs       SYSTEM                        
/dev/sda2        3416272F1626F212                       ntfs                                     
/dev/sda3        ec5c9b59-c1e9-4d43-ac65-1ddec3e63d50   crypto_LUKS                               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e00ddccd-1f34-4006-84ee-21ef3d629ec7   ext4                                     
/dev/sda6        06f002b6-1117-47be-9733-72c04c029c5f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E064-E123                              vfat       Wilfind                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/UBCD50RC1         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/Wilfind           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
insmod jpeg
if background_image /usr/share/images/desktop-base/Splash.jpg ; then
  set color_normal=blue/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e00ddccd-1f34-4006-84ee-21ef3d629ec7 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e00ddccd-1f34-4006-84ee-21ef3d629ec7 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24d2084cd20824a0
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3416272f1626f212
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
UUID=e00ddccd-1f34-4006-84ee-21ef3d629ec7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=06f002b6-1117-47be-9733-72c04c029c5f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 455.9GB: boot/grub/core.img
 456.0GB: boot/grub/grub.cfg
 288.0GB: boot/initrd.img-2.6.32-27-generic
 455.9GB: boot/vmlinuz-2.6.32-27-generic
 288.0GB: initrd.img
 455.9GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
insmod jpeg
if background_image /usr/share/images/desktop-base/Splash.jpg ; then
  set color_normal=blue/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e00ddccd-1f34-4006-84ee-21ef3d629ec7 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e00ddccd-1f34-4006-84ee-21ef3d629ec7 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e00ddccd-1f34-4006-84ee-21ef3d629ec7
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24d2084cd20824a0
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3416272f1626f212
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 04 08 00 00 00 10  |................|
00000070  99 2e 4d 9b d3 20 41 84  9d 2d 07 ed b7 76 57 43  |..M.. A..-...vWC|
00000080  10 ca 2a 2b 9a 76 69 b2  8b 2d cb ce 7c 47 89 d5  |..*+.vi..-..|G..|
00000090  3d 8b b7 4d de f3 ea ed  98 02 be 90 44 dd fe 19  |=..M........D...|
000000a0  06 43 c6 52 00 00 00 0a  65 63 35 63 39 62 35 39  |.C.R....ec5c9b59|
000000b0  2d 63 31 65 39 2d 34 64  34 33 2d 61 63 36 35 2d  |-c1e9-4d43-ac65-|
000000c0  31 64 64 65 63 33 65 36  33 64 35 30 00 00 00 00  |1ddec3e63d50....|
000000d0  00 ac 71 f3 00 02 7f a7  38 38 81 41 60 92 84 3f  |..q.....88.A`..?|
000000e0  a0 19 41 a6 66 ef 35 27  49 d0 ac 4c 3a c8 e8 a3  |..A.f.5'I..L:...|
000000f0  23 4a 79 c6 b6 79 aa 0a  00 00 00 08 00 00 0f a0  |#Jy..y..........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 88 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 01 88 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 02 88 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sda4

00000000  2e 78 64 94 2f 12 40 16  98 ce 28 dd 4a c4 54 52  |.xd./.@...(.J.TR|
00000010  6f e2 a9 15 4d ee 88 36  43 65 64 43 e4 3f fa cd  |o...M..6CedC.?..|
00000020  15 64 8d 2b 0b 06 a1 d2  b5 99 88 c1 28 71 e2 c1  |.d.+........(q..|
00000030  5d 47 de a2 c1 38 da 11  a9 8e 48 18 ab e7 0a d2  |]G...8....H.....|
00000040  d1 0b 82 51 3d f0 b6 8a  8e db cb 51 90 c6 ce a7  |...Q=......Q....|
00000050  ae 87 bc 77 d1 a5 29 78  39 84 72 bb 2f ae 2d a1  |...w..)x9.r./.-.|
00000060  44 53 61 7b b2 03 13 37  94 17 ce a9 a2 77 75 b1  |DSa{...7.....wu.|
00000070  eb fb 6d 8c 48 6b 8a da  62 e3 a2 24 72 20 a6 bf  |..m.Hk..b..$r ..|
00000080  5c 4c b4 51 dc c5 bb e5  4c 8a e2 ee cd a7 14 52  |\L.Q....L......R|
00000090  41 b1 0a dc af 0a 1d 83  42 9e ca f3 10 eb 96 30  |A.......B......0|
000000a0  bc e9 93 16 e3 91 98 14  13 8b 02 b3 c9 ac 5b 24  |..............[$|
000000b0  40 3c f0 bb 68 0f 75 c8  91 99 f7 cc 5e 16 8c ee  |@<..h.u.....^...|
000000c0  59 18 87 e9 1a 8d 70 67  63 fa a2 c7 a2 06 9f f8  |Y.....pgc.......|
000000d0  b4 c9 13 43 95 d3 d2 8a  34 f2 5c a5 1f f4 6c 1a  |...C....4.\...l.|
000000e0  6f c2 a6 9b 59 59 25 6a  65 68 40 6e 39 29 8c 85  |o...YY%jeh@n9)..|
000000f0  1b a7 c6 66 88 5e 19 35  55 86 a1 46 2d 32 8b 5e  |...f.^.5U..F-2.^|
00000100  e6 32 0d 41 3b 6c 3c 50  19 0e f2 5b 01 5c be cf  |.2.A;l<P...[.\..|
00000110  9b de 03 82 ef a4 9f de  a5 9b e0 81 78 7d 6c da  |............x}l.|
00000120  5d 08 5f 25 c8 ee 7c 52  a6 f4 6d 33 a0 c8 9d 57  |]._%..|R..m3...W|
00000130  15 ce cc b6 5c b6 37 1b  2a 7a 60 2d e5 c2 14 3e  |....\.7.*z`-...>|
00000140  a2 d5 8c 99 b2 6f 39 4a  2b a8 0b ba 7b ae 55 22  |.....o9J+...{.U"|
00000150  87 0b 13 51 5b 6f 86 6d  d8 56 fa b9 91 e0 ee 8b  |...Q[o.m.V......|
00000160  0d f7 db 43 a8 c6 63 e5  fc 24 7e 0c 49 54 00 5a  |...C..c..$~.IT.Z|
00000170  8f 1a 6f 78 35 ae bd 76  8c 98 ab 4f ec 2b 3e 82  |..ox5..v...O.+>.|
00000180  d5 b7 a4 90 a5 33 59 05  74 4c bf 23 1c 8e f5 be  |.....3Y.tL.#....|
00000190  d5 29 be 16 2a 3a fa 46  8c 7e 6e 8d 8c dc 18 1d  |.)..*:.F.~n.....|
000001a0  2c ab af a7 01 00 f3 d9  20 1c 56 40 9b fa c4 ba  |,....... .V@....|
000001b0  c2 f9 6e f5 68 80 3a 2d  b7 de 61 24 6d 8b 00 fe  |..n.h.:-..a$m...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a8 d2 1f 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a8  d2 1f 00 48 59 01 00 00  |...........HY...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2011-01-05
While you are waiting for some Windows users to chime in, if you are on an Ubuntu LiveCD...

Disclaimer: Not a Windows user, but I'd try this if I was bored or got tired of waiting for a Windows user to respond.  ;-)

The results I've seen for W7 normally have either 1) boot partition with /bootmgr and /boot/BCD and a W7 partition with /Windows/System32/winload.exe , or 2) /bootmgr /boot/BCD /Windows/System32/winload.exe all on a single partition. 

I was just wondering if it would boot if you moved the boot flag to sda2. If sda2 had all the necessary files perhaps it would boot. If you want to try it, from the LiveCD just open System, Administration, Disk Utility. Highlight sda2 and then click on Edit Partition and tick "Bootable" and reboot. 

If it doesn't boot, move the boot flag back to sda1.

---

### Post by sohlinux on 2011-01-05
I would ask on some windows forums

---

### Post by silkworm2.5 on 2011-01-05
Ok, I'll wait for someone who knows more about Windows. Thank you both for your help! :)

---

