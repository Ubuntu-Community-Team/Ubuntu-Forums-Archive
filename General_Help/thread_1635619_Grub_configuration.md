---
title: "Grub configuration"
date: 2010-12-02
forum: General Help
---

### Post by lanig on 2010-12-02
Hi, 

I have three disks in my computer.
1)one ATA with only windows (sda1),
2)one sata with windows on one partition (sdb1) and linux  (/ on sdb5) on the others,
3)one sata for data (backup).
When I upgraded from 10.04, grub was nicely configurated with a menu item for each of the bootable partitions.
I had previously tried to have this config but failed and had considerable work to come back to an usable state.
With the last kernel udate, the sda1 choice is gone from the menu and I must hit F11 to boot from it. How can I simply edit my config to  get back to the previous state ?

TIA

Alain

---

### Post by garvinrick4 on 2010-12-02
You are going to have to download this script to your DESKTOP and then run the code given below and will put a file called RESULTS on your desktop. Copy and paste it
to this thread of yours. After pasted you can highlight whole thing is long and hit the little
# sign in right of the Message box and will put in nice little box to be read easily.
Only takes 30 seconds or so. Users will be able to find any problem right away.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by lanig on 2010-12-02
Thanks for your answer. Here is the output.
It can probably be guessed from the end but there is no windows on /dev/sdc.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 82.0 Go, 81964302336 octets
255 têtes, 63 secteurs/piste, 9964 cylindres, total 160086528 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,811   960,478,154   919,512,344   5 Extended
/dev/sdb5          40,965,813   149,516,954   108,551,142  83 Linux
/dev/sdb6         149,517,018   171,027,989    21,510,972  82 Linux swap / Solaris
/dev/sdb7         171,028,053   960,478,154   789,450,102  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        506C5D1B6C5CFD62                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BAB03A69B03A2BEF                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4935671a-aa02-4c12-b9ee-c46c2d751b5a   ext3                                     
/dev/sdb6        669cd73b-f38c-47ef-846b-9d6c65edea9e   swap                                     
/dev/sdb7        f9333098-d4e2-430b-aff1-b830554e2198   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        bf6af452-21dd-4404-bb70-c05fc6046269   ext3                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/il2               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/cao               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /backup                  ext3       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /fastdetect /NoExecute=OptIn


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /fastdetect /NoExecute=OptIn


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="0"
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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
set locale_dir=($root)/boot/grub/locale
set lang=fr
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=4935671a-aa02-4c12-b9ee-c46c2d751b5a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=4935671a-aa02-4c12-b9ee-c46c2d751b5a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4935671a-aa02-4c12-b9ee-c46c2d751b5a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4935671a-aa02-4c12-b9ee-c46c2d751b5a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 4935671a-aa02-4c12-b9ee-c46c2d751b5a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set bab03a69b03a2bef
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=4935671a-aa02-4c12-b9ee-c46c2d751b5a /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=f9333098-d4e2-430b-aff1-b830554e2198 /home           ext3    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=669cd73b-f38c-47ef-846b-9d6c65edea9e none            swap    sw              0       0
UUID=bf6af452-21dd-4404-bb70-c05fc6046269 	/backup 	ext3	 defaults 	0	2
UUID=BAB03A69B03A2BEF	/media/il2  ntfs defaults  0	2
UUID=506C5D1B6C5CFD62  	/media/cao	ntfs defaults  0	2



=================== sdb5: Location of files loaded by Grub: ===================


  29.8GB: boot/grub/core.img
  29.8GB: boot/grub/grub.cfg
  29.9GB: boot/initrd.img-2.6.35-22-generic
  29.9GB: boot/initrd.img-2.6.35-23-generic
  29.9GB: boot/vmlinuz-2.6.35-22-generic
  29.9GB: boot/vmlinuz-2.6.35-23-generic
  29.9GB: initrd.img
  29.9GB: initrd.img.old
  29.9GB: vmlinuz
  29.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  77 77 77 77 77 77 77 77  77 77 77 77 77 77 77 77  |wwwwwwwwwwwwwwww|
*
000001b0  77 77 77 77 77 77 77 77  77 77 77 77 77 77 00 01  |wwwwwwwwwwwwww..|
000001c0  c1 ff 83 fe ff ff 02 00  00 00 e6 5b 78 06 00 fe  |...........[x...|
000001d0  ff ff 05 fe ff ff e8 5b  78 06 7b 3b 48 01 00 00  |.......[x.{;H...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by searchfgold6789 on 2010-12-02
Maybe you will have to run sudo update-grub again.
That sometimes happens to me, which is ugly doing it from the LiveCD.

---

### Post by drs305 on 2010-12-02
If it's not picked up by update-grub, you could try adding this as a 40_custom menuentry.

Open /etc/grub.d/40_custom and replace the contents with the following:
> 
#!/bin/sh
echo "Adding 40_custom." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 506C5D1B6C5CFD62
	drivemap -s (hd0) ${root}
	chainloader +1
}


Save the file and run update-grub. You should see a terminal entry "Adding 40_custom." as the command is run. If you don't see it, make sure 40_custom is executable (sudo chmod +x /etc/grub.d/40_custom).

Added: You may need to play with the (hdX) values. The easiest/fastest way to test the combinations is to highlight the menuentry at the Grub2 menu and then press "e" to enter the editing mode. Experiment with the values and press CTRL-x to boot. Once you find a combination which works you will have to edit the 40_custom file and run update-grub to make the change permanent.

---

### Post by lanig on 2010-12-02
Thanks a lot. update grub alone did fix the problem but I am glad to know how to describe a correct sda entry for grub.

Thanks again,

Alain

---

