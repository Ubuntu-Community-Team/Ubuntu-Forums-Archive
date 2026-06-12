---
title: "Corrupted partition table"
date: 2011-01-09
forum: General Help
---

### Post by Howy on 2011-01-09
I have managed to restore my system, partly. Now i have a new problem: my partition table is messed up after that Windows had a spin with it. (It installed its MBR to the first HDD, but i restored Grub2 successfully, and i can boot.)
My belief is that Windows did it, and now it doesnt support overlapping partitions. On install, i had a 250Gb partition as sda1 formatted as Ext4, for backup. Then i had a 750Gb extended one containing the OS on a 250Gb partition formatted to ext4.
Finally, i have a 500Gb partition for storage, also ext4.
This is where the error occurs: the extended partitions is now shown as an own partition in Disk Utility, and i dont want to take the risk of deleting it. In addition, the OS's partition shows up as free, and there is some corrupt partition at the end showing up with like 18 million Tbs.
Before this happened, i added 2 partitions of 5Gb formatted to NTFS. They are put on the start and beginning of the table. I made them in order to repair Windows XP, which failed horribly. Now i want to delete them.
However, one of them has taken the position as sda1, and the other is sda7, the last partition. When i try to delete either of them in Disk Utility, i get this error:
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=1048576
Entering MS-DOS parser (offset=0, size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 5242880000, type 0x07)
new part entry
looking at part 1 (offset 5243928576, size 247494344704, type 0x83)
new part entry
looking at part 2 (offset 252739320832, size 747464819712, type 0x05)
Entering MS-DOS extended parser (offset=252739320832, size=747464819712)
readfrom = 252739320832
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 500102594560, size 495101935616, type 0x83)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
Error: Can't have overlapping partitions.
ped_disk_new() failed

```
So, how can i delete the NTFS partitions, and repair my partition table?
I dont have any idea of what to do, all i want is to restore the partition table back to a more... stable... state.

---

### Post by Quackers on 2011-01-09
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Howy on 2011-01-09
Here you go:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    10,242,047    10,240,000   7 HPFS/NTFS
/dev/sda2          10,242,048   493,629,439   483,387,392  83 Linux
/dev/sda3         493,631,486 1,953,523,711 1,459,892,226   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5    *    493,631,488   957,100,031   463,468,544  83 Linux
/dev/sda6         957,102,080   976,752,639    19,650,560  82 Linux swap / Solaris
/dev/sda7       1,943,760,896 1,953,523,711     9,762,816   7 HPFS/NTFS
/dev/sda4         976,762,880 1,943,758,847   966,995,968  83 Linux

/dev/sda3 overlaps with /dev/sda4

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   377,061,614   377,061,552   7 HPFS/NTFS
/dev/sdb2         377,077,680   390,716,864    13,639,185   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        40F4B34219CEE934                       ntfs       WinMBR                        
/dev/sda2        b3e7fc6a-d673-4267-ba60-d8285551b832   ext4       Backup                        
/dev/sda3: PTTYPE="dos" 
/dev/sda4        bd3d1b40-04cf-4eab-9a40-8a43793a4e1c   ext4       Lagring                       
/dev/sda5        05042069-be03-441a-adaf-07c61f0f579b   ext4                                     
/dev/sda6        c6874d5e-24fe-4d38-b45c-c3cc131fa556   swap                                     
/dev/sda7        0BBB9778245919B8                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2BA95E1E14F9018F                       ntfs       PRESARIO                      
/dev/sdb2        4B6E-6BC0                              vfat       PRESARIO_RP                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /media/Lagring           ext4       (rw)
/dev/sda2        /media/Backup            ext4       (rw)
/dev/sdb1        /media/PRESARIO          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
set locale_dir=($root)/boot/grub/locale
set lang=nb
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro  vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro  vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro  vga=792 splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro single  vga=792 splash
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 2ba95e1e14f9018f
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
	insmod part_msdos
	insmod fat
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 4b6e-6bc0
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda7 during installation
UUID=05042069-be03-441a-adaf-07c61f0f579b  /               ext4  errors=remount-ro    0  1  
# swap was on /dev/sda8 during installation
UUID=c6874d5e-24fe-4d38-b45c-c3cc131fa556  none            swap  sw                   0  0  
/dev/sda1                                  /media/Backup   ext4  defaults             0  0  
/dev/sda5                                  /media/Lagring  ext4  defaults             0  0  

=================== sda5: Location of files loaded by Grub: ===================


 476.2GB: boot/grub/core.img
 257.2GB: boot/grub/grub.cfg
 253.8GB: boot/initrd.img-2.6.35-22-generic
 301.1GB: boot/initrd.img-2.6.35-23-generic
 346.7GB: boot/initrd.img-2.6.35-24-generic
 476.9GB: boot/vmlinuz-2.6.35-22-generic
 477.4GB: boot/vmlinuz-2.6.35-23-generic
 476.5GB: boot/vmlinuz-2.6.35-24-generic
 346.7GB: initrd.img
 301.1GB: initrd.img.old
 476.5GB: vmlinuz
 477.4GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /noguiboot
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=15
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```
sdb is the old partition of my XP installation. It's the one i tried to repair. (It doesn't support the I/O of my current motherboard. I can't move the mouse or use the keyboard. But it does work when using generic drivers in some cases, however it doesn't do so all the time.)

