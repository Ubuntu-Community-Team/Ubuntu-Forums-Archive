---
title: "Grub can't dual-boot after upgrade"
date: 2010-05-15
forum: General Help
---

### Post by Bob_I on 2010-05-15
I have a system dual booting Ubuntu with XP.  Up to upgrade to Lucid, grub worked fine, but now any attempt to use the grub menu to move to XP gives only another grub menu.  I need to use XP once in a while.  How do I resolve this?
   Bob_I

---

### Post by ryan858 on 2010-05-15
You should check over your grub config files... Now there's a catch to this:

If you're using *Grub Legacy*, then you should just have a */boot/grub/grub.conf*

If you have* Grub2*, then it's a bit more complicated... With Grub2 you have the following configuration files:

[I]/boot/grub/grub.cfg
/etc/default/grub

[/I]**/etc/grub.d/:** [I]
/etc/grub.d/00_header
/etc/grub.d/05_debian_theme
/etc/grub.d/10_linux
/etc/grub.d/20_memtest86+
/etc/grub.d/30_os-prober
/etc/grub.d/40_custom[/I]

All of them except */etc/default/grub* are basically shell scripts, and probably shouldn't be edited unless you know what you're doing, and know a bit about shell scripting. **Especially, don't mess with grub.cfg unless you really know everything about how it works. If there's one misspelled word or one letter or number off in the wrong place, you will FUBAR your installation.**

Editing the */etc/grub.d*/ files and */etc/default/grub* are pretty safe though because there is a command called *update-grub* that will check over all the config files and make sure they have no errors in them, then compile them into */boot/grub/grub.cfg* which is read during boot. If you're going to change anything you should use the config files rather than directly editing grub.cfg, unless you are absolutely sure you know what you're doing.

If you can post a copy of your */boot/grub/grub.cfg* or */boot/grub/grub.conf* then we can check over it and see if there's anything wrong with it.

---

### Post by oldfred on 2010-05-15
when you upgraded did you check off all the drives (and partitions) to install grub to? If you did you overwrote the windows boot sector.

Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by ryan858 on 2010-05-15
> **oldfred said:**
> when you upgraded did you check off all the drives (and partitions) to install grub to? If you did you overwrote the windows boot sector.

Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

:confused: 

I was under the impression he was wanting to use Grub as the bootloader, not the Windows bootloader... If that's the case, then you are *supposed to* overwrite the windows bootloader.

I thought his problem was that he couldn't select Win XP from Grub.

Am I correct?

---

### Post by Flangeman on 2010-05-16
Hi,

I have the same problem as Bob I have XP on a separate hard drive. When Grub loads XP is shown as an available operating system. If I select XP grub seems to begin, the screen goes blank for a short time and then I end up back at the initial grub screen to select the operating system.

If I select Ubuntu everything works fine

Cheers

---

### Post by oldfred on 2010-05-16
Grub goes into the MBR which is the drive boot loader and where everything starts. This is the first sector on a hard drive and is not part of any partition.

But windows has its part two in the partition boot record (PBR) or boot sector. This is the first sector of a partition and is not used except for booting. Also when grub chainloads to windows it just jumps to the windows PBR to boot windows.

Some have many operating systems and install one boot loader to the MBR and each operating system's boot loader to the PBR of that system and chainboot all the others from the first. Grub2 does not like to be installed to a PBR - something about blocklists and less reliable, but old grub works just fine in a PBR.

So if you overwrite the windows boot loader in the windows PBR - boot sector then windows will not boot.

 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Flangeman on 2010-05-17
