---
title: "XP won't boot after upgrading to 10.04"
date: 2010-07-05
forum: General Help
---

### Post by riccopt on 2010-07-05
I have 2 HDDs on my computer on one I have Ubuntu and on the other I have Windows XP Home Edition, but after I have done the upgrade on the Ubuntu, windows XP won't boot... 
even if I disconnect the HDD (power and data) where Ubuntu is installed... any idea what could be causing this problem?

it gives me some GRUB ERROR (I didn't try to boot on windows with both HDDs connected as I only have 2 power cables and I need to use my DVD recorder on Windows)

I have seen similar topics about this, but couldn't understand most of what was posted on them...

---

### Post by wilee-nilee on 2010-07-05
Post the bootscript in my signature in code tags as suggested.

---

### Post by riccopt on 2010-07-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 535942464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 535942464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 535942464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   535,671,359   535,655,295   f W95 Ext d (LBA)
/dev/sdb5              16,128   529,711,244   529,695,117   7 HPFS/NTFS
/dev/sdb6         529,711,308   535,671,359     5,960,052  82 Linux swap / Solaris
/dev/sdb2         535,671,360   781,417,664   245,746,305  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1CB8DBF6B8DBCD00                       ntfs       160_Windows                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        11d452d0-a075-4653-99e5-b690506e966d   ext4                                     
/dev/sdb5        01CA94E8FFABC090                       ntfs       271_NTFS                      
/dev/sdb6        6480c3eb-81cd-4d38-a510-4d6b6df65ab8   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/160_Windows       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/271_NTFS          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=11d452d0-a075-4653-99e5-b690506e966d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 11d452d0-a075-4653-99e5-b690506e966d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1cb8dbf6b8dbcd00
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=11d452d0-a075-4653-99e5-b690506e966d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6480c3eb-81cd-4d38-a510-4d6b6df65ab8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 274.4GB: boot/grub/core.img
 280.3GB: boot/grub/grub.cfg
 291.3GB: boot/initrd.img-2.6.31-22-generic
 291.5GB: boot/initrd.img-2.6.32-22-generic
 287.2GB: boot/initrd.img-2.6.32-23-generic
 275.3GB: boot/vmlinuz-2.6.31-22-generic
 289.3GB: boot/vmlinuz-2.6.32-22-generic
 296.7GB: boot/vmlinuz-2.6.32-23-generic
 287.2GB: initrd.img
 291.5GB: initrd.img.old
 296.7GB: vmlinuz
 289.3GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-07-05
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: ** Grub 2 is installed in the boot sector of sda1 and **
                       looks at sector 535942464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

You have grub in the windows boot. use this link to clean it out just follow the instructions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

sda is the master boot record the first 512mb of the hard drive and where grub only goes. Same would be for sdb where Ubuntu actually is no numbers no partitions.

Just try the link and then see how it boots.

---

### Post by riccopt on 2010-07-05
I will try to reboot and see what goes on...

---

### Post by riccopt on 2010-07-05
the problem is solved... but now the black screen with the blinking cursor takes a lot longer to pass...

how do I mark the topic as solved?

---

### Post by wilee-nilee on 2010-07-05
> **riccopt said:**
> the problem is solved... but now the black screen with the blinking cursor **takes a lot longer to pass...**

how do I mark the topic as solved?

Solved is in thread tools.

Can you define how long; longer to pass is, in seconds?

You have grub installed in two HD and sda is probably first. Can you run ```
sudo update-grub
``` in Ubuntu and put sdb first to be read from bios, this should fix any long delay.

Is sdb a external HD?

---

### Post by riccopt on 2010-07-05
> **wilee-nilee said:**
> Solved is in thread tools.

Can you define how long; longer to pass is, in seconds?

You have grub installed in two HD and sda is probably first. Can you run ```
sudo update-grub
``` in Ubuntu and put sdb first to be read from bios, this should fix any long delay.

Is sdb a external HD?
no, both drives are internal... the screen used to pass by and now it is taking around 5s... nothing that bugs me... maybe that happened also because it was the 1st time I was booting the PC with the new configuration...
I already run that sudo command so "clear" grub...
thanks for the awesome support you have provided to me!

---

### Post by wilee-nilee on 2010-07-05
> **riccopt said:**
> no, both drives are internal... the screen used to pass by and now it is taking around 5s... nothing that bugs me... maybe that happened also because it was the 1st time I was booting the PC with the new configuration...
I already run that sudo command so "clear" grub...
thanks for the awesome support you have provided to me!

There is a auto 10 second pause for grub choice, I could only speculate about any other time outs. In the future since you don't have a XP disc download this legit one, you could reload the XP bootloader in sda if you wanted to and other repairs.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

This is a slipsteamed sp3 full XP haome install disc, best used for repairs beyond reloading a acer computer.

---

