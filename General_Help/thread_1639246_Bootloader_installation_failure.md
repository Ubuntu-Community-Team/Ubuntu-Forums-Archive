---
title: "Bootloader installation failure"
date: 2010-12-06
forum: General Help
---

### Post by Osedax on 2010-12-06
I'm trying to install 10.10 on a desktop system, but every time I go through the process, it gives an error saying that the installer cannot install the bootloader on the hard drive. Before this, I manually set up the partition table so that there's a 10 gig / partition, a 68 gig /home partition, and a 2 gig swap. What could be causing the problem? (In setting up the partitions, I have each listed to be formatted to ext4. There shouldn't be any other stuff on the disk.)

---

### Post by Rubi1200 on 2010-12-07
Hi,
from the LiveCD, post the output of the following command:
```
sudo fdisk -lu
```

Thanks.

---

### Post by Osedax on 2010-12-07
fdisk output:```

Disk /dev/sda: 80 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9727 cylinders, total 156301488 sectors
Units = sectors of 1*512 = 512 bytes
Sector size (logical/physical): 512 bytes , 512 bytes
I/O size (minimum/optional): 512 bytes, 512 bytes
Disk identifier: 0x000910e6
   Device    Boot      Start         End     Blocks    Id    System
/dev/sda1       *       2048   150159359   75078656    83     Linux
/dev/sda2          150161406   156301311    3069953     5  Extended
/dev/sda5          150161408   156301311    3069952    82  Linux swap / Solaris
```

NB: this is after I ran through the installation, allowing the livedisk to do whatever it wanted with the partition table.
sda3-4 are two other hard drives that I *do not* want to touch.

I suspect that the MBR is corrupted, since the previous install started having troubles booting up. But shouldn't that get fixed when the livedisk reformats the drive?

---

### Post by matt_symes on 2010-12-07
Hi

> sda3-4 are two other hard drives that I *do not* want to touch.Did  you mean  partitions (sda3,  sda4)? If so, it looks like they are gone.

or  did you mean sdb and sdc hard drives?

Run the boot info script in Rubi1200 signature [Boot info script]("http://bootinfoscript.sourceforge.net/") courtesy of meierfra. It will give  more information of what is going on with  your system. Run it from the  LiveCD.

Kind  regards

---

### Post by Rubi1200 on 2010-12-07
+1 to the boot info script recommended by matt_symes.

The results will hopefully give us a much clearer picture of what is going on.

Posting the full specifications for the machine in question would also help.

Thanks.

---

### Post by Osedax on 2010-12-07
Ran the script, got the results. Had to carry results file over to other computer to post, and windows notepad won't display it properly. Here goes.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,159,359   150,157,312  83 Linux
/dev/sda2         150,161,406   156,301,311     6,139,906   5 Extended
/dev/sda5         150,161,408   156,301,311     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders, total 12594960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     8,401,994     8,401,932   b W95 FAT32
/dev/sdb2          12,578,895    12,594,959        16,065  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        346fb267-4a0b-4473-a61c-f90db8158f0c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        dfd2fe8e-a688-47b2-87ec-364de81a7751   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        147B-2B34                              vfat                                     
/dev/sdb2        11f699b8-069c-4668-a98c-0526926f74f4   ext3       /                             
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        10D8-132E                              vfat       THE BARN                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        C755-A439                              vfat       USB DISK                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=346fb267-4a0b-4473-a61c-f90db8158f0c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=346fb267-4a0b-4473-a61c-f90db8158f0c ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 346fb267-4a0b-4473-a61c-f90db8158f0c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod part_msdos
	insmod fat
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 147b-2b34
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=346fb267-4a0b-4473-a61c-f90db8158f0c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dfd2fe8e-a688-47b2-87ec-364de81a7751 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.4GB: boot/grub/core.img
  36.7GB: boot/grub/grub.cfg
  13.1GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: initrd.img
    .3GB: vmlinuz

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by matt_symes on 2010-12-07
Hi

Part of the RESULTS.TXT file  you posted above is missing.  We really need the output of the whole  file. You could please repost it in its entirety.

 > I manually set up the partition table so that there's a 10 gig / partition, a 68 gig /home partition, and a 2 gig swap

Did you mean to have your Linux partitions to straddle to drives? Also you have not set them up as stated in the quote above.

Kind regards

---

### Post by Osedax on 2010-12-07
> **matt_symes said:**
> 
Did you mean to have your Linux partitions to straddle to drives?

Edited above to include the entirety of the results file.

My intention was to configure one hard drive to have two partitions: one for the OS and a separate one for my /home directory. Since I first posted this problem, I tried letting the installer "use the entire disk" on the next go 'round, without doing anything to the partition table on my own. Hopefully the results of the boot inspector reflect this; if not, yikes!

---

### Post by Osedax on 2010-12-09
I'm still stumped. Is there a better way of examining the MBR? Or is it possible that the .iso is defective, since it took several attempts for me to produce a functioning live cd?

---

### Post by Rubi1200 on 2010-12-09
The results seem to indicate that Ubuntu and GRUB are installed and in the right places.

Have you tried changing the boot order priority in BIOS to boot sda as the first drive?

---

### Post by Osedax on 2010-12-09
> **Rubi1200 said:**
> Have you tried changing the boot order priority in BIOS to boot sda as the first drive?

Yup. It's something with hard drive itself. What other tools can I use to figure what the problem is?

---

### Post by matt_symes on 2010-12-09
Hi

Have you checked the SMART status of the drive?

Kind regards.

---

### Post by Osedax on 2010-12-10
> **matt_symes said:**
> Hi

Have you checked the SMART status of the drive?

Kind regards.

How? I'm a noob and know nothing about this stuff.

---

### Post by matt_symes on 2010-12-10
Hi

As Dino1200 pointed out Grub looks fine. Can you actually boot into sda?

If you can boot into sda, you can check your hard drive status from System->Administration->Disk utility. 

If not you can do it from the live CD or USB from the same menu. 

Select  the drive and it will tell you its status in the right hand pane. You can also run tests on the  drive.

Kind regards

---

### Post by Osedax on 2010-12-12
OK, I tried the disk utility on the live CD (cannot boot the disk). It says that SMART is not supported. Attempting to format the disk through the utility gave this error:> 
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file = /dev/sda, scheme = 3
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/sda: Device or resource busy
Nothing else yielded any information.
Thanks for your patience, by the way, in continuing to reply to this thread after all these days. I'm at the end of my rope here; several hours of googling haven't gotten me anywhere.

For what it's worth, the device is a Maxtor ATA 6L080P0, which I got >4 years ago, and has seen a lot of use since. Is this simply the end of a modern hdd's life cycle?

EDIT: just rechecked the disk utility, and *now* it's showing the SMART data, saying that the disk is "healthy". There are no bad sectors, disk isn't running hot, and all other parameters seem to be just fine.

So, what the hell?

---

