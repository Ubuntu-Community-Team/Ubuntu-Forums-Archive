---
title: "window 7 restarts computer"
date: 2010-09-14
forum: General Help
---

### Post by techclown on 2010-09-14
in grub i choose Windows 7 but all it does is restart computer. 

I had windows 7 installed first then dual boot ubuntu 10.04 on same drive

PLEASE help !!!

Thanks

---

### Post by oldfred on 2010-09-14
Post this, you can run from Ubuntu or the liveCD, just note where it downloads.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by techclown on 2010-09-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   254,253,178   254,046,331   7 HPFS/NTFS
/dev/sda3         254,255,102   312,580,095    58,324,994   5 Extended
/dev/sda5         254,255,104   310,083,583    55,828,480  83 Linux
/dev/sda6         310,085,632   312,580,095     2,494,464  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4E18C13618C11E39                       ntfs       System Reserved               
/dev/sda2        0288C4F888C4EAED                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ea9d82cd-42ac-4e92-8b68-248bae04c5a0   ext4                                     
/dev/sda6        3ea577ae-ad05-4cb4-8c4f-5f9b2fb3c140   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ea9d82cd-42ac-4e92-8b68-248bae04c5a0

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        ea9d82cd-42ac-4e92-8b68-248bae04c5a0
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        ea9d82cd-42ac-4e92-8b68-248bae04c5a0
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Chainload into GRUB 2
root        ea9d82cd-42ac-4e92-8b68-248bae04c5a0
kernel        /boot/grub/core.img

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        ea9d82cd-42ac-4e92-8b68-248bae04c5a0
kernel        /boot/memtest86+.bin

title Windows sda2
rootnoverify (hd0,1)
chainloader +1
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea9d82cd-42ac-4e92-8b68-248bae04c5a0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e18c13618c11e39
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
UUID=ea9d82cd-42ac-4e92-8b68-248bae04c5a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3ea577ae-ad05-4cb4-8c4f-5f9b2fb3c140 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 132.4GB: boot/grub/core.img
 156.1GB: boot/grub/grub.cfg
 132.5GB: boot/grub/menu.lst
 132.4GB: boot/grub/stage2
 132.4GB: boot/initrd.img-2.6.32-24-generic
 132.4GB: boot/vmlinuz-2.6.32-24-generic
 132.4GB: initrd.img
 132.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f7 bc 10 75 f5 6c 27 ea  b0 b5 93 92 23 90 92 2a  |...u.l'.....#..*|
