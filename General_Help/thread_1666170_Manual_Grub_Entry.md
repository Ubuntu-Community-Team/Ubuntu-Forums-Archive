---
title: "Manual Grub Entry"
date: 2011-01-13
forum: General Help
---

### Post by _Mark_ on 2011-01-13
Hi
I have added a manual entry to /etc/grub.d/40_custom and ran update-grub and the entry is added to /boot/grub/grub.cfg OK

But when booting the entry is not appearing :confused:

Has anyone come across this before as am a bit stumped trouble shooting this as there are no errors

Thanks

---

### Post by Quackers on 2011-01-13
Have a look at item number 14 in this guide by drs305, just to check what you've done 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by _Mark_ on 2011-01-13
Ye I have I looked at this thread by the same person [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Basically add the entry, update-grub and voila, to be honest I'm not sure the entry is 100% correct but that shouldn't stop it appearing especially as it is written to grub.cfg correctly

Weird

---

### Post by Quackers on 2011-01-13
I haven't done this addition myself, but I would imagine that the entry has to EXACTLY match what drs305 quotes (except for the different drive/partition number) for it to work.

---

### Post by ajgreeny on 2011-01-13
Is it possible that you have more than one linux with more than one grub2 and you are trying to edit the wrong one, ie a grub2 menu that is actually from a different OS to the one you are editing?

It should be obvious, I agree, as the default OS to which the system boots will be the OS that has the active grub2 configuration files.

---

### Post by Quackers on 2011-01-13
An excellent point! I have fallen foul of that myself :-)

---

### Post by _Mark_ on 2011-01-13
> **Quackers said:**
> I haven't done this addition myself, but I would imagine that the entry has to EXACTLY match what drs305 quotes (except for the different drive/partition number) for it to work.
It does see below the contents of 40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Wary (on sdb1)"{ 
set root=(hd1,1) 
linux /vmlinuz pmedia=usbhd
initrd /initrd.gz 
} 
EOF

