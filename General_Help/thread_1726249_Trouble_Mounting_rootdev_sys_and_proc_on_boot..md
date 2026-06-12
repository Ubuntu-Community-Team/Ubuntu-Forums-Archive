---
title: "Trouble Mounting /root/dev /sys and /proc on boot."
date: 2011-04-10
forum: General Help
---

### Post by jethro_tell on 2011-04-10
My system has been having some trouble booting lately.  When I go start the system it loads the boot list from grub and after I have selected the kernel to load it trys to mount the partitions for a minute then gives me this error:

```
mount: mounting /dev/sdf1 on /root failed: no such device
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have requested /sbin/inti.
no into found. Try passing init= booting. 
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

enter help for a list of commands. 
(initramfs)
```

It has been doing this off and on for a couple weeks.  I get this error then an hour latter it might boot normally.
Because it's been a bit sporadic I assumed the drive was failing.

I used a live cd to run ckfs -fv and the drive seems to be fine:

```
root@ubuntu:~# fsck -fv /dev/sdc1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

 322981 inodes used (6.89%)
    410 non-contiguous files (0.1%)
    358 non-contiguous directories (0.1%)
        # of inodes with ind/dind/tind blocks: 0/0/0
        Extent depth histogram: 288338/97
 2138465 blocks used (11.42%)
      0 bad blocks
      1 large file

 239451 regular files
  41236 directories
     59 character device files
     26 block device files
      3 fifos
    390 links
  42163 symbolic links (34414 fast symbolic links)
     34 sockets
--------
 323362 files
```

I'm thinking that I have a configuration problem in my boot set up but I'm having trouble tracking it down.  I ran the Boot Info Script to grab as much Data as I can.  I'm hoping someone who understands a little bit more about the boot process might be able to spot a problem.  I haven't been able to find much on the googler that wasn't for a failed drive, so the forum posts I have seen aren't real helpful to my problem.

 ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
 => Syslinux is installed in the MBR of /dev/sdf
 => No boot loader is installed in the MBR of /dev/sdg
 => No boot loader is installed in the MBR of /dev/sdh
 => No boot loader is installed in the MBR of /dev/sdi
 => Syslinux is installed in the MBR of /dev/sdj

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdg1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdi1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdj1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdj1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdj1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

md0: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,953,523,711 1,953,521,664  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              40       409,639       409,600 System/Boot Partition
/dev/sdb2         409,640   976,510,983   976,101,344 HFS+

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   149,792,767   149,790,720  83 Linux
/dev/sdc2         149,794,814   156,248,063     6,453,250   5 Extended
/dev/sdc5         149,794,816   156,248,063     6,453,248  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048    12,290,047    12,288,000  83 Linux
/dev/sdd2          12,290,048   106,151,935    93,861,888  83 Linux
/dev/sdd3         106,151,936   147,533,823    41,381,888  83 Linux
/dev/sdd4         147,533,824   156,248,063     8,714,240  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               2,048 1,953,523,711 1,953,521,664  fd Linux raid autodetect


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1027 MB, 1027416576 bytes
32 heads, 62 sectors/track, 1011 cylinders, total 2006673 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             62     2,005,823     2,005,762   c W95 FAT32 (LBA)


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048 1,953,523,711 1,953,521,664  fd Linux raid autodetect


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               2,048 1,953,523,711 1,953,521,664  fd Linux raid autodetect


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1               2,048 1,953,523,711 1,953,521,664  fd Linux raid autodetect


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdj1    *             62    15,620,279    15,620,218   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       88b97a52-ca7b-43f1-8552-39f6c2db926c   ext3                                     
/dev/md0: PTTYPE="gpt" 
/dev/sda1        6322c931-65e0-9e2f-2391-f9ca37b8650c   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        70D6-1701                              vfat       EFI                           
/dev/sdb2        7802ffc3-8d9b-3333-8e64-43b67f682b5f   hfsplus                                  
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        a2bb0a63-d923-4693-a43b-e5dca30cef7b   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        29dd463c-d10c-423e-b4ea-dfd66160f3dd   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        f2a20577-8934-478f-b1c9-956f6cb7b867   ext3       boot                          
/dev/sdd2        d21a0001-ecf2-4749-8ab0-ae0d0bd6db3d   ext3       home                          
/dev/sdd3        26797a7c-65a8-42b7-a2ce-904dc14f8ba6   ext3       src                           
/dev/sdd4        696d810b-545d-4f3a-9daf-0ceeb42190df   swap       swap                          
/dev/sdd: PTTYPE="dos" 
/dev/sde1        6322c931-65e0-9e2f-2391-f9ca37b8650c   linux_raid_member                               
/dev/sde: PTTYPE="dos" 
/dev/sdf1        0C6A-4648                              vfat                                     
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        6322c931-65e0-9e2f-2391-f9ca37b8650c   linux_raid_member                               
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        6322c931-65e0-9e2f-2391-f9ca37b8650c   linux_raid_member                               
/dev/sdh: PTTYPE="dos" 
/dev/sdi1        6322c931-65e0-9e2f-2391-f9ca37b8650c   linux_raid_member                               
/dev/sdi: PTTYPE="dos" 
/dev/sdj1        8C54-CCDB                              vfat                                     
/dev/sdj: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/drive             hfsplus    (rw)
/dev/sdj1        /media/8C54-CCDB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd5,msdos1)'
search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd5,msdos1)'
search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-28-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=/dev/sdf1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-27-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=/dev/sdf1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=/dev/sdf1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-24-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=/dev/sdf1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-23-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=/dev/sdf1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux	/boot/vmlinuz-2.6.35-22-generic root=/dev/sdf1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=/dev/sdf1 ro single 
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
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd5,msdos1)'
	search --no-floppy --fs-uuid --set a2bb0a63-d923-4693-a43b-e5dca30cef7b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# OS Disk:
# / was on /dev/sda1 during installation
UUID=a2bb0a63-d923-4693-a43b-e5dca30cef7b /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
UUID=29dd463c-d10c-423e-b4ea-dfd66160f3dd none            swap    sw              0       0


#Array:
# md0p1  /media/Media          ext4    rw,users,auto   0       0

#floppy
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


=================== sdc1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.35-22-generic
  10.4GB: boot/initrd.img-2.6.35-23-generic
  17.4GB: boot/initrd.img-2.6.35-24-generic
  19.6GB: boot/initrd.img-2.6.35-25-generic
  26.4GB: boot/initrd.img-2.6.35-27-generic
  74.5GB: boot/initrd.img-2.6.35-28-generic
  13.0GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: boot/vmlinuz-2.6.35-23-generic
  14.5GB: boot/vmlinuz-2.6.35-24-generic
  14.8GB: boot/vmlinuz-2.6.35-25-generic
  13.1GB: boot/vmlinuz-2.6.35-27-generic
  74.4GB: boot/vmlinuz-2.6.35-28-generic
  74.5GB: initrd.img
  26.4GB: initrd.img.old
  74.4GB: vmlinuz
  13.1GB: vmlinuz.old

=========================== sdf1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdf1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

=========================== sdj1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdj1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  82 96 78 69 8a 47 27 b0  1b e5 d6 9e 88 d3 33 7c  |..xi.G'.......3||
00000010  35 ee e6 d1 a3 1f e9 f4  6b 24 02 45 6b 3f be 75  |5.......k$.Ek?.u|
00000020  93 14 6c a0 e6 57 47 30  84 e4 cd 78 1c 72 90 c4  |..l..WG0...x.r..|
00000030  ab 43 7c 7d 70 b1 32 64  e2 9d 83 cf 0e 5d 9e c8  |.C|}p.2d.....]..|
00000040  f2 a3 bf 54 9e 11 5a 37  fd ba 33 55 16 7d 31 9f  |...T..Z7..3U.}1.|
00000050  64 e2 ce 21 0f 57 37 60  be a3 c5 c0 a1 57 72 f3  |d..!.W7`.....Wr.|
00000060  c7 cb af f7 2c d4 88 1a  95 97 05 81 83 15 27 6a  |....,.........'j|
00000070  aa 59 19 9b 3c 74 d8 90  cc 2e 2a 17 6c 36 c5 53  |.Y..<t....*.l6.S|
00000080  92 81 27 7f 2e 3e f0 b0  21 a8 4c b3 17 97 e9 21  |..'..>..!.L....!|
00000090  70 91 3b 84 e0 a1 82 4b  00 75 c9 27 6e b6 e1 6f  |p.;....K.u.'n..o|
000000a0  60 9b d6 bf b4 ec c6 f3  b1 01 23 81 a4 4b f7 3a  |`.........#..K.:|
000000b0  0e a2 10 b3 ac 0c 22 93  24 41 9c da c1 e8 3c 14  |......".$A....<.|
000000c0  97 aa 95 37 00 b4 51 82  c8 1c f6 b5 14 d1 d6 ec  |...7..Q.........|
000000d0  95 5a f2 b3 56 9b e2 d6  b1 e4 c1 02 d1 fe e6 92  |.Z..V...........|
000000e0  41 79 1a 16 e9 9e 1a 57  f6 7a 31 d7 93 67 fc 5c  |Ay.....W.z1..g.\|
000000f0  32 08 48 43 3b 66 fc 3f  70 5b e1 a0 2f 20 c4 6b  |2.HC;f.?p[../ .k|
00000100  ca ea f1 a9 93 ee 53 26  d7 ac a1 51 6f 80 82 95  |......S&...Qo...|
00000110  23 fa e4 2e 7d ff c8 e4  de 3d fd 10 28 52 13 c8  |#...}....=..(R..|
00000120  f1 4a 0b c6 1b 41 b5 cb  44 e5 c5 07 45 d5 bd de  |.J...A..D...E...|
00000130  9a 49 ed e1 3f ba 9c a1  3b 13 77 3c 24 44 e8 be  |.I..?...;.w<$D..|
00000140  c1 2b 3a bf 43 04 94 99  94 f9 cc 1b b3 93 77 c7  |.+:.C.........w.|
00000150  a2 0b d0 be 3f 04 e5 11  82 bb 00 0e 86 7a 59 e3  |....?........zY.|
00000160  79 e2 92 33 19 16 b8 83  7f c9 db 50 b1 fe bf ff  |y..3.......P....|
00000170  08 f9 92 34 74 b4 04 96  f4 29 2b 61 48 8b d9 f3  |...4t....)+aH...|
00000180  19 db 94 94 2d 49 28 4b  b1 97 5e 9a 8d 84 27 60  |....-I(K..^...'`|
00000190  06 38 64 15 1c 42 b5 bd  5e 72 13 e9 9e ae 87 32  |.8d..B..^r.....2|
000001a0  4a b4 d8 2a 53 c7 7b aa  d1 a6 f2 23 bc 4d 88 3d  |J..*S.{....#.M.=|
000001b0  31 82 58 a0 f7 23 2b 46  a7 eb d8 f8 6b f5 00 fe  |1.X..#+F....k...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 62 00 00 00  |...........xb...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdf1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 20 00 00 00 00 00  |........>. .....|
00000020  02 9b 1e 00 a8 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 48 46 6a 0c 20  20 20 20 20 20 20 20 20  |..)HFj.         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 f0 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdj1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 f7 00 00 00 00 00  |........>.......|
00000020  7a 58 ee 00 80 3b 00 00  00 00 00 00 02 00 00 00  |zX...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 db cc 54 8c 20  20 20 20 20 20 20 20 20  |..)..T.         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 a0 2e 16 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: /dev/md0 has been started with 5 drives.
mdadm: stopped /dev/md0
```

---

### Post by srs5694 on 2011-04-11
It looks to me as if your drive IDs have changed:


[list]
[*]Your /etc/fstab indicates that Linux was /dev/sda1 when it was installed, but that's now a Linux RAID member partition
[*]Your GRUB configuration is telling the Linux kernel to use /dev/sdf1 as the root (/) filesystem, but that appears to be a FAT partition
[*]From various clues, it appears to me that your Linux root (/) filesystem is actually /dev/sdc1
[/list]


I recommend you edit your /boot/grub/grub.cfg file to pass /dev/sdc1 rather than /dev/sdf1 as a kernel option (the "root=/dev/sdf1" bit on the "linux" lines, or at least one of them). I think it's also possible to use a UUID here, which would be even better, but I'm not sure of the exact syntax.

---

### Post by jethro_tell on 2011-04-11
> **srs5694 said:**
> I think it's also possible to use a UUID here, which would be even better, but I'm not sure of the exact syntax.

That would explain why it is a bit hit or miss for the boot (depending which usb drives I have mounted  . . .)  I'll try this and see if it fixes it.

---

### Post by WorMzy on 2011-04-11
> **srs5694 said:**
> It looks to me as if your drive IDs have changed:


[list]
[*]Your /etc/fstab indicates that Linux was /dev/sda1 when it was installed, but that's now a Linux RAID member partition
[*]Your GRUB configuration is telling the Linux kernel to use /dev/sdf1 as the root (/) filesystem, but that appears to be a FAT partition
[*]From various clues, it appears to me that your Linux root (/) filesystem is actually /dev/sdc1
[/list]


I recommend you edit your /boot/grub/grub.cfg file to pass /dev/sdc1 rather than /dev/sdf1 as a kernel option (the "root=/dev/sdf1" bit on the "linux" lines, or at least one of them). I think it's also possible to use a UUID here, which would be even better, but I'm not sure of the exact syntax.

It'd be "root=/dev/disk/by-uuid/a2bb0a63-d923-4693-a43b-e5dca30cef7b", assuming that the root partition is indeed sdc1.

---

### Post by jethro_tell on 2011-04-11
> **WorMzy said:**
> It'd be "root=/dev/disk/by-uuid/a2bb0a63-d923-4693-a43b-e5dca30cef7b", assuming that the root partition is indeed sdc1.

Ok, Thanks team!! That was it, It's all good now.

I have a couple questions about my grub.cfg then.  Is there a way to automate this so that new kernel installs update the boot loader by uuid?  

can I go through and delete the kernel entries I'm not using?

Thanks for your help!!

---