00000010  25 50 12 4e d7 80 90 9c  f5 fc 12 4f f9 76 b2 4e  |%P.N.......O.v.N|
00000020  49 ba e0 0d 42 cd 18 28  69 3e 58 95 2c e8 19 f2  |I...B..(i>X.,...|
00000030  f1 01 fa 5d 68 b3 74 b7  19 d4 c0 f9 5c 5e 49 45  |...]h.t.....\^IE|
00000040  47 f9 35 1c da 2c 1d a1  34 83 0b 8e e0 66 9a 54  |G.5..,..4....f.T|
00000050  85 80 03 bf 83 ee b4 89  82 99 e9 95 ca 88 3e b8  |..............>.|
00000060  29 d5 ef 5d 4a d7 fe ac  7f b6 92 c9 80 4a 9d e6  |)..]J........J..|
00000070  c0 5d 49 d5 ee 4e 51 5d  c8 06 bc ad cb 03 95 bc  |.]I..NQ]........|
00000080  b2 d3 a0 61 31 30 47 fd  13 d1 5b 21 80 dc b4 be  |...a10G...[!....|
00000090  7f 82 16 01 41 b6 6e f4  be 3f 4c ad 0d 2d ea 2b  |....A.n..?L..-.+|
000000a0  22 57 f2 be 3f cf 16 a8  f0 b9 95 ce 31 6b 8a 45  |"W..?.......1k.E|
000000b0  c3 5c 4a ad 6a 81 45 c2  f6 e4 6d 13 7c 7f ff f7  |.\J.j.E...m.|...|
000000c0  9e 42 f1 6c 4c 11 a6 60  f1 3f 89 1f b6 06 1f 84  |.B.lL..`.?......|
000000d0  58 d3 81 07 56 7b 4f d6  86 46 04 6a e5 62 22 57  |X...V{O..F.j.b"W|
000000e0  e1 7b d6 1a 71 4e 64 54  69 a6 50 3c d9 6a 19 f0  |.{..qNdTi.P<.j..|
000000f0  1a de 76 fc 4c d7 d8 bf  7f 5f 9f b2 7c 26 ec 95  |..v.L...._..|&..|
00000100  30 43 2d cb 7e 03 24 26  74 ca 6a ee 1b b7 62 e8  |0C-.~.$&t.j...b.|
00000110  88 42 0f 8f 35 d1 eb d4  31 84 49 49 31 9c 62 ca  |.B..5...1.II1.b.|
00000120  c9 3b 9f 6c df 57 df 3f  2d 24 c9 5e 19 a7 d6 9c  |.;.l.W.?-$.^....|
00000130  0e e5 8f 0a b4 15 2d 88  00 0f 59 e3 df ca 97 a3  |......-...Y.....|
00000140  4d e2 a6 53 55 cf d4 7a  9f 85 73 15 b4 95 dd 03  |M..SU..z..s.....|
00000150  4f 62 52 a9 f9 d7 be 6c  85 fd 77 17 33 37 49 7b  |ObR....l..w.37I{|
00000160  7f 81 52 38 6f d6 50 28  0a cc 09 48 22 62 6a 90  |..R8o.P(...H"bj.|
00000170  78 d4 ca ff 40 12 3f e0  50 03 53 a1 82 c3 01 f6  |x...@.?.P.S.....|
00000180  b1 c5 fb 30 e5 38 6c 98  17 dd c7 c1 8a aa b4 a0  |...0.8l.........|
00000190  20 c7 ff 9b ea 92 d9 2c  80 4c 46 3a 4d 08 6b be  | ......,.LF:M.k.|
000001a0  68 3b a6 1e 3f 6d 42 26  3f 7f cd 14 fa 33 56 97  |h;..?mB&?....3V.|
000001b0  61 28 a2 11 6c 1a 1c 60  16 cb 5f 7f 42 34 00 fe  |a(..l..`.._.B4..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 53 03 00 fe  |............S...|
000001d0  ff ff 05 fe ff ff 02 e0  53 03 00 18 26 00 00 00  |........S...&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```


THANKS FOR HELPINGS

---

### Post by oldfred on 2010-09-14
You seem to be booting with grub legacy, but also have a grub.cfg from grub2.

Your windows boot/recovery partition is sda1 or hd0,0 in old grub and hd0,1 in grub2. You also have the boot flag on the sda2 partition but boot is sda1, but that will only matter if you are booting windows from the MBR.

Change this in /boot/grub/menu.lst

title Windows sda[COLOR=Red]1 [/COLOR]
rootnoverify (hd0,[COLOR=Red]0[/COLOR])
 chainloader +1
 boot

You also have the above stanza inside the automagic area. Next update will erase it.
Move it below the line that says end automagic. Or way up above the line that says start automagic.

---

### Post by techclown on 2010-09-14
applied changes but still restarts

---

### Post by Lawrence Talbot on 2010-09-14
I would just reinstall Ubuntu, which takes about 30 mintues, including updates.  That should correct any problems you have.  You have been at this for over an hour already so I guess it can't hurt much.  ):P

---

### Post by techclown on 2010-09-14
thanks anyway

---

### Post by wilee-nilee on 2010-09-14
> **techclown said:**
> thanks anyway

Just hang a bit your the person who gave you those commands post #4 is your best bet amongst a few others at getting you up and running. ;)

---

### Post by techclown on 2010-09-14
im still trying to figure iit out but i cant

---

### Post by techclown on 2010-09-14
for some reason i thought it was the same person!! lol so yea all it did was restart

---

### Post by oldfred on 2010-09-14
I thought your entry was ok with the correction. This is one I saved. It has no boot and savedefault, but I think the boot will not matter as it should jump after the chainload command and savedefault is just another option. 

title Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify (hd0,0)
savedefault
chainloader +1

If windows is not booting reinstalling Ubuntu will not fix windows. Did you use gparted to modify windows or use windows tools to resize the windows partition. You may need to use a windows CD and run chkdsk on the windows partitions sda1 & sda2.

---

### Post by techclown on 2010-09-16
Installed ubuntu again now again have grub2 heres boot info please help






```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   254,253,178   254,046,331   7 HPFS/NTFS
/dev/sda3         254,255,102   312,580,095    58,324,994   5 Extended
/dev/sda5         310,085,632   312,580,095     2,494,464  82 Linux swap / Solaris
/dev/sda6         254,255,104   307,689,471    53,434,368  83 Linux
/dev/sda7         307,691,520   310,071,295     2,379,776  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4E18C13618C11E39                       ntfs       System Reserved               
/dev/sda2        0288C4F888C4EAED                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3ea577ae-ad05-4cb4-8c4f-5f9b2fb3c140   swap                                     
/dev/sda6        474c85de-d729-41d3-b5ce-26b326a355f9   ext4                                     
/dev/sda7        0222f709-9696-432a-bd91-d827c99f31a4   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/DRIVER            iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/System_Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: grub/core.img

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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
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
search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=474c85de-d729-41d3-b5ce-26b326a355f9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=474c85de-d729-41d3-b5ce-26b326a355f9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 474c85de-d729-41d3-b5ce-26b326a355f9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4e18c13618c11e39
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0288c4f888c4eaed
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda6 :
UUID=474c85de-d729-41d3-b5ce-26b326a355f9	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=4E18C13618C11E39	/media/System_Reserved	ntfs-3g	defaults,locale=en_NZ.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=0288C4F888C4EAED	/media/sda2	ntfs-3g	defaults,locale=en_NZ.UTF-8	0	0
#Entry for /dev/sda7 :
UUID=0222f709-9696-432a-bd91-d827c99f31a4	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0



=================== sda6: Location of files loaded by Grub: ===================


 136.7GB: boot/grub/core.img
 154.0GB: boot/grub/grub.cfg
 136.7GB: boot/initrd.img-2.6.32-24-generic
 136.7GB: boot/vmlinuz-2.6.32-24-generic
 136.7GB: initrd.img
 136.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f7 bc 10 75 f5 6c 27 ea  b0 b5 93 92 23 90 92 2a  |...u.l'.....#..*|
00000010  25 50 12 4e d7 80 90 9c  f5 fc 12 4f f9 76 b2 4e  |%P.N.......O.v.N|
00000020  49 ba e0 0d 42 cd 18 28  69 3e 58 95 2c e8 19 f2  |I...B..(i>X.,...|
00000030  f1 01 fa 5d 68 b3 74 b7  19 d4 c0 f9 5c 5e 49 45  |...]h.t.....\^IE|
00000040  47 f9 35 1c da 2c 1d a1  34 83 0b 8e e0 66 9a 54  |G.5..,..4....f.T|
00000050  85 80 03 bf 83 ee b4 89  82 99 e9 95 ca 88 3e b8  |..............>.|
00000060  29 d5 ef 5d 4a d7 fe ac  7f b6 92 c9 80 4a 9d e6  |)..]J........J..|
00000070  c0 5d 49 d5 ee 4e 51 5d  c8 06 bc ad cb 03 95 bc  |.]I..NQ]........|
00000080  b2 d3 a0 61 31 30 47 fd  13 d1 5b 21 80 dc b4 be  |...a10G...[!....|
00000090  7f 82 16 01 41 b6 6e f4  be 3f 4c ad 0d 2d ea 2b  |....A.n..?L..-.+|
000000a0  22 57 f2 be 3f cf 16 a8  f0 b9 95 ce 31 6b 8a 45  |"W..?.......1k.E|
000000b0  c3 5c 4a ad 6a 81 45 c2  f6 e4 6d 13 7c 7f ff f7  |.\J.j.E...m.|...|
000000c0  9e 42 f1 6c 4c 11 a6 60  f1 3f 89 1f b6 06 1f 84  |.B.lL..`.?......|
000000d0  58 d3 81 07 56 7b 4f d6  86 46 04 6a e5 62 22 57  |X...V{O..F.j.b"W|
000000e0  e1 7b d6 1a 71 4e 64 54  69 a6 50 3c d9 6a 19 f0  |.{..qNdTi.P<.j..|
000000f0  1a de 76 fc 4c d7 d8 bf  7f 5f 9f b2 7c 26 ec 95  |..v.L...._..|&..|
00000100  30 43 2d cb 7e 03 24 26  74 ca 6a ee 1b b7 62 e8  |0C-.~.$&t.j...b.|
00000110  88 42 0f 8f 35 d1 eb d4  31 84 49 49 31 9c 62 ca  |.B..5...1.II1.b.|
00000120  c9 3b 9f 6c df 57 df 3f  2d 24 c9 5e 19 a7 d6 9c  |.;.l.W.?-$.^....|
00000130  0e e5 8f 0a b4 15 2d 88  00 0f 59 e3 df ca 97 a3  |......-...Y.....|
00000140  4d e2 a6 53 55 cf d4 7a  9f 85 73 15 b4 95 dd 03  |M..SU..z..s.....|
00000150  4f 62 52 a9 f9 d7 be 6c  85 fd 77 17 33 37 49 7b  |ObR....l..w.37I{|
00000160  7f 81 52 38 6f d6 50 28  0a cc 09 48 22 62 6a 90  |..R8o.P(...H"bj.|
00000170  78 d4 ca ff 40 12 3f e0  50 03 53 a1 82 c3 01 f6  |x...@.?.P.S.....|
00000180  b1 c5 fb 30 e5 38 6c 98  17 dd c7 c1 8a aa b4 a0  |...0.8l.........|
00000190  20 c7 ff 9b ea 92 d9 2c  80 4c 46 3a 4d 08 6b be  | ......,.LF:M.k.|
000001a0  68 3b a6 1e 3f 6d 42 26  3f 7f cd 14 fa 33 56 97  |h;..?mB&?....3V.|
000001b0  61 28 a2 11 6c 1a 1c 60  16 cb 5f 7f 42 34 00 df  |a(..l..`.._.B4..|
000001c0  d3 ff 82 df d3 ff 02 e8  53 03 00 10 26 00 00 fe  |........S...&...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 58 2f 03 00 00  |...........X/...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by techclown on 2010-09-16
bump plese help !!!

---