```

and here is the entry in grub.cfg

```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Wary (on sdb1)"{ 
set root=(hd1,1) 
linux /vmlinuz pmedia=usbhd
initrd /initrd.gz 
} 
EOF
```

As I said the entry may not be 100% correct but that shouldn't stop it appearing on boot should it?

> **ajgreeny said:**
> Is it possible that you have more than one linux with more than one grub2 and you are trying to edit the wrong one, ie a grub2 menu that is actually from a different OS to the one you are editing?

It should be obvious, I agree, as the default OS to which the system boots will be the OS that has the active grub2 configuration files.

Thanks for the idea I do have several partitions with another *nix but I have double checked and I am using the correct grub
Edit:
the only complication is it is on a USB HD but again I can't see that stopping it appearing

---

### Post by oldfred on 2011-01-13
If you have lots of systems & then lots of entries in grub's menu, you can have more entires than the display box can show. If there is a tiny arrow on the right side it means there are more entries and you have to scroll down to see the last one's.

---

### Post by _Mark_ on 2011-01-13
> **oldfred said:**
> If you have lots of systems & then lots of entries in grub's menu, you can have more entires than the display box can show. If there is a tiny arrow on the right side it means there are more entries and you have to scroll down to see the last one's.

I only have about 8 entries it's definitely not hiding but thanks for the reply :)

I even renamed it to 06_custom so it should be at the top but no dice

---

### Post by oldfred on 2011-01-13
Just so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by _Mark_ on 2011-01-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 280569419 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 334513819 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    61,850,249    61,850,187   7 HPFS/NTFS
/dev/sda2         471,592,800   488,391,119    16,798,320  12 Compaq diagnostics
/dev/sda3         204,796,620   471,588,074   266,791,455   5 Extended
/dev/sda5    *    204,796,683   331,774,379   126,977,697  83 Linux
/dev/sda6         331,774,443   458,752,139   126,977,697  83 Linux
/dev/sda7         458,752,203   471,588,074    12,835,872  82 Linux swap / Solaris
/dev/sda4          61,850,250   204,796,619   142,946,370  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4A5C16565C163D5F                       ntfs       Win                           
/dev/sda2        2455-E940                              vfat       SERVICEV001                   
/dev/sda3: PTTYPE="dos" 
/dev/sda4        3b333693-e5ee-4cdf-8694-216466ee1594   ext3       Data                          
/dev/sda5        56b4b4cc-161b-4251-b820-b6f099e33e35   ext4       Ubuntu                        
/dev/sda6        70a7f403-a8a9-471a-afc5-472812f8324f   ext3       BackTrack                     
/dev/sda7        31953d15-f2e7-4c12-b1c5-68f7e3908a14   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9d28a6b3-7cda-46e4-b38f-e9fc0a1e4e65   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/9d28a6b3-7cda-46e4-b38f-e9fc0a1e4e65 ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\ 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\ = "PC-DOS" 

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
search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
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
search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
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
search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
insmod tga
if background_image /usr/share/images/desktop-base/Apollo.tga ; then
  set color_normal=white/black
  set color_highlight=black/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=1024x768
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=1024x768
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 56b4b4cc-161b-4251-b820-b6f099e33e35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4a5c16565c163d5f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2455-e940
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 70a7f403-a8a9-471a-afc5-472812f8324f
    linux /boot/vmlinuz-2.6.35.8 root=UUID=70a7f403-a8a9-471a-afc5-472812f8324f ro quiet vga=0x317
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 70a7f403-a8a9-471a-afc5-472812f8324f
    linux /boot/vmlinuz-2.6.35.8 root=UUID=70a7f403-a8a9-471a-afc5-472812f8324f ro single
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 70a7f403-a8a9-471a-afc5-472812f8324f
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Wary (on sdb1)"{ 
set root=(hd1,1) 
linux /vmlinuz pmedia=usbhd
initrd /initrd.gz 
} 
EOF


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
UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=31953d15-f2e7-4c12-b1c5-68f7e3908a14 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 143.6GB: boot/grub/core.img
 152.4GB: boot/grub/grub.cfg
 144.4GB: boot/initrd.img-2.6.32-27-generic
 144.0GB: boot/vmlinuz-2.6.32-27-generic
 144.4GB: initrd.img
 144.0GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=70a7f403-a8a9-471a-afc5-472812f8324f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=70a7f403-a8a9-471a-afc5-472812f8324f

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

vga=0x317image=70a7f403-a8a9-471a-afc5-472812f8324f/boot/grub/vga=0x317.xpm.gz

title        BackTrack 4 R2, kernel 2.6.35.8
uuid        70a7f403-a8a9-471a-afc5-472812f8324f
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=70a7f403-a8a9-471a-afc5-472812f8324f ro quiet vga=0x317 
initrd        /boot/initrd.img-2.6.35.8
quiet

title        BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid        70a7f403-a8a9-471a-afc5-472812f8324f
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=70a7f403-a8a9-471a-afc5-472812f8324f ro  single
initrd        /boot/initrd.img-2.6.35.8

title        BackTrack 4 R2, memtest86+
uuid        70a7f403-a8a9-471a-afc5-472812f8324f
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
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro quiet vga=0x317 
initrd        /boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro single 
initrd        /boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro quiet vga=0x317 
initrd        /boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=56b4b4cc-161b-4251-b820-b6f099e33e35 ro single 
initrd        /boot/initrd.img-2.6.32-25-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=70a7f403-a8a9-471a-afc5-472812f8324f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=31953d15-f2e7-4c12-b1c5-68f7e3908a14 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 171.3GB: boot/grub/menu.lst
 171.2GB: boot/grub/stage2
 171.8GB: boot/initrd.img-2.6.35.8
 171.3GB: boot/vmlinuz-2.6.35.8
 171.8GB: initrd.img
 171.3GB: vmlinuz

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: initrd.gz
    .1GB: vmlinuz

```

---

### Post by tredegar on 2011-01-13
```
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  [COLOR="Green"]Grub 2[/COLOR]
    Boot sector info:  Grub 2 is installed in the boot sector of [COLOR="Red"]sda5[/COLOR] and 
                       looks at sector 280569419 of the same hard drive for 
                       core.img, [COLOR="Red"]but core.img can not be found at this 
                       location.[/COLOR]

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector info:  [COLOR="Green"]Grub 0.97[/COLOR] is installed in the boot sector of [COLOR="Red"]sda6[/COLOR] and 
                       looks at sector 334513819 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

```
Looks like you have several grubs, "legacy", and grub2 and you are configuring the wrong one, from the wrong distro. grub "legacy" and grub2 can fight.

Choose the distro you want to update grub from. REMEMBER this. Write it down. Boot to it, then, edit the config files. Then, for grub2:
```
sudo grub-install /dev/sda
sudo update-grub
sudo reboot
```

---

