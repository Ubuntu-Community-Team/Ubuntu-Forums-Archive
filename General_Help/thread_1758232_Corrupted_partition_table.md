---
title: "Corrupted partition table"
date: 2011-05-14
forum: General Help
---

### Post by pveurshout on 2011-05-14
Hello,

Ever since installing Ubuntu there has been a discrepancy between the info shown by Gparted and the Windows Vista disk management utility. As I never use Vista, I never bothered fixing this thing as it didn't create problems anyway. When I deleted my pre-installed HP_TOOLS partition (because I needed to create another primary partition), I got a GRUB rescue screen at reboot. Using the Maverick LiveCD I found out that both my / and swap partitions had turned into unallocated space. Note that these were inside an extended partition (which still exists, including two other logical volumes).

I've searched through the forums and the internet, and found out that it should be possible to recover my 'lost' / partition - but I don't know where to start. Does anyone know how to do this? Below I have provided an overview of my partitions, indicating those which have turned into unallocated space

-------
sda1: Vista (NTFS)
sda2: Extended
[LIST]sda7: Ubuntu (ext4) [now: unallocated space][/LIST]
[LIST]sda8: swap [now: unallocated space][/LIST]
[LIST][there was some unallocated space inbetween][/LIST]
[LIST]sda5: ext3 partition[/LIST]
[LIST]sda6: NTFS partition[/LIST]
[unallocated space - formerly: HP_TOOLS partition which I deliberately deleted]
sda3: Vista Recovery partition
-------

sda7 and sda8 should still be out there - somewhere.. :confused:

Thanks a LOT for your help!

---

### Post by blueridgedog on 2011-05-14
Can you post the output of 

```
sudo fdisk -l
```

While booted on the live CD?

Though I have not seen the fdisk output, if the partition is missing, I would use testdisk to attempt to recover it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by pveurshout on 2011-05-14
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6687    53711276    7  HPFS/NTFS
/dev/sda2            7471       29160   174223361    5  Extended
/dev/sda3           29226       30401     9439232    7  HPFS/NTFS
/dev/sda5           11423       26482   120969324   83  Linux
/dev/sda6           26483       29160    21509120    7  HPFS/NTFS

```

Note that /dev/sda3 is actually located at the very end of the disk. The lost partitions are located in /sda2, just before /sda5.

---

### Post by pveurshout on 2011-05-14
I read through the TestDisk documentation and am now ready to use it - but I can' t seem to get it started from the LiveCD. Using apt-get I get the error "Unable to locate package testdisk". Do you happen to know where to find the program?

---

### Post by Rubi1200 on 2011-05-14
Check Software Sources and make sure universe and multiverse are enabled then run apt-get update before installing Testdisk.

---

### Post by pveurshout on 2011-05-14
Thanks! Now let's see if it works :)

---

### Post by pveurshout on 2011-05-14
I get a message that 'hidden sectors are present'. Should I simply continue?
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - ATA ST9250421AS

Hidden sectors are present.

size       488397168 sectors
user_max   488397168 sectors
dco        488397168 sectors
Device Configuration Overlay (DCO) present.






[ Continue ]  Continue even if there are hidden data

```

---

### Post by pveurshout on 2011-05-14
Testdisk is now done with its Deeper Search and seems to find all my partitions in a correct manner. However, because there was an inconsistency between Vista and Ubuntu with respect to considering partitions as Primary or Logical, I must now choose one of these layouts to write to the disk using TestDisk. (they are all considered as Deleted, so I must assign P and L characteristics manually anyway)

Vista treated the two hidden partitions (see my first post) as separate primary partitions (don't ask me why/how it managed to show 6 primary partitions), whereas Ubuntu included these as a part of the extended partition (sda2). Regardless of this issue, everything worked perfectly fine under both OSs. I think I should go for the Ubuntu layout - any different ideas?

---

### Post by pveurshout on 2011-05-14
Allright, I decided to go with the Ubuntu structure, but unfortunately I keep getting the same GRUB error. Will now try to update GRUB - perhaps my partition numbering was altered in the process.

---

### Post by pveurshout on 2011-05-14
IT WORKS! blueridgedog and Rubi1200: thanks for your help!

Before I mark this thread as solved, there is one small remaining issue. Because my partition numbering was altered (sda5 became sda7 etc.) I had to reconfigure my auto-mount options using Storage Device Manager. When opening the /etc/fstab file, however, I noticed that my root / file system was no longer listed (neither was swap). fstab now only lists two of my data partitions - is this normal?

---

### Post by LostFarmer on 2011-05-14
You may have to edit /etc/fstab if UUID or Name is not used for the /dev/sdax.

> Device Configuration Overlay (DCO) present.
That might present a problem if indeed an overlay is present in the MBR, that would indicate the BIOS is old and can not see the whole hdd. Once linux is loaded there would be no problem but for grub (?).  If Vista came with the comp. then the bios should be new , after 2001.

> Vista treated the two hidden partitions (see my first post) as separate  primary partitions (don't ask me why/how it managed to show 6 primary  partitions)  If that was the case then it adds a new problem (maybe), it would indicate the new partition table is in use  [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by Rubi1200 on 2011-05-14
I am glad you got things sorted out (surely after more than a few nervous moments :)).

Post the boot script so we can take a look at the new situation please (can also be done from inside Ubuntu if you want):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by pveurshout on 2011-05-14
> **Rubi1200 said:**
> (...) (surely after more than a few nervous moments :)).

