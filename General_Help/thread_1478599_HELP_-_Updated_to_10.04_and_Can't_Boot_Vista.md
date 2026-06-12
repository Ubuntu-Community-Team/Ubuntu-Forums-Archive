---
title: "HELP - Updated to 10.04 and Can't Boot Vista"
date: 2010-05-09
forum: General Help
---

### Post by bluec10 on 2010-05-09
Yesterday I updated to Ubuntu 10.04.  I had a nice dual boot system going with Ubuntu and Windows Vista.  After the update I can't boot Vista anymore - and I really need it!

I don't know much about Grub, but I know enough about computers to edit config files etc.  What settings should I punch into grub.cfg to get Vista to boot properly?

---

### Post by James78 on 2010-05-09
Well, you could start with trying to reconfigure grub.

sudo update-grub, will regenerate the configuration, OS prober should find Vista for you and configure the right options too boot to it. Let me know if that one doesn't work. If it doesn't, then it's likely there is a larger issue that will have to be worked with, such as the Master Boot Record.

---

### Post by bluec10 on 2010-05-09
> **James78 said:**
> Well, you could start with trying to reconfigure grub.

sudo update-grub, will regenerate the configuration, OS prober should find Vista for you and configure the right options too boot to it. Let me know if that one doesn't work. If it doesn't, then it's likely there is a larger issue that will have to be worked with, such as the Master Boot Record.

I ran the os prober and sudo update-grub, but it didn't help - same results.

---

### Post by bluec10 on 2010-05-09
I ran the boot info script and got the results below.  Hope some kind soul has a chance to take a look at it for me.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1741077127 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1741080223 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 1741089927 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1741084831 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 1741085831 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,466,810   498,898,574   478,431,765   6 FAT16
/dev/sda3         498,898,575   976,768,064   477,869,490   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   819,202,047   819,200,000   7 HPFS/NTFS
/dev/sdb2         819,202,048 1,740,802,047   921,600,000   7 HPFS/NTFS
/dev/sdb3       1,740,803,400 1,953,520,064   212,716,665   5 Extended
/dev/sdb5       1,740,803,463 1,944,780,704   203,977,242  83 Linux
/dev/sdb6       1,944,780,768 1,953,520,064     8,739,297  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4258414916D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        44F07983F0797C4C                       ntfs       ACER                          
/dev/sda3        9604926A04924CDD                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1CEC16E4EC16B84A                       ntfs       EXTRA1                        
/dev/sdb2        F8AACB07AACAC0FC                       ntfs       EXTRA2                        
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        8cd32353-f771-4ba3-84e9-ddfa844b4851   ext4                                     
/dev/sdb6        3346ac43-4359-4629-9a80-bbe24ef7ad68   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=kerry)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="10"
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 8cd32353-f771-4ba3-84e9-ddfa844b4851
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4258414916d9b5d2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 44f07983f0797c4c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=8cd32353-f771-4ba3-84e9-ddfa844b4851 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=3346ac43-4359-4629-9a80-bbe24ef7ad68 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 891.4GB: boot/grub/core.img
 897.8GB: boot/grub/grub.cfg
 894.9GB: boot/initrd.img-2.6.31-14-generic
 894.9GB: boot/initrd.img-2.6.31-20-generic
 894.9GB: boot/initrd.img-2.6.31-21-generic
 894.9GB: boot/initrd.img-2.6.32-22-generic
 891.4GB: boot/vmlinuz-2.6.31-14-generic
 891.5GB: boot/vmlinuz-2.6.31-20-generic
 892.1GB: boot/vmlinuz-2.6.31-21-generic
 893.4GB: boot/vmlinuz-2.6.32-22-generic
 894.9GB: initrd.img
 894.9GB: initrd.img.old
 893.4GB: vmlinuz
 892.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by James78 on 2010-05-09
Anyways, next thing would most likely be to reinstall grub. I assume you're using Grub2 (default for Karmic and Lucid)?

How're your hard drives configured as far as master and slave go? For example, I have /dev/sda as Windows, and /dev/sdb as Linux.

It is likely that Grub may have overwritten something on the MBR or Windows boot partition that it shouldn't have, but this can most likely be easily fixed.

I hope you have a Windows Vista install disk, because the MBR utilities on it will be useful to restore any Windows MBR/Boot damage, and it might also be the only way it can be fixed, which might be the case here why it's not booting.

Seeing your log above, it looks like your best guess is to go use the Vista CD/USB. Automatic repair may fix the startup, there's an option to automatically fix startup issues. If that doesn't work, you can open the command line from the CD and use the bootrec tool to fixboot.

---

### Post by bukwirm on 2010-05-09
What happens when you try to boot into Vista? Error message?

---

### Post by YossiB on 2010-05-10
Hi,

I am running into the same problem - also updated to 10.04 - and now can't boot to Vista.

I am just getting a blank screen and no progress when I try to boot vista.

I've also tried to update grub. and I can paste my boot info script results if it's helpful for anyone to solve this issue.


Yossi.

---

### Post by shaneg-nz on 2010-05-10
Same for me.. except my bootloader was a windows one.. so couldnt do anything.

i just wiped Kubuntu and re-installed off a live-cd.
tried to go into windows off the new grub2... no go

tried to go in off vmware... no go

---

### Post by James78 on 2010-05-10
If you have the setup disk, boot into it and run automatic repair (Vista onward only unfortunately). If that didn't work or it didn't find any problems, then click the partition when it comes up, click next, then click command line, and use 'bootrec /fixboot' to fix it.

---

### Post by wilee-nilee on 2010-05-10
1st if your not the thread starter, start your own thread and post the boot script in code tags, which means highlighting the text and clicking on the # in the posting gui.

Now thread starter either edit your bootscipt into code tags, or paste it in to a new reply highlight it and hit the # in the top panel you paste into.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Everybody having a problem with booting is going to be a mix of slightly if not very different situation. So don't just try to fix, or suggest if you are not sure that the method will work. There are plenty of people on the UF that know exactly what to do.

---

### Post by James78 on 2010-05-10
The Vista automatic repair DOES not edit Linux partitions in anyway. It detects the right Windows installation, and if it doesn't, then you cannot do anything to fix it, but in most cases it does. The only thing to worry about when doing it is that you can boot to Vista again. Just leave /fixmbr alone and it should all be good.

---

### Post by Mark Phelps on 2010-05-10
Bluec10:

Did you manually install GRUB to every single NTFS partition you have?

You only need GRUB installed to the boot DRIVE, not to every NTFS partition.

Since you probably do NOT have a Vista repair CD, suggest you go to the site below, download and burn the proper cd image, boot from that, and run Startup Repair three times.  That should get you booting back into Vista.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you have that working, come back for instructions on how to install GRUB2 once ... and only once.

---

