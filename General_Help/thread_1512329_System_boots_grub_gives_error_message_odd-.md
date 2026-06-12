---
title: "System boots grub gives error message odd:-|"
date: 2010-06-18
forum: General Help
---

### Post by skaramanger on 2010-06-18
Greetings,

I recently did some hard drive swapping around on my two systems.  I cloned a 250GB eide to a 250GB sata. Then swapped in a second 320GB sata and put the eide in another machine.  So I have my main box with two sata drives.

After cloning, and subsequent booting grub gave a file not found error message and then a 10 second countdown and then would boot up the system.  I'd obviously like to eliminate this unusual behavior by grub.  I thinks its possible when I did my disk to disk clone I told clonezilla to do something that might have caused this message and additional time delay. I'm hoping for some troubleshooting suggestions and of course an outright solution would be nicer;).

Tia

---

### Post by wilee-nilee on 2010-06-18
I think a good start would be the script in my sig to see whats going on, and where and what the boot setups are and what OS are being used. Post it in code tags as the sig shows.;)

---

### Post by skaramanger on 2010-06-19
Thanks for your reply,

Well here goes:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,080   366,217,739   327,147,660   5 Extended
/dev/sda5          39,070,143    62,508,914    23,438,772  83 Linux
/dev/sda6          62,508,978    73,256,399    10,747,422  82 Linux swap / Solaris
/dev/sda7          73,256,463   366,217,739   292,961,277  83 Linux
/dev/sda3         366,217,740   488,392,064   122,174,325   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,593,239   409,593,177  83 Linux
/dev/sdb2         409,593,240   625,137,344   215,544,105   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0eaa02f9-8d4a-40b6-b282-9001ca383700   ext3       root                          
/dev/sda2: PTTYPE="dos" 
/dev/sda3        2536E56D4D3327B3                       ntfs                                     
/dev/sda5        b34aa478-7495-4e4a-bfba-f31d24d268eb   ext3       Home                          
/dev/sda6        e3c944e6-00af-44f5-b937-6d5999325148   swap                                     
/dev/sda7        969e7370-b0e5-4127-85e1-745cb500d6b8   ext3       Downloads                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e6ac3aa6-4191-435d-9dd0-2924f7a415ba   ext4       More_Storage                  
/dev/sdb2        493B029C1F00B81C                       ntfs       More_NTFS                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /media/More_Storage      ext4       (rw,noexec,nosuid,nodev,user_xattr)
/dev/sda7        /media/Downloads         ext3       (rw,noexec,nosuid,nodev,user_xattr)
/dev/sdb2        /media/More_NTFS         fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /home                    ext3       (rw,user_xattr)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=12
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 ro   quiet splash apci_enforce_resorces=lax
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 ro   quiet splash apci_enforce_resorces=lax
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0eaa02f9-8d4a-40b6-b282-9001ca383700
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 /               ext3    errors=remount-ro 0       1
# MyDwnlds was on /dev/sda7 during installation
UUID=969e7370-b0e5-4127-85e1-745cb500d6b8 /media/Downloads ext3	defaults,auto,users,user_xattr        0       2
# UUID=969e7370-b0e5-4127-85e1-745cb500d6b8 for Downloads partition
# /home was on /dev/sda5 during installation
UUID=b34aa478-7495-4e4a-bfba-f31d24d268eb /home ext3 defaults,user_xattr        0       2
# swap was on /dev/sda6 during installation
UUID=e3c944e6-00af-44f5-b937-6d5999325148 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# UUID=0a3b8fc4-062f-4ff6-81d5-f3ba03f1d425	/media/My_Book	ext3	defaults,users,auto	0	0
UUID="e6ac3aa6-4191-435d-9dd0-2924f7a415ba" /media/More_Storage ext4 defaults,auto,users,user_xattr 0	2
UUID="493B029C1F00B81C" /media/More_NTFS ntfs defaults,auto,users

=================== sda1: Location of files loaded by Grub: ===================


  18.6GB: boot/grub/core.img
  18.6GB: boot/grub/grub.cfg
  18.5GB: boot/initrd.img-2.6.31-21-generic
  18.5GB: boot/initrd.img-2.6.32-22-generic
  18.5GB: boot/vmlinuz-2.6.31-21-generic
  18.7GB: boot/vmlinuz-2.6.32-22-generic
  18.5GB: initrd.img
  18.5GB: initrd.img.old
  18.7GB: vmlinuz
  18.5GB: vmlinuz.old
```

Thanks again

---

### Post by skaramanger on 2010-07-12
I believe the error message from setting up one of the partitions as a primary partitionin with grub installed on it.  After post the system finds that drive first though I thought I set it up as sdb and not sda (somehow in bios they are switched).  After it doesn't find an OS to boot it jumps to the next bootable device and grub menu appears.  Just my thoughts.  Any suggestions as to make sure that it is not accessed during boot?

Skaramanger

---

### Post by skaramanger on 2010-07-21
Bump?

---

### Post by oldfred on 2010-07-21
You have to be booting the 250GB drive as the grub in sdb 320GB does not boot at all. Both initial set root of hd01 and UUID look correct for boot partition, so I do not know why it has issues.

Do you have a floppy configued in BIOS but no floppy. I might also try manually editing grub menu to delete search line. Is error before or after menu?

---

### Post by skaramanger on 2010-07-21
>>>[QUOTE=oldfred;9618047]You have to be booting the 250GB drive as the >>>grub in sdb 320GB does not boot at all. Both initial set root of hd01 >>>and UUID look correct for boot partition, so I do not know why it has >>>issues.

>>> Do you have a floppy configued in BIOS but no floppy.

There is a floppy drive configured in bios and physically present. Though I'd just as soon dump it, but I have a couple of floppies lying around.


>>> I might also try manually editing grub menu to delete search line.

Search line?

>>> Is error before or after menu?

Its been awhile since a reboot, but IIRC I get the message grub starting, the menu appears, I make my selection for the default kernel, and an error message appears, file not found.

Thanks,

Skaramanger

---

### Post by drs305 on 2010-07-21
I don't see the problem with your grub.cfg either. If you are currently booted into your Ubuntu install, you might check */boot/grub/device.map* to see if the drives are assigned correctly. Running "sudo update-grub" wouldn't hurt either, just to ensure Grub2 has the current configuration.

As far as the "search" line, if you are still having an initial failure when selecting the entry at the Grub boot menu, try pressing "e" to get into the grub edit mode. Cursor to the start of the "search" line and hold down the DEL key until that line is completely removed. Then press CTRL-x to try to boot.

If it works, we will have to get rid of the search line by modifying some of your Grub system files, but we can take care of that if we determine the 'search' line is the thing causing the problem.

---

### Post by skaramanger on 2010-07-23
Just in case,

I got the most recent updates for grub and kept my original file and when prompt had grub installed on /dev/sda. Rebooted and error message went away.

Thanks for everyone's response

Skaramanger


drs305,

I did reboot and noted that I was in error. The error message appears then the grub menu. Does this implicate device.map as the culprit? 

>>>[QUOTE=drs305;9620301]I don't see the problem with your grub.cfg >>>either. If you are currently booted into your Ubuntu install, you >>>might check */boot/grub/device.map*


(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

Maybe sdb and sda need to switch places?

<snip>

>>Running "sudo update-grub" wouldn't hurt either, just to ensure Grub2 >>has the current configuration.

<whackity whack>

Thanks,

Skaramanger

---