You can say that again;)

> Post the boot script so we can take a look at the new situation please (can also be done from inside Ubuntu if you want):

That would be awesome. I'll run Boot info script and get back with the results ASAP (I'm afraid I gotta run right now). It works for now, so don't hurry and just have a look at it whenever it suits you best. Thanks so much in advance - I really appreciate it! =D>

---

### Post by srs5694 on 2011-05-14
> **pveurshout said:**
> Because my partition numbering was altered (sda5 became sda7 etc.) I had to reconfigure my auto-mount options using Storage Device Manager. When opening the /etc/fstab file, however, I noticed that my root / file system was no longer listed (neither was swap). fstab now only lists two of my data partitions - is this normal?

If root (/) is not specified in /etc/fstab, then the system won't boot (unless Ubuntu is doing something weird I don't know about). The root (/) filesystem *must* be defined. You can add an entry manually. The default entry on an Ubuntu 11.04 system looks something like this:

```
# / was on /dev/sda8 during installation
UUID=43d1353d-6174-4ed4-be30-c24b4cba3d8e  /  ext4  errors=remount-ro 0  1

```

You'll need to change the UUID value; use blkid to identify it, or change it to refer to the device directly, as in:

```
# / was on /dev/sda8 during installation
/dev/sda8  /  ext4  errors=remount-ro 0  1

```

Of course, you'll need to know the device filename either way. You might also need to change the filesystem code (ext4 here) if you use a different filesystem. (The blkid command will identify your filesystem, if that's the case.)

(re: Windows identifying the disk as having six primary partitions.)

[quote=LostFarmer]If that was the case then it adds a new problem (maybe), it would indicate the new partition table is in use  [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)[/quote]

This would be true if the Windows partitioning tools could be trusted. They can't, though. They often report *all* partitions as primary, even when they aren't. I don't know if this is always true or just under certain circumstances. FWIW, my suspicion is that it was the Windows partitioning tool that created this mess in the first place. The Windows Vista and 7 installer's partitioning tool is known to delete extended partitions without informing the user of this fact under certain circumstances. (This seems to be a mutation of a bug in the XP installer that would convert logical partitions into primary partitions without resizing the extended partition.) I haven't tested the tool in Windows itself, but it wouldn't surprise me if it's got the same very serious bug.

My advice: Don't use the Windows partitioning tools for any reason except to resize a Windows boot partition. It's untrustworthy.

---

### Post by LostFarmer on 2011-05-14
> The Windows Vista and 7 installer's partitioning tool is known to delete  extended partitions without informing the user of this fact under  certain circumstances. So will ubuntu,xubuntu and Igolaqare, all 3 did so during install.

---

### Post by pveurshout on 2011-05-14
> **Rubi1200 said:**
> I am glad you got things sorted out (surely after more than a few nervous moments :)).

Post the boot script so we can take a look at the new situation please (can also be done from inside Ubuntu if you want):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I ran Boot Info Script using the LiveCD and the results are pasted below. Also I think there's something wrong with my swap partition. It is not activated (System Monitor says I'm using "0 bytes of 0 bytes") and when I try to manually activate it using Gparted I get the following error:

```

swapon: /dev/sda6: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda6: pagesize=4096, swapsize=6399459328, devsize=6399451136
swapon: /dev/sda6: last_page 0x17d700000 is larger than actual size of swapspace
swapon: /dev/sda6: swapon failed: Invalid argument

```

Should I simply re-format the swap partition, or is something else up?

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 1806. But according to the info from fdisk, 
                       sda8 starts at sector 425435136.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   107,422,614   107,422,552   7 HPFS/NTFS
