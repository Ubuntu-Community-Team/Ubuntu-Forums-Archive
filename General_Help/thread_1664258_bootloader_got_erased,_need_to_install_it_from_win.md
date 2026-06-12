---
title: "bootloader got erased, need to install it from windows side"
date: 2011-01-10
forum: General Help
---

### Post by nam42589 on 2011-01-10
I am new to ubuntu

I downloaded Ubuntu 10.4. Then I downloaded Windows 7 Pro. the bootloader got overwritten with windows 7. I cant get to the ubuntu side to do the whole sudo command to reinstall the bootloader because I do not have my ubuntu cd. Can someone please explain to me in detail how to install the bootloader from my windows side.

Thank you in advance

---

### Post by Quackers on 2011-01-10
Welcome to UF.
You will need an Ubuntu Live cd or usb to re-install grub. Don't you have the cd/usb that you used to install Ubuntu?

---

### Post by nam42589 on 2011-01-11
found the cd, i tried reinstalling it but i makes a new partition, i just want to write over the old one

---

### Post by Quackers on 2011-01-11
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nam42589 on 2011-01-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /menu.lst /boot.ini /Windows/System32/winload.exe 
                       /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 696324112 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   491,838,742   491,427,095   7 HPFS/NTFS
/dev/sda3         687,575,038   945,829,887   258,254,850   f W95 Ext d (LBA)
/dev/sda5         881,913,856   945,829,887    63,916,032   7 HPFS/NTFS
/dev/sda6         687,575,040   873,918,463   186,343,424  83 Linux
/dev/sda7         873,920,512   881,903,615     7,983,104  82 Linux swap / Solaris
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        802C2EE72C2ED844                       ntfs                                     
/dev/sda2        BA5832AA58326573                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        8C523F94523F81CE                       ntfs       LENOVO_PART                   
/dev/sda5        62808AA5808A7F73                       ntfs       LENOVO                        
/dev/sda6        4fce79c5-065b-42cc-96be-14bff3382e6d   ext4                                     
/dev/sda7        9615f6e9-80f1-49d6-96a0-8ee6f10a383f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/4fce79c5-065b-42cc-96be-14bff3382e6d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/BA5832AA58326573  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/LENOVO            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/802C2EE72C2ED844  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/menu.lst: ================================

ï»¿timeout 0 
default 0 
title grub2 
find --set-root /boot/grub/core.img 
kernel /boot/grub/core.img 
boot
================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=c:\grldr.mbr 
[operating systems] 
C:\grldr.mbr=&#148;Grub4Dos&#148;
=================== sda2: Location of files loaded by Grub: ===================


    ??GB: menu.lst

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
search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
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
search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=4fce79c5-065b-42cc-96be-14bff3382e6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=4fce79c5-065b-42cc-96be-14bff3382e6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4fce79c5-065b-42cc-96be-14bff3382e6d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4fce79c5-065b-42cc-96be-14bff3382e6d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 4fce79c5-065b-42cc-96be-14bff3382e6d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 802c2ee72c2ed844
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 8c523f94523f81ce
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
UUID=4fce79c5-065b-42cc-96be-14bff3382e6d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9615f6e9-80f1-49d6-96a0-8ee6f10a383f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 356.5GB: boot/grub/core.img
 429.5GB: boot/grub/grub.cfg
 356.5GB: boot/grub/stage2
 356.5GB: boot/initrd.img-2.6.32-24-generic
 356.5GB: boot/initrd.img-2.6.32-27-generic
 356.6GB: boot/vmlinuz-2.6.32-24-generic
 356.6GB: boot/vmlinuz-2.6.32-27-generic
 356.5GB: initrd.img
 356.5GB: initrd.img.old
 356.6GB: vmlinuz
 356.6GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-11
So Windows 7 still boots?
With a wubi loader, a grub legacy boot file and a Windows XP boot file in the same partition with the third Windows 7 boot file, that's amazing!

It may be worth waiting to see what other users think of what I'm suggesting here, but I would suggest that you re-install grub from the live cd desktop, but ONLY if Windows is booting normally now!
To install grub to the mbr of sda you should run these commands in the terminal from the live cd desktop.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then try rebooting and see what happens :-)

It may be necessary to purge/re-install frub, as you seem to have bits all over the place, but we'll see.

---

### Post by bodhi.zazen on 2011-01-11
See also:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It is a bit messy, but it covers the issues. You can skip the information on grub versions (grub legacy vs gru2) as you are using grub2.

---