### Post by ajgreeny on 2011-01-13
What I see here, which is a bit worrying is the text in red below, though I'm not sure if this is a result of the **custom** file you have made.:-
```
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 280569419 of the same hard drive for 
                       core.img, [COLOR=Red]but core.img can not be found at this 
                       location.[/COLOR]
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

---

### Post by _Mark_ on 2011-01-13
No I am definitely using the correct grub from the correct distro I am booting from sda5 10.04 with grub2 as you can see my custom entry is in the grub.cfg of sda5 

the core.img error has always been there i think from running the bootinfo script in the past, and the /boot/grub/core.img is there so not sure on that one. It has never caused a booting problem now or in the past

---

### Post by oldfred on 2011-01-13
Having grub in a partition boot sector is not a problem unless you are using it and it is not configured correctly. The grub legacy entry looks like you could chainload from grub2 to old grub to load backtrack if you wanted. Grub2 in the boot sector is not recommended, but it is not easy to remove, so it is ok if not used.

It looks like the entry for sdb is there. Are you sure you tried scrolling all the way down on the menu?

---

### Post by _Mark_ on 2011-01-13
> **oldfred said:**
> Having grub in a partition boot sector is not a problem unless you are using it and it is not configured correctly. The grub legacy entry looks like you could chainload from grub2 to old grub to load backtrack if you wanted. Grub2 in the boot sector is not recommended, but it is not easy to remove, so it is ok if not used.

It looks like the entry for sdb is there. Are you sure you tried scrolling all the way down on the menu?

Ye sure have give me some credit :D
I have found a [THREAD]("http://ubuntuforums.org/showthread.php?t=1640995&highlight=missing+grub+entries") where someone had a similar problem, although not a manual entry
I have sent a PM to the OP to see if he ever resolved it

---

### Post by _Mark_ on 2011-01-14
Well I fixed it :D

For info what I did removed my entry in 40_custom ran update-grub to remove entry from grub.cfg, added my entry back into 40_custom and grub.cfg and didn't run update-grub.

rebooted and voila the entry was there after a tweak or 2 it booted fine, just to test booted back to buntu and ran update-grub and the entry still there and booting fine

Possibly a bug in update-grub? who knows
Thanks for all the replies guys much appreciated

---

### Post by _Mark_ on 2011-01-14
Well I fixed it :D

For info what I did removed my entry in 40_custom ran update-grub to remove entry from grub.cfg, added my entry back into 40_custom and grub.cfg and didn't run update-grub.

rebooted and voila the entry was there after a tweak or 2 it booted fine, just to test booted back to buntu and ran update-grub and the entry still there and booting fine

Possibly a bug in update-grub? who knows
Thanks for all the replies guys much appreciated

---

### Post by _Mark_ on 2011-01-14
Well I fixed it :D

For info what I did removed my entry in 40_custom ran update-grub to remove entry from grub.cfg, added my entry back into 40_custom and grub.cfg and didn't run update-grub.

rebooted and voila the entry was there after a tweak or 2 it booted fine, just to test booted back to buntu and ran update-grub and the entry still there and booting fine

Possibly a bug in update-grub? who knows
Thanks for all the replies guys much appreciated

---

### Post by _Mark_ on 2011-01-14
Well I fixed it :D

For info what I did removed my entry in 40_custom ran update-grub to remove entry from grub.cfg, added my entry back into 40_custom and grub.cfg and didn't run update-grub.

rebooted and voila the entry was there after a tweak or 2 it booted fine, just to test booted back to buntu and ran update-grub and the entry still there and booting fine

Possibly a bug in update-grub? who knows
Thanks for all the replies guys much appreciated

---

### Post by _Mark_ on 2011-01-14
Well I fixed it :D

For info what I did removed my entry in 40_custom ran update-grub to remove entry from grub.cfg, added my entry back into 40_custom and grub.cfg and didn't run update-grub.

rebooted and voila the entry was there after a tweak or 2 it booted fine, just to test booted back to buntu and ran update-grub and the entry still there and booting fine

Possibly a bug in update-grub? who knows
Thanks for all the replies guys much appreciated

---

### Post by tredegar on 2011-01-14
Sounds like there was a problem with your **40_custom**

Are you aware that grub2 fails (well, that was the case a year ago) if there are _any_ lines in that file that have even a single trailing space (ie a space at the end of the line) ?

Might be worth checking for that.

---

### Post by _Mark_ on 2011-01-15
> **tredegar said:**
> Sounds like there was a problem with your **40_custom**

Are you aware that grub2 fails (well, that was the case a year ago) if there are _any_ lines in that file that have even a single trailing space (ie a space at the end of the line) ?

Might be worth checking for that.

I think after playing a bit more you are correct I think after copying and pasting did not put in a carriage return on the last line

---