/dev/sda2         120,006,621   468,455,399   348,448,779   f W95 Ext d (LBA)
/dev/sda5         120,006,656   152,037,375    32,030,720  83 Linux
/dev/sda6         152,039,424   164,538,351    12,498,928  82 Linux swap / Solaris
/dev/sda7         183,494,682   425,433,329   241,938,648  83 Linux
/dev/sda8         425,435,136   468,453,375    43,018,240   7 HPFS/NTFS
/dev/sda3         469,507,849   488,386,312    18,878,464   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0BEFF4A84D38A0A9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        C49AA4209AA410CA                       ntfs       HP_RECOVERY                   
/dev/sda5        3c68458b-b10f-4d95-b9c2-89ca658920bc   ext4                                     
/dev/sda6        7d651367-5b70-477a-96ef-8473c2d74705   swap                                     
/dev/sda7        63983304-bba7-4dff-bf8b-94145cea3e88   ext3       Multimedia                    
/dev/sda8        B65CA4D75CA493A1                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro   
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3c68458b-b10f-4d95-b9c2-89ca658920bc ro single 
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
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3c68458b-b10f-4d95-b9c2-89ca658920bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0beff4a84d38a0a9
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set c49aa4209aa410ca
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/sda8	/media/Data	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/sda7	/media/Multimedia	ext3	defaults	0	0



=================== sda5: Location of files loaded by Grub: ===================


  72.5GB: boot/grub/core.img
  75.9GB: boot/grub/grub.cfg
  63.2GB: boot/initrd.img-2.6.35-22-generic
  72.8GB: boot/initrd.img-2.6.35-23-generic
  73.0GB: boot/initrd.img-2.6.35-24-generic
  77.8GB: boot/initrd.img-2.6.35-25-generic
  64.7GB: boot/initrd.img-2.6.35-27-generic
  63.3GB: boot/initrd.img-2.6.35-28-generic
  72.5GB: boot/vmlinuz-2.6.35-22-generic
  72.8GB: boot/vmlinuz-2.6.35-23-generic
  73.3GB: boot/vmlinuz-2.6.35-24-generic
  72.8GB: boot/vmlinuz-2.6.35-25-generic
  72.8GB: boot/vmlinuz-2.6.35-27-generic
  72.9GB: boot/vmlinuz-2.6.35-28-generic
  63.3GB: initrd.img
  64.7GB: initrd.img.old
  72.9GB: vmlinuz
  72.8GB: vmlinuz.old

```

---

### Post by srs5694 on 2011-05-14
> **LostFarmer said:**
> [quote=srs5694]The Windows Vista and 7 installer's partitioning tool is known to delete extended partitions without informing the user of this fact under certain circumstances. So will ubuntu,xubuntu and Igolaqare, all 3 did so during install.[/QUOTE]

Do you have a reference for this, or more details? I've never before heard of this happening, at least not in the way it's been described in this thread. The closest I've heard is that tools based on libparted, including the Ubuntu installer, will *think* that a hard disk is completely unpartitioned if the partition table is damaged. Most people have the sense to stop when they see this, so it's more of an annoyance than a threat, but if you didn't stop, it might overwrite all the disk's partitions with new ones.

[quote=pveurshout]I think there's something wrong with my swap partition. It is not  activated (System Monitor says I'm using "0 bytes of 0 bytes") and when I  try to manually activate it using Gparted I get the following error:

 	Code:
 	swapon: /dev/sda6: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda6: pagesize=4096, swapsize=6399459328, devsize=6399451136
swapon: /dev/sda6: last_page 0x17d700000 is larger than actual size of swapspace
swapon: /dev/sda6: swapon failed: Invalid argument 
Should I simply re-format the swap partition, or is something else up?[/quote]

I recommend you try "swapon" directly, since I'm not sure how GParted is calling it:

```
sudo swapon /dev/sda6
```

If that works, you can add an entry for it to /etc/fstab:

```
UUID=7d651367-5b70-477a-96ef-8473c2d74705  none  swap  sw  0 0
```

If manually using swapon doesn't work, then the swap space has become corrupted in some way. Re-creating the swap will fix the problem:

```

sudo mkswap /dev/sda6
sudo blkid /dev/sda6

```

The blkid command is necessary to learn the new UUID of the swap space, since mkswap will change it. You should use the new UUID in /etc/fstab. Alternatively, you could pass the old UUID with the -U option, as in "sudo mkswap -U 7d651367-5b70-477a-96ef-8473c2d74705 /dev/sda6".

[quote=pveurshout]```
=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/sda8    /media/Data    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda7    /media/Multimedia    ext3    defaults    0    0

