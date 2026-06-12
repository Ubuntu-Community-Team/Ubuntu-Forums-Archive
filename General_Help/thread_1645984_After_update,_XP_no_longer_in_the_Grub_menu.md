---
title: "After update, XP no longer in the Grub menu"
date: 2010-12-15
forum: General Help
---

### Post by Coco999 on 2010-12-15
I have a dual syatem featuring both XP and Ubuntu, with choice at the grub menu. But after the last update(s), XP no longer appears in the grub menu. I do need XP for a few tasks. What can I do? My Ubuntu is 10.04

---

### Post by NCLI on 2010-12-15
> **Coco999 said:**
> I have a dual syatem featuring both XP and Ubuntu, with choice at the grub menu. But after the last update(s), XP no longer appears in the grub menu. I do need XP for a few tasks. What can I do? My Ubuntu is 10.04

Open a terminal, then run this command:
```
gksudo update-grub
```

Post the output here, then try rebooting.

---

### Post by Coco999 on 2010-12-15
> **NCLI said:**
> Open a terminal, then run this command:
```
gksudo update-grub
```

Post the output here, then try rebooting.

Thank you, NCLI. So I did, got no output at all, tried rebooting and got the same trouble. Any suggestion?

---

### Post by sikander3786 on 2010-12-15
As you said, I hope Ubuntu is not installed inside Windows using the Wubi installer and it is a proper dual boot setup. It would just be better to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup, might indicate the problem so we might be able to advise more efficiently.

When posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

@**NCLI**: I am not sure if it would work with *gksudo*? I think it should be *sudo update-grub* instead.

---

### Post by Coco999 on 2010-12-15
> **sikander3786 said:**
> As you said, I hope Ubuntu is not installed inside Windows using the Wubi installer and it is a proper dual boot setup. It would just be better to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup, might indicate the problem so we might be able to advise more efficiently.

When posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

@**NCLI**: I am not sure if it would work with *gksudo*? I think it should be *sudo update-grub* instead.

Thank you, sikander3786. It is indeed a proper dual boot setup. I did as advised and got a longish RESULTS.txt file that I copy and paste in full here. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda2 starts at sector 0. But according to the info 
                       from fdisk, sda2 starts at sector 61432686.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 starts at sector 0. But according to the info 
                       from fdisk, sda3 starts at sector 112631715.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 270612338 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 0. But according to the info 
                       from fdisk, sda5 starts at sector 174064338.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 271234562 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1    *             63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sda2          61,432,686   112,631,714    51,199,029   b W95 FAT32
/dev/sda3         112,631,715   174,064,274    61,432,560   b W95 FAT32
/dev/sda4         174,064,275   312,576,704   138,512,430   5 Extended
/dev/sda5         174,064,338   270,325,754    96,261,417   b W95 FAT32
/dev/sda6         270,325,818   310,729,229    40,403,412  83 Linux
/dev/sda7         310,729,293   312,576,704     1,847,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7C95-1978                              vfat       WDC1                          
/dev/sda2        5141-E757                              vfat       WDC2                          
/dev/sda3        508C-CCA4                              vfat       WDC3                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        50E6-B14E                              vfat       WDC4                          
/dev/sda6        b79c4293-976a-4962-a852-2e0fae9f084d   ext4                                     
/dev/sda7        df72390c-4ec3-421e-a16a-f0bc4417cacb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7c95-1978
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b79c4293-976a-4962-a852-2e0fae9f084d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=df72390c-4ec3-421e-a16a-f0bc4417cacb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 138.8GB: boot/grub/core.img
 143.6GB: boot/grub/grub.cfg
 149.1GB: boot/initrd.img-2.6.31-21-generic
 147.4GB: boot/initrd.img-2.6.32-21-generic
 148.1GB: boot/initrd.img-2.6.32-22-generic
 149.2GB: boot/initrd.img-2.6.32-23-generic
 155.4GB: boot/initrd.img-2.6.32-24-generic
 155.0GB: boot/initrd.img-2.6.32-25-generic
 156.0GB: boot/initrd.img-2.6.32-26-generic
 146.0GB: boot/vmlinuz-2.6.31-21-generic
 149.1GB: boot/vmlinuz-2.6.32-21-generic
 147.7GB: boot/vmlinuz-2.6.32-22-generic
 151.8GB: boot/vmlinuz-2.6.32-23-generic
 153.3GB: boot/vmlinuz-2.6.32-24-generic
 154.3GB: boot/vmlinuz-2.6.32-25-generic
 155.1GB: boot/vmlinuz-2.6.32-26-generic
 156.0GB: initrd.img
 155.0GB: initrd.img.old
 155.1GB: vmlinuz
 154.3GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-15
