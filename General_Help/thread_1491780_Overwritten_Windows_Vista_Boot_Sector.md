---
title: "Overwritten Windows Vista Boot Sector"
date: 2010-05-24
forum: General Help
---

### Post by dukeofgp on 2010-05-24
Two days ago, I was very excited to upgrade my Ubuntu to 10.04. But, I made a mistake to install GRUB in all partitions. I have three bootable partitions: 1 recovery Partition (windows Vista), normal Windows Vista, and Ubuntu.

Now, after booting my notebook and the GRUB menu displayed, I select my Windows Vista and it can't boot to that partition and a cursor is blinking and nothing happen.

I have Windows Vista SP2. I tried to use an old Recovery Disk to boot and run bootrec /fixboot, it said it can't find an volume.

Would anyone help me?

Thanks.

---

### Post by bcbc on 2010-05-24
> **dukeofgp said:**
> Two days ago, I was very excited to upgrade my Ubuntu to 10.04. But, I made a mistake to install GRUB in all partitions. I have three bootable partitions: 1 recovery Partition (windows Vista), normal Windows Vista, and Ubuntu.

Now, after booting my notebook and the GRUB menu displayed, I select my Windows Vista and it can't boot to that partition and a cursor is blinking and nothing happen.

I have Windows Vista SP2. I tried to use an old Recovery Disk to boot and run bootrec /fixboot, it said it can't find an volume.

Would anyone help me?

Thanks.

Try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by wilee-nilee on 2010-05-24
If the testdisk approach doesn't work post this script in code tags. Really you should post it before doing anything.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dukeofgp on 2010-05-24
Thank you. Here is the results

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 240073198 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 240073198 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 240073198 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,467,712   166,793,215   146,325,504   6 FAT16
/dev/sda3         166,793,216   239,794,167    73,000,952   7 HPFS/NTFS
/dev/sda4         239,794,174   312,580,095    72,785,922   5 Extended
/dev/sda5         239,794,176   309,499,903    69,705,728  83 Linux
/dev/sda6         309,501,952   312,580,095     3,078,144  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BE2C1C84E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        E8FC9F99FC9F609C                       ntfs       ACER                          
/dev/sda3        54DA359BDA3579F6                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7b099623-5d1f-4867-8693-a983340dc9ea   ext4                                     
/dev/sda6        dd104d3d-2139-4c9f-9678-e1a06972e00d   swap                                     
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
search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
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
search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7b099623-5d1f-4867-8693-a983340dc9ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7b099623-5d1f-4867-8693-a983340dc9ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7b099623-5d1f-4867-8693-a983340dc9ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7b099623-5d1f-4867-8693-a983340dc9ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7b099623-5d1f-4867-8693-a983340dc9ea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be2c1c84e49bed2a
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e8fc9f99fc9f609c
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
UUID=7b099623-5d1f-4867-8693-a983340dc9ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dd104d3d-2139-4c9f-9678-e1a06972e00d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 155.1GB: boot/grub/core.img
 145.0GB: boot/grub/grub.cfg
 155.1GB: boot/initrd.img-2.6.32-21-generic
 155.4GB: boot/initrd.img-2.6.32-22-generic
 155.1GB: boot/vmlinuz-2.6.32-21-generic
 123.1GB: boot/vmlinuz-2.6.32-22-generic
 155.4GB: initrd.img
 155.1GB: initrd.img.old
 123.1GB: vmlinuz
 155.1GB: vmlinuz.old

How can I fix it?

Thanks again

---

### Post by bcbc on 2010-05-24
Click on the link I posted earlier. It describes the fix.

---

### Post by oldfred on 2010-05-24
Your sda2 is saying it is type 6 FAT, I did not think Vista even would run on a FAT partition, it should be NTFS. Testdisk may also fix that or sfdisk can change it but that has risks.

---

### Post by bcbc on 2010-05-24
> **oldfred said:**
> Your sda2 is saying it is type 6 FAT, I did not think Vista even would run on a FAT partition, it should be NTFS. Testdisk may also fix that or sfdisk can change it but that has risks.

I've seen other cases of this. fdisk says fat16 but blkid is showing ntfs. I believe testdisk also saw it as fat (from another case). But this seems highly unlikely!?

---

### Post by oldfred on 2010-05-24
bcbc you are correct. the listing of UUIDs which in the script uses blkid says ntfs. Very strange.

---

### Post by dukeofgp on 2010-05-24
Thank you all for your help. I changed the type back to NTFS and ran testdisk. It is fixed now.

---

### Post by dukeofgp on 2010-05-26
by the way, there is a hidden partition in my hard disk. How can I restore the boot sector to it?

---

### Post by bcbc on 2010-05-26
> **dukeofgp said:**
> by the way, there is a hidden partition in my hard disk. How can I restore the boot sector to it?
Doesn't testdisk work?

---

### Post by mumble83 on 2010-07-27
> **dukeofgp said:**
> Thank you all for your help. I changed the type back to NTFS and ran testdisk. It is fixed now.
Did you use sfdisk to set it back to NTFS?

---