```[/quote]

This /etc/fstab is definitely missing the root (/) filesystem entry. Add one as described in my previous post. You might also want to add entries for other filesystems, too, but that's a matter of personal preference. (Your swap partition should definitely be listed here, although if it's not, it just makes the swap go unused; the system will still boot and function normally, aside from the lack of swap space.)

Also, these two entries reference partitions by device filename. This works, but if the partition table changes, the entries might need to be changed. You can substitute UUIDs to make /etc/fstab more robust against such changes.

---

### Post by LostFarmer on 2011-05-14
[srs5694]("http://ubuntuforums.org/member.php?u=1032238")        see post # [http://ubuntuforums.org/showthread.php?t=1723604](http://ubuntuforums.org/showthread.php?t=1723604)  problem #3, any questions will answer on that post.

---

### Post by srs5694 on 2011-05-15
> **LostFarmer said:**
> [srs5694]("http://ubuntuforums.org/member.php?u=1032238")        see post # [http://ubuntuforums.org/showthread.php?t=1723604](http://ubuntuforums.org/showthread.php?t=1723604)  problem #3, any questions will answer on that post.

I've just posted to that thread. I was unable to replicate your problem, but there were enough variables in my test that it's impossible to draw firm conclusions.

---

### Post by pveurshout on 2011-05-15
> **srs5694 said:**
> 
(...)

This /etc/fstab is definitely missing the root (/) filesystem entry. Add one as described in my previous post. You might also want to add entries for other filesystems, too, but that's a matter of personal preference. (Your swap partition should definitely be listed here, although if it's not, it just makes the swap go unused; the system will still boot and function normally, aside from the lack of swap space.)

Also, these two entries reference partitions by device filename. This works, but if the partition table changes, the entries might need to be changed. You can substitute UUIDs to make /etc/fstab more robust against such changes.

Thanks! It works now. I had to recreate the swap space because it had indeed become corrupted.

Should I add / to fstab with the errors=remount-ro option only, or should 'defaults' also be in there?

---

### Post by pveurshout on 2011-05-15
> **srs5694 said:**
> 
My advice: Don't use the Windows partitioning tools for any reason except to resize a Windows boot partition. It's untrustworthy.

Never again will I use Windows for partitioning.. Actually, I touched Windows twice in the past year or so. And twice it messed up my system. Coincidence? I think not. :P

---

### Post by blueridgedog on 2011-05-15
> **pveurshout said:**
> Should I add / to fstab with the errors=remount-ro option only, or should 'defaults' also be in there?

Mine is:

UUID=XXXX /      ext4    errors=remount-ro 0       1

---

### Post by srs5694 on 2011-05-15
> **pveurshout said:**
> Thanks! It works now. I had to recreate the swap space because it had indeed become corrupted.

Should I add / to fstab with the errors=remount-ro option only, or should 'defaults' also be in there?

The "defaults" option just sets the defaults. Anything else sets the defaults with the exception of the other options are specified. The "errors=remount-ro" option causes the filesystem to be mounted in a read-only form if the computer has problems mounting the filesystem. (The default behavior is set in the filesystem metadata itself.) On a normal boot, whether you use this option or not will make no difference whatsoever. Many distributions do *not* use this option in their /etc/fstab files. Presumably the Ubuntu developers thought it was potentially helpful in case of certain types of errors, but that's speculation on my part.

---

### Post by pveurshout on 2011-05-17
> **srs5694 said:**
> The "defaults" option just sets the defaults. Anything else sets the defaults with the exception of the other options are specified. The "errors=remount-ro" option causes the filesystem to be mounted in a read-only form if the computer has problems mounting the filesystem. (The default behavior is set in the filesystem metadata itself.) On a normal boot, whether you use this option or not will make no difference whatsoever. Many distributions do *not* use this option in their /etc/fstab files. Presumably the Ubuntu developers thought it was potentially helpful in case of certain types of errors, but that's speculation on my part.

I set it as errors=remount-ro and it works perfectly :)

As a sort of follow-up question (a new thread would feel like overkill): can fstab deal with mounting devices to hidden folders, or can those at least be contained in the /.path_to/mount_point ? The reason I'm asking is that I'm using symbolic links for the home folders Documents, Pictures, etc. which point to folders on other partitions (but where not each folder has its own partition).

---

### Post by blueridgedog on 2011-05-17
> **pveurshout said:**
> As a sort of follow-up question (a new thread would feel like overkill): can fstab deal with mounting devices to hidden folders, or can those at least be contained in the /.path_to/mount_point ?

Should be no problem.  I too use sym links to Documents and the like.

---