There are multiple problems in your output. Grub2 is installed in the boot sector of every partition except the Win XP one. And there are Wubi files also, I don't know if they were to be intended there or not.

We need to go step by step.

First of all, purge and re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And let us know if you are able to boot Windows or not. Otherwise, you might need to fixmbr for Win XP. It would be even better that once your re-install Grub as mentioned in the other thread, re-run the boot script and post the output once more.

---

### Post by NCLI on 2010-12-15
> **sikander3786 said:**
> As you said, I hope Ubuntu is not installed inside Windows using the Wubi installer and it is a proper dual boot setup. It would just be better to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your setup, might indicate the problem so we might be able to advise more efficiently.

When posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

@**NCLI**: I am not sure if it would work with *gksudo*? I think it should be *sudo update-grub* instead.

It works, I test every command I post ;)

---

### Post by Coco999 on 2010-12-15
> **sikander3786 said:**
> There are multiple problems in your output. Grub2 is installed in the boot sector of every partition except the Win XP one. And there are Wubi files also, I don't know if they were to be intended there or not.

We need to go step by step.

First of all, purge and re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And let us know if you are able to boot Windows or not. Otherwise, you might need to fixmbr for Win XP. It would be even better that once your re-install Grub as mentioned in the other thread, re-run the boot script and post the output once more.

I did as you told me. starting from step 2 as I'm working within the Ubuntu 10.04 installed. I got this:
```
coco@coco-desktop:~$ apt-get update   # ***
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
coco@coco-desktop:~$ 

```

I am at a loss what to do next. I wonder why do I have to go through this trouble. Until the last updates all worked properly, for years. Thank you for your help.

---

### Post by sikander3786 on 2010-12-15
You need root privileges for that. Type *sudo* in the beginning of every command.

---

### Post by wilee-nilee on 2010-12-15
> **NCLI said:**
> It works, I test every command I post ;)

Gksudo is for a graphic display like gparted.

---

### Post by Coco999 on 2010-12-15
> **sikander3786 said:**
> You need root privileges for that. Type *sudo* in the beginning of every command.

I did as instructed and before exit I saw a sort of grub menu with an XP option included. But upon restart, the grub menu doesn't include XP, so I am at point zero again. I ran again
 sudo bash ~/Desktop/boot_info_script*.sh 
I got a new **results** as follows. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda2 starts at sector 0. But according to the info 
                       from fdisk, sda2 starts at sector 61432686.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 starts at sector 0. But according to the info 
                       from fdisk, sda3 starts at sector 112631715.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 270612338 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 0. But according to the info 
                       from fdisk, sda5 starts at sector 174064338.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 271234562 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1    *             63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sda2          61,432,686   112,631,714    51,199,029   b W95 FAT32
