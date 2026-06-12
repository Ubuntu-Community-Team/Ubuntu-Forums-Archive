---
title: "Problems loading Vista from Ubuntu"
date: 2010-06-29
forum: General Help
---

### Post by crazy_augusto on 2010-06-29
I installed Vista on my Acer 64-bit laptop first, then installed Ubuntu 9.10 in a dual-boot configuration.  And when I start up my computer, Windows Vista is an option in the Grub menu. But when I use the grub loader to load Vista all I see is a black screen, with a flashing underscore character (it looks a lot like a terminal screen, waiting for input). The screen just stays like this, too - I timed it once, and 13 minutes later it was the same.

Do any of you guys (or girls) know why this is happening? Any help would be greatly appreciated :)

---

### Post by johngreth on 2010-06-29
Ubuntu and Vista don't like each other. This should help: [http://ubuntuforums.org/showthread.php?t=828862](http://ubuntuforums.org/showthread.php?t=828862)

---

### Post by sandyd on 2010-06-29
> **crazy_augusto said:**
> I installed Vista on my Acer 64-bit laptop first, then installed Ubuntu 9.10 in a dual-boot configuration.  And when I start up my computer, Windows Vista is an option in the Grub menu. But when I use the grub loader to load Vista all I see is a black screen, with a flashing underscore character (it looks a lot like a terminal screen, waiting for input). The screen just stays like this, too - I timed it once, and 13 minutes later it was the same.

Do any of you guys (or girls) know why this is happening? Any help would be greatly appreciated :)
ooooh. I guess that means you fell into the trap of letting ubuntu resize the windows partition....

anyways. for future refrence, don't let ubuntu resize the partitions to create a dual boot...
follow the instructions here : [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows) (and yes, sorry if the guide is a bit messed, my english is terrible even though I was born in Canada.....)

and if you look a bit lower on the page, it will show you how to recover from this issue.

---

### Post by wilee-nilee on 2010-06-29
Post the bootscript in my signature in code tags as described. Without more information I wouldn't advise you its just guessing. If I was to guess you have grub in windows what you describe is a standard response.

It is possible that it is a resizing problem but no information is given that suggests this; no mention of the install partitioner or gparted.

---

### Post by crazy_augusto on 2010-06-29
About the partition, when I installed ubuntu I made a partition on my hard drive that gave around 100 gb of the 160 total on the disk to ubuntu.

But I did it in gparted.... I ran the vista reinstallation disc and hit "Repair my computer" and then "Repair startup issues", but the problem is still around. Would enlarging my Windows partition fix the problem?

---

### Post by wilee-nilee on 2010-06-29
Just to be sure here would you post the bootscript in my signature in code tags. To post with code tags follow my description in the signature, or highlight the txt in the reply of the readout of the script and click on the # in the panel. Enlarging the vista partition is not a good idea we want it working and both OS booting first.

Did you shrink Vista with gparted or the installer partitioner, or was it installed originally in a 40 gig partition?

---

### Post by oldfred on 2010-06-29
Resizing windows will not fix it. Did you just run the auto repair. That supposedly only fixes one thing at a time and you really need to run the command line repairs.

The boot script should tell us what is missing and then we may be able to suggest what to do.

---

### Post by crazy_augusto on 2010-06-30
> **wilee-nilee said:**
> Just to be sure here would you post the bootscript in my signature in code tags. To post with code tags follow my description in the signature, or highlight the txt in the reply of the readout of the script and click on the # in the panel. Enlarging the vista partition is not a good idea we want it working and both OS booting first.

Did you shrink Vista with gparted or the installer partitioner, or was it installed originally in a 40 gig partition?


[COLOR=Black]OK, OK, good to know. Here's what RESULTS.txt had to say[/COLOR]:


[COLOR=Blue]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 105503182 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

/dev/sda1    *          2,048   104,856,254   104,854,207   7 HPFS/NTFS
/dev/sda2         104,856,255   312,576,704   207,720,450   5 Extended
/dev/sda5         104,856,318   304,046,189   199,189,872  83 Linux
/dev/sda6         304,046,253   312,576,704     8,530,452  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7ECC5C93CC5C4793                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        93bc3be6-3977-4931-909b-9589e1c72f57   ext4                                     
/dev/sda6        bf7dbda0-57f3-46b3-a60a-f1b9c3455f46   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
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
search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=93bc3be6-3977-4931-909b-9589e1c72f57 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 93bc3be6-3977-4931-909b-9589e1c72f57
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7ecc5c93cc5c4793
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=93bc3be6-3977-4931-909b-9589e1c72f57 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bf7dbda0-57f3-46b3-a60a-f1b9c3455f46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  54.0GB: boot/grub/core.img
  58.6GB: boot/grub/grub.cfg
  54.4GB: boot/initrd.img-2.6.31-22-generic
  54.4GB: boot/initrd.img-2.6.32-22-generic
  54.4GB: boot/initrd.img-2.6.32-23-generic
  53.8GB: boot/vmlinuz-2.6.31-22-generic
 120.5GB: boot/vmlinuz-2.6.32-22-generic
  66.7GB: boot/vmlinuz-2.6.32-23-generic
  54.4GB: initrd.img
  54.4GB: initrd.img.old
  66.7GB: vmlinuz
 120.5GB: vmlinuz.old[/COLOR]


[COLOR=Black] Vista originally took up all my hard drive, then [/COLOR]I shrunk it using the Ubuntu installer.

---

### Post by wilee-nilee on 2010-06-30
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: [B]Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and[/B]
looks at sector 105503182 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

As I suspected you have the grub bootloader in the windows partition, follow this links instructions to remove it from sda1.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

In the future just so you know grub goes in the master boot record which would be sda in this case, no partition numbers.

---

### Post by wilee-nilee on 2010-06-30
So additionally, if the shrinking of Vista has caused problems after this process of getting grub out you can run a command from the command portion on that install dvd. You already know how to get to the startuprepair but instead of that choose the command prompt and run,
```
CHKDSK C: /F /R
```" (note: you can replace C: with any drive letter that you want to check).

---

### Post by crazy_augusto on 2010-06-30
> **wilee-nilee said:**
> So additionally, if the shrinking of Vista has caused problems after this process of getting grub out you can run a command from the command portion on that install dvd. You already know how to get to the startuprepair but instead of that choose the command prompt and run,
```
CHKDSK C: /F /R
```" (note: you can replace C: with any drive letter that you want to check).

I tried the testdisk utility, but according to the instructions I was supposed to get an option to 
"BackupBS" but it does not appear. Does this mean my problem lies elsewhere? Btw thanks for your continued help with this

---

### Post by wilee-nilee on 2010-06-30
> **crazy_augusto said:**
> I tried the testdisk utility, but according to the instructions I was supposed to get an option to 
"BackupBS" but it does not appear. Does this mean my problem lies elsewhere? Btw thanks for your continued help with this

So I haven't actually used testdisk myself but this is a standard method you can try again and follow the instructions or from the install dvd use the highlighted command to do the same thing I believe.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