---

### Post by oldfred on 2011-01-09
I found this in my notes, if it changes partition numbers, you may have to reinstall grub and edit fstab:

Just to be on safe side I might make a copy of the partition table and save it to an external device.

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Extended partition linking to another extended partition
Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. 

More detail on fdisk commands.
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

Then if that does not work I would use testdisk to review/recover partitions.

---

### Post by srs5694 on 2011-01-09
As near as I can tell, this is the problem, on /dev/sda:

```

/dev/sda3         493,631,486 1,953,523,711 1,459,892,226   5 Extended
Extended  partition  linking to another extended partition

/dev/sda3 overlaps with /dev/sda4

```

There's at least one problem, possibly two.

First, /dev/sda3 and /dev/sda4 (an extended and a primary partition) overlap. More precisely, the primary /dev/sda4 resides entirely within the extended /dev/sda3. This is illegal, and it will be tricky to fix because you have no spare primary partitions, so the only real solution is to convert /dev/sda4 into a logical partition. I don't know of any disk utility that's designed explicitly to do this, but I do know of two ways to do it (see below).

Second, the comment about an extended partition pointing to another extended partition suggests that you've got a logical partition that's marked as an extended partition. This is illegal. If the embedded extended partition has any logical partitions defined that you want to keep, it's unclear if they're present in the output you see or if they could be recovered with anything short of [TestDisk.](http://www.cgsecurity.org/wiki/TestDisk)

As to solutions, one possibility is to use sfdisk. Type this command:

```

sudo sfdisk -d /dev/sda > sda.parts

```

This command will generate a file called sda.parts that contains the partition table data. Edit it (you'll need to type "sudo chown yourusername: sda.parts", where "yourusername" is your username, to give yourself ownership of the file). Review the file to be sure all your partitions are listed. Change "/dev/sda4" to "/dev/sda8". You can then write it back to disk:

```

sudo sfdisk -f /dev/sda < sda.parts

```

This should fix the problem; however, it's possible you'll just make matters worse if you're not careful. Post the sfdisk output here before proceeding if you're uncertain of anything at all.

A second approach to fixing the problem is to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program. It was designed to work on the new GPT disks rather than the older MBR disks, but it can convert back and forth, and because GPT doesn't use extended or logical partitions, converting back and forth will clear away the extended/logical problems you've got. To fix the problem in this way, follow these steps:


[list=1]
[*]Download GPT fdisk from its [Sourceforge downloads page.](https://sourceforge.net/projects/gptfdisk/files/) Do not use the version in the Ubuntu repositories; it's embarrassingly old and has bugs that could wipe out your partitions if you use it as I'm about to suggest!
[*]Launch gdisk on the disk by typing "sudo gdisk /dev/sda"
[*]Type "p" to view your partition table. Verify that all the partitions are present.
[*]Type "v" to verify your partitions. If it reports any overlapping partitions, either post back here with details or try to work out what's overlapping and what you can safely delete.
[*]Type "r" to enter the recovery & transformation menu.
[*]Type "g" to convert the (internally converted) GPT data structures back to MBR form. The program displays the partitions as it will write them to disk. You can adjust primary/logical assignment and change type codes. You'll have to adjust the type codes of the Linux partitions from 07 to 83. Be sure the Windows boot partition is primary.
[*]When you're satisfied with your changes, type "0" to accept them, then "Y" to write them.
[/list]


Either approach poses risks. Either could make matters worse. You might have to re-install your boot loader, particularly if you use GPT fdisk. If you try either method and get confused or don't understand something, post back before proceeding further.

Good luck!

---

### Post by srs5694 on 2011-01-09
I don't think oldfred's suggestion of the fdisk commands will work; however, I'm not positive of that, and if it does work, it might be a bit less risky than either of the methods I suggested. Thus, it's probably worth trying oldfred's method first.

---

### Post by Howy on 2011-01-09
Nice to see that someone has answered, but i can't take the risk of messing up my system until the end of the week. But i will get back to it. ;-)
Thanks for replying. You will get feedback on next Saturday.

---

### Post by Howy on 2011-07-07
Ok, so I'm resuming trying to repair this problem. (Yes, I've been living with it for a half year. So far, I think it makes me unable to use automount.)
I've backup up my partition table to a USB stick using sfdisk, but I'm unsure about what I'm going to do next.
Do I only have to change sda4 to sda8 to fix it?
I've backed up every single file on my system to a nice and sturdy drive, but sda4 contains a good deal of my photos and other data. (If something goes wrong, I'd worry even though I've backed it up.)
Do you recommend writing the partition table directly from within Ubuntu, or should I do it otherwise? (I have a LiveCD with Lucid)

---

### Post by srs5694 on 2011-07-07
In waiting six months, you happen to have waited long enough for a new tool to become available to fix the problem: My [FixParts](http://www.rodsbooks.com/fixparts/) program should make quick work of the problem. Follow the instructions on its Web page and be very sure that all your partitions (except the extended partition, which it deletes and then re-creates from scratch) are present as either "primary" or "logical" (*not* "omitted") before you use the "w" option.

---

### Post by Howy on 2011-07-07
I'll certainly try that tool. :)

Right now, when I reboot, it will use the new partition table. Wish me luck, will you? :P

Many thanks to you, good sir! :D
I just got my partition table back, and oh boy!
I feel like a hobo who has won a million dollars in a lottery... xD
Now, all I have to do is setup GRUB to work with the new partition table.

Ok... problem:
My OS's partition doesn't show up in /dev/, but it does in GParted. I believe it shows up in GParted because I wrote the partition table to it with FixParts, but I don't know.
It says:
```
root@ubuntu:/home/ubuntu# e2fsck -b 8193 /dev/sda5
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```I'm not too worried as I have it all backed up. Except for /dev, /proc and /sys.
I still believe that the partition is there, it's just that it's not listed in /dev.
And if I can't recover it, do anyone know how I can make new /dev, /proc and /sys directories?
(I'll be rebooting the liveCD to check the partition and try to recover it. Be right back.)

Ok, I'm sure about one thing: the partition is intact. But the superblock isn't. GParted can fetch information about the drive and so on, but it still won't show up in /dev/.
Is it possible to recover the superblock when you know what sectors it is located on and what type it is?

I'm considering to go for ddrescue.. But does it require a block device as target?

---

### Post by srs5694 on 2011-07-07
First, are you positive that /dev/sda is the same /dev/sda you showed earlier? Sometimes disk identities (/dev/sda, /dev/sdb, etc.) change between boots. If that happened to you, /dev/sda wouldn't have a /dev/sda5, since /dev/sda would actually be your 200 GB disk with just two primary partitions, not your 1 TB disk.

Second, have you rebooted after using FixParts? If not, that could explain it, since FixParts, like fdisk and several other tools, can make changes to partition tables that the kernel might not detect until after a reboot. OTOH, /dev/sda had a /dev/sda5 initially, and it'd be the same /dev/sda5 in both cases, so I'd expect you'd still be able to access it.

If you have rebooted, then I suggest seeing if fdisk can see the partitions. If it sees them all fine, then type "w" in fdisk to rewrite the partition table -- but *don't* type "w" if fdisk doesn't see all your partitions! If fdisk sees your partitions correctly, it may write the partitions in a slightly different way, which the kernel may find more palatable. You could do something similar with an sfdisk backup ("sfdisk -d /dev/sda > parts.txt" to back up, followed by "sfdisk -f /dev/sda < parts.txt" to restore).

Don't worry about /dev, /proc, and /sys; those are created dynamically by Linux, rather than stored as partitions on the hard disk, so partitioning tools don't affect them.

---

### Post by Howy on 2011-07-07
Hmm... Yes, fdisk does show them :)
I'll just see if they're located on the same cylinders as the original partition table.
This is what it says:
```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000599b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5120000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             638       30728   241693696   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3          120994      121602     4881408    7  HPFS/NTFS
/dev/sda4           30728      120994   725063680+   f  W95 Ext'd (LBA)
/dev/sda5   *       30728       59577   231734272   83  Linux
/dev/sda6           59577       60801     9825280   82  Linux swap / Solaris
/dev/sda7           60801      120994   483497984   83  Linux

Partition table entries are not in disk order
```Should I be worried about sda1 and sda2?

And now, I don't have the 200Gb HDD inside. I removed it to get rid of the temptation of ever booting it again. (On this hardware)

Ok... I rewrote the partition table. But I noticed something at boot. The /dev/sda5 entry gets removed. I don't know why, but it just does. When the liveCD is freshly booted, I can ls /dev/sd* and see it, but a few secs later it's not there.
It's clear that the partition is still there, but I don't know why it just disappears like that.
Even the kernel detects it like normal in dmesg. The partition is far from being deleted.

---

### Post by srs5694 on 2011-07-07
That's very strange. If the /dev/sda5 file exists and then disappears, there ought to be a message about the removal in dmesg output. If you can find such a message, maybe it'll provide a clue about what's going on.

The only oddity I see in your fdisk output is that /dev/sda5 is marked with a boot flag. Normally only primary partitions should have such flags; however, to the best of my knowledge the Linux kernel ignores that flag, so it shouldn't have any effect. Nonetheless, you could try removing it (with the "a" option in fdisk) and then re-write the partition table without that flag.

As to the "does not end on cylinder boundary" messages, you can ignore them. They're warning you about a partition alignment issue that's been irrelevant for over a decade. Today, partitions are typically aligned on 1 MiB boundaries rather than the old cylinder boundaries. The very latest versions of fdisk (more recent than what's included in Ubuntu 11.04) no longer produce such warnings, at least not by default.

One other comment: You might want to examine the partition table with sector precision rather than cylinder precision. Again, this is because cylinders are no longer a relevant unit of measure for most purposes. There's a slim chance that there's some oddity in your partition table that will turn up if you display it in sector values.

---

### Post by Howy on 2011-07-07
Ok, I've checked it with sectors. This is it:
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 10240000, Id= 7, bootable
/dev/sda2 : start= 10242048, size=483387392, Id=83
/dev/sda3 : start=1943760896, size=  9762816, Id= 7
/dev/sda4 : start=493631487, size=1450127361, Id= f
/dev/sda5 : start=493631488, size=463468544, Id=83, bootable
/dev/sda6 : start=957102080, size= 19650560, Id=82
/dev/sda7 : start=976762880, size=966995968, Id=83
```I don't think there's anything wrong with this. But you say that a having a bootable, logical partition isn't normal? I think I set up too many partitions when setting up my system, then... :p
But it hasn't been a problem for me, and GRUB hasn't complained.

I think I'll have to dig in some logs to get to the bottom of why the partition disappears.

Ok, I really don't understand this. Every log in /var/log/ says that /dev/sda5 was registered and nothing about removing it. I'm getting tired of this...

Halleluja! I caught the partition! :D
I opened up dmesg | tail -f to look for any upcoming kernel messages, but there were none.
Then I entered ls /dev/sd*, sda5 was there. After a couple of minutes, it's still there. :) (And it is right now, too)
So, right now I'll chroot into it and restore GRUB, and I'll hopefully live happily ever after.
If I can make it work this time...

The nightmare is finally over, and I can sleep safely tonight, by the knowledge that I not only have a clean partition table, but I also have automounting back. :)
Thanks for all the help, srs5694. :)

---

### Post by srs5694 on 2011-07-07
I'm glad it seems to be working now. I'm puzzled about why it didn't for a while, though. If the problem recurs, it might be worth using sfdisk to move the start point of the extended partition back a bit and extending its length appropriately. It's conceivable that the tight fit between it and the first logical partition is causing problems, although I've never before heard of a tight fit like that causing problems. If you need explicit instructions on how to do this, just say so.

As to bootable logical partitions, it's just the boot *flag* in the partition table on a logical partition that's unusual. GRUB and Linux both ignore the boot flag; AFAIK, only some boot loaders, such as the DOS/Windows MBR-resident boot loader, use it for anything. Thus, a bootable Linux partition often lacks a boot flag and it still boots fine.

---

### Post by Howy on 2011-07-08
Hmm... I guess I'm a bit old-fashioned to use the boot-flag, then. :p

I'll certainly report back in this thread if it ever should recur. (I hope not. I just love the way Unity shows my mounted devices. :) )

---