/dev/sda3         112,631,715   174,064,274    61,432,560   b W95 FAT32
/dev/sda4         174,064,275   312,576,704   138,512,430   5 Extended
/dev/sda5         174,064,338   270,325,754    96,261,417   b W95 FAT32
/dev/sda6         270,325,818   310,729,229    40,403,412  83 Linux
/dev/sda7         310,729,293   312,576,704     1,847,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7C95-1978                              vfat       WDC1                          
/dev/sda2        5141-E757                              vfat       WDC2                          
/dev/sda3        508C-CCA4                              vfat       WDC3                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        50E6-B14E                              vfat       WDC4                          
/dev/sda6        b79c4293-976a-4962-a852-2e0fae9f084d   ext4                                     
/dev/sda7        df72390c-4ec3-421e-a16a-f0bc4417cacb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7c95-1978
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b79c4293-976a-4962-a852-2e0fae9f084d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=df72390c-4ec3-421e-a16a-f0bc4417cacb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 138.8GB: boot/grub/core.img
 143.7GB: boot/grub/grub.cfg
 149.1GB: boot/initrd.img-2.6.31-21-generic
 147.4GB: boot/initrd.img-2.6.32-21-generic
 148.1GB: boot/initrd.img-2.6.32-22-generic
 149.2GB: boot/initrd.img-2.6.32-23-generic
 155.4GB: boot/initrd.img-2.6.32-24-generic
 155.0GB: boot/initrd.img-2.6.32-25-generic
 156.0GB: boot/initrd.img-2.6.32-26-generic
 146.0GB: boot/vmlinuz-2.6.31-21-generic
 149.1GB: boot/vmlinuz-2.6.32-21-generic
 147.7GB: boot/vmlinuz-2.6.32-22-generic
 151.8GB: boot/vmlinuz-2.6.32-23-generic
 153.3GB: boot/vmlinuz-2.6.32-24-generic
 154.3GB: boot/vmlinuz-2.6.32-25-generic
 155.1GB: boot/vmlinuz-2.6.32-26-generic
 156.0GB: initrd.img
 155.0GB: initrd.img.old
 155.1GB: vmlinuz
 154.3GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-15
You mean XP is not listed in the Grub menu? Whereas grub.cfg has got an entry for that.

> menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7c95-1978
    drivemap -s (hd0) ${root}
    chainloader +1
}


---

### Post by Coco999 on 2010-12-15
> **sikander3786 said:**
> You mean XP is not listed in the Grub menu? Whereas grub.cfg has got an entry for that.

I'm not sure what do you mean here or what to do next.

I ran grub-config and got as follows.

```

coco@coco-desktop:~$ sudo update-grub 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
coco@coco-desktop:~$ 

```

As you see, it found XP, but to no avail. Please do help me.

---

### Post by sikander3786 on 2010-12-15
If you've got a Windows install disc, the only suggestion I've got for now is to boot it and try fixmbr.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Once you are able to boot Windows XP successfully, re-install Grub from an Ubuntu Live CD/USB.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by oldfred on 2010-12-15
Are you scrolling down on your grub boot menu?

The box for the grub menu listings only shows so many lines. IF you have a tiny arrow you have more entries than shown.

You have a long list of kernels, so you have many entries. You may also want to houseclean out older kernels and only keep current and one older known working one.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by Coco999 on 2010-12-15
I'm sorry, but the more I do, the more lost I become. Just in case, I came across the following.

```
&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; The grub-pc package is being upgraded.  This menu allows you to select    &#8593; 
 &#9474; which devices you'd like grub-install to be automatically run for, if     &#9646; 
 &#9474; any.                                                                      &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; It is recommended that you do this in most situations, to prevent the     &#9618; 
 &#9474; installed GRUB from getting out of sync with other components such as     &#9618; 
 &#9474; grub.cfg or with newer Linux images it will have to load.                 &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,    &#9618; 
 &#9474; it is often a good idea to install GRUB to all of them.                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Note: It is possible to install GRUB to partition boot records as well,   &#9618; 
 &#9474; and some appropriate partitions are offered here.  However, this forces   &#9618; 
 &#9474; GRUB to use the blocklist mechanism, which makes it less reliable, and    &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
```

From this on, nothing happens again in that terminal. Selecting <Ok> and pushing Enter has no effects. If you want a terminal you have to open a new one.

If that means anything for somebody, please tell me. I wonder why they issue updates, that later on require this elaborate fixing, which not everybody can do.

---

### Post by Coco999 on 2010-12-15
> **oldfred said:**
> Are you scrolling down on your grub boot menu?

The box for the grub menu listings only shows so many lines. IF you have a tiny arrow you have more entries than shown.

You have a long list of kernels, so you have many entries. You may also want to houseclean out older kernels and only keep current and one older known working one.



Thank you oldfred, it was there. By scrolling I could see it and use it to boot. There is the tiny arrow alright. Perhaps it has always been there, who can know now? With time, I'll remove some of the older versions, althogh scrolling is easy enough.

Thank you as well to sikander3786 and the other friends who helped me

---

