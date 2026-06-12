---
title: "Mounting SATA hard drives"
date: 2011-07-03
forum: General Help
---

### Post by Bynack on 2011-07-03
Hello. Really hoping someone can help me me. I've decided to move from Ubuntu to Xubuntu on my aging desktop. I opted for a completely new installation so that I could start with a clean system. I have two additional 250GB SATA drives which were working fine under Ubuntu, but I am unable to mount them in Xubuntu. My partitioned 40GB ATA drive (which I use as my primary drive for the operating system) is working fine. When I run "sudo fdisk -l" I get:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         523     4200966    7  HPFS/NTFS
/dev/sda2             524        1709     9526545   83  Linux
/dev/sda3            1710        1970     2096482+  82  Linux swap / Solaris
/dev/sda4            1971        4865    23254087+  83  Linux

Disk /dev/sdd: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000353c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30395   244139008   83  Linux

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000353c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30395   244139008   83  Linux

Disk /dev/sdb: 15.4 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1868    15004678+  83  Linux

Disk /dev/dm-0: 250.0 GB, 249997295616 bytes
255 heads, 63 sectors/track, 30393 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000353c2

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1 

If I try and mount sdc1 with "sudo mount /dev/sdc1 /mnt" I get:

mount: special device /dev/sdc1 does not exist

I don't know what is going on, but I really need to get these drive to mount.

Thanks

A

---

### Post by oldfred on 2011-07-03
I really do not know RAID or LVM. But /dev/dm-0 is RAID I think. 

Run this script but download the extra drivers first.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
#may already be installed
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install mawk

---

### Post by psusi on 2011-07-03
I am guessing that these two drives are part of a fakeraid raid-1, and you are trying to directly access an individual drive instead of the raid array.  Don't do that.

---

### Post by Bynack on 2011-07-04
Hi thanks for replying. Yes I am trying to mount to two drives individual drives (I want the extra disk space). This was the set up I had on my previous installation of Ubuntu 11.04 and had no problems until switching to Xubuntu. What is the problem with mounting them separately?

I ran the boot info script which gave the output below.

Thanks


                 ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_heeeffjgb_ARRAY 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

isw_heeeffjgb_ARRAY1: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     8,401,994     8,401,932   7 NTFS / exFAT / HPFS
/dev/sda2           8,401,995    27,455,084    19,053,090  83 Linux
/dev/sda3          27,455,085    31,648,049     4,192,965  82 Linux swap / Solaris
/dev/sda4          31,648,050    78,156,224    46,508,175  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.4 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders, total 30015216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    30,009,419    30,009,357  83 Linux


Drive: isw_heeeffjgb_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_heeeffjgb_ARRAY: 250.0 GB, 249997295616 bytes
255 heads, 63 sectors/track, 30393 cylinders, total 488275968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_heeeffjgb_ARRAY1              2,048   488,280,063   488,278,016  83 Linux

/dev/mapper/isw_heeeffjgb_ARRAY1 ends after the last sector of /dev/mapper/isw_heeeffjgb_ARRAY

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8834F11634F107C8                       ntfs       
/dev/sda2        3f1b5309-da1d-487a-8e9a-9d60bf3da800   ext4       
/dev/sda3        e61a869f-c579-47d0-9a72-f381dc6a09a1   swap       
/dev/sda4        948e1a14-e60d-45a4-8c66-958e1a90de26   ext3       
/dev/sdb1        93c57a17-50e2-476b-85ab-be71c904247d   ext3       
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_heeeffjgb_ARRAY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3f1b5309-da1d-487a-8e9a-9d60bf3da800 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3f1b5309-da1d-487a-8e9a-9d60bf3da800 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f1b5309-da1d-487a-8e9a-9d60bf3da800
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8834F11634F107C8
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=e61a869f-c579-47d0-9a72-f381dc6a09a1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.314496517 = 11.075106304   boot/grub/core.img                             1
  10.315545559 = 11.076232704   boot/grub/grub.cfg                             1
   7.418076992 = 7.965099520    boot/initrd.img-2.6.38-8-generic               1
  10.354344845 = 11.117893120   boot/vmlinuz-2.6.38-8-generic                  1
   7.418076992 = 7.965099520    initrd.img                                     1
  10.354344845 = 11.117893120   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_heeeffjgb_ARRAY1



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/mapper/isw_heeeffjgb_ARRAY1: No such file or directory
hexdump: /dev/mapper/isw_heeeffjgb_ARRAY1: No such file or directory
  No volume groups found

```

---

### Post by oldfred on 2011-07-04
I know with RAID you do not use standard partition tools but you have to adjust the end of the RAID.

/dev/mapper/isw_heeeffjgb_ARRAY1 ends after the last sector of /dev/mapper/isw_heeeffjgb_ARRAY

---

### Post by Bynack on 2011-07-04
Is it possible to mount two RAID drives as separate hard drives? I don't really understand how RAID drives work (sorry), I just want these to run/mount as separate drives. Any suggestion gratefully received

A

---

### Post by psusi on 2011-07-04
If you don't want to use the drives in a raid array any more, then you need to go into the bios and destroy the raid array.

---

### Post by Bynack on 2011-07-04
Ok, I will try an work out how to do this (any suggestions? I'm using a Dell Precision Desktop). Will destroying the RAID array format the hard drives?

---

### Post by oldfred on 2011-07-04
After you turn off RAID, you also have to remove some meta-data from the drives. Yours may not be sda & sdb as shown in example below. Just change to whichever drive letters they are.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Bynack on 2011-07-04
My BIOS doesn't appear to have any RAID options (its an old Dell Precision 360). The two SATA drives were taken from another computer - could the problem be that they were mounted as RAID partitions on the old PC and still have some residual files from old installations as mentioned in this thread [http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650) ? I ask being I wasn't sure whether to run the command 

```
sudo dmraid -E -r /dev/sda
```

with out altering the bios. Is this likely to cause issues i.e. data loss? I think the drives are back up but am not 100% sure everything is back up so would like to avoid formatting them if possible.

Thanks for all you help by the way. The Ubuntu community shows is strength again!

---

### Post by oldfred on 2011-07-04
Anytime you change configurations of drives there is some risk of data loss. Some more than others. 

But if the link says they did not lose data, I would not think running the command will cause data loss on its own. 

But if you want to be able to use drives in a computer that does not support RAID you have to remove the RAID meta-data.

---

### Post by Bynack on 2011-07-04
It Works!!!

Thank you so much for your help. I have now managed to mount my two drives with all the data in tact. All I had to do was run 

```
sudo dmraid -E -r /dev/sdc
sudo dmraid -E -r /dev/sdd
```

Brilliant!

Thanks again

---