It looks like I have overwritten the XP boot sector:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 272495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 272495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   156,248,189   156,135,735   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   150,288,074   150,288,012  83 Linux
/dev/sdb2         150,288,075   156,296,384     6,008,310   5 Extended
/dev/sdb5         150,288,138   156,296,384     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-021B                              vfat       DellUtility                   
/dev/sda2        828CC9178CC9069F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9b375680-47f1-4c27-9159-c163c6097ef2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d0352853-c17e-4306-bb45-a76be3661563   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9b375680-47f1-4c27-9159-c163c6097ef2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9b375680-47f1-4c27-9159-c163c6097ef2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=9b375680-47f1-4c27-9159-c163c6097ef2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=9b375680-47f1-4c27-9159-c163c6097ef2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b375680-47f1-4c27-9159-c163c6097ef2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-021b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 828cc9178cc9069f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=9b375680-47f1-4c27-9159-c163c6097ef2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d0352853-c17e-4306-bb45-a76be3661563 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   2.8GB: boot/grub/grub.cfg
  12.4GB: boot/initrd.img-2.6.31-21-generic
  14.7GB: boot/initrd.img-2.6.32-22-generic
   9.3GB: boot/vmlinuz-2.6.31-21-generic
  10.3GB: boot/vmlinuz-2.6.32-22-generic
  14.7GB: initrd.img
  12.4GB: initrd.img.old
  10.3GB: vmlinuz
   9.3GB: vmlinuz.old

---

### Post by oldfred on 2010-05-17
Either grub reports the wrong drive or the script parses grub incorrectly as the first entry saying same drive partition #1 is wrong, but I bet it works. On my computer I have 3 drives with Lucid in sdc7, but the grub 1.98 in sda says same drive partition #7 (my sda only has 3 partitions)

But the fix for windows is in post #3. All the other grubs in other partitions do not really matter as the PBR (partition first sector) is not normally used.

---

### Post by Bob_I on 2010-05-17
OK.  Here is my /boot/grub/grub.cfg file:

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcce487-02fa-43a6-8bd7-ca8bec305f66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1bcce487-02fa-43a6-8bd7-ca8bec305f66 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 268402e98402bb77
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 1497-4c10
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)


        search --no-floppy --fs-uuid --set ae18f79918f75f31
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

There is no "/boot/grub/grub.conf"

Is there a way to get the "old" grub to work on this system?  Otherwise I will have to trash Lucid and re-install Karmic.

Bob I

---

### Post by oldfred on 2010-05-17
Old grub will not boot windows if windows is damaged. Did you run the fix from post #3? That usually solves it.

Old grub had menu.lst and grub2 uses grub.cfg. Your grub.cfg was already listed (as would any menu.lst if you had them) in the results.txt from the boot info script. 

It is a lot easier if you use the code tags. They preserve formating and put the entry in a scroll box for ease of reviewing. You highlight and click on the # in the edit panel as you are pasting. (put mouse over # and it explains what it does).

---

### Post by Bob_I on 2010-05-17
Friends:
   Please forgive me.  Ignore the above post.  I did it from another machine, one that is still running Karmic.  I am now on a machine running Lucid, and will attempt to show you the /boot/grub/grub.cfg file.

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
search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
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
search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1db07eda-0e7d-4970-9d45-7f37a69992c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1db07eda-0e7d-4970-9d45-7f37a69992c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1db07eda-0e7d-4970-9d45-7f37a69992c3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1db07eda-0e7d-4970-9d45-7f37a69992c3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1db07eda-0e7d-4970-9d45-7f37a69992c3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9c9439359439136e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


I'm sorry, but I can't make much sense of the code above.  I hope someone can help or else I will go back to Karmic.
   Bob I

---

### Post by oldfred on 2010-05-17
This was from Flangeman which does confuse the issue. We want the results.txt not config.sys. And we want it in code tags. Your posts get too long to scroll thru.

If you get an entry like this in your windows partition then you need to run the fix in post #3.

File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 272495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

---

### Post by Bob_I on 2010-05-17
OK.  Post #3 gave me the fix, and I can now dual boot again.  So any ideas what happened?  Why did upgrading to Lucid trash my XP boot sector?  I think that there is a major bug here somewhere.
   Bob_I

---

### Post by Flangeman on 2010-05-18
Apologies for hijacking the thread!
The solution from post #3 worked, many thanks.
I now remember installing grub on both drives, which shows me not to mess with things without proper research

Cheers

---

### Post by oldfred on 2010-05-18
It is not a software bug per se, but the instructions assume you know the difference between a drive sda and a partition sda1 which many do not.

If you would go out and sign up and add your's to the bug list it would help.  We have seen many with this problem and only a few have signed up.
Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

