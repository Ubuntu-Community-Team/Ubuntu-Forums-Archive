---
title: "Additional Win 7 partition broke my Ubuntu Grub"
date: 2010-06-13
forum: General Help
---

### Post by OOzypal on 2010-06-13
Hello,

I have Ubuntu installed side by side with Win7.

My Ubuntu partition was (hd0,6). Then I created one Win 7 partition using Win7 before my Ubuntu partition. Win 7 pushed my Ubuntu partition to (hd0,7). 

When I start Ubuntu, I get an error ```
error: unknown filesystem
grub rescue>
```

Now, when I do this 
```

grub rescue> set
prefix=(hd0,6)/boot/grub
root=hd0,6

```

The following command show my Ubuntu directory ok
```

grub rescue> ls (hd0,7)/
./ ../ lost+found/ var/ etc/ media/ bin/ boot/ dev/ home/ etc...... 

```
How can I change these settings so grub looks for boot data in partition (hd0,7)

---

### Post by wilee-nilee on 2010-06-13
Boot stuff is best approached with the script in my sig.

---

### Post by OOzypal on 2010-06-13
Hello,
I attached my file result file. Can you help.

I don't have Ubuntu CD but I have Backtrack 4. I think I can fix through this BT4.

Thx

---

### Post by wilee-nilee on 2010-06-13
I'm going to put it on the page for all to see.;) Hold on.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 233. But according to the info from fdisk, 
                       sda5 starts at sector 279001088.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76692ca8

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    34,812,854    34,810,807  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     34,812,855   279,000,854   244,188,000   7 HPFS/NTFS
/dev/sda3         279,001,086   976,773,119   697,772,034   f W95 Ext d (LBA)
/dev/sda5         279,001,088   532,336,639   253,335,552   7 HPFS/NTFS
/dev/sda6         532,338,688   547,287,039    14,948,352   7 HPFS/NTFS
/dev/sda7         547,289,088   959,277,055   411,987,968  83 Linux
/dev/sda8         959,279,104   976,773,119    17,494,016  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 263 MB, 263061504 bytes
8 heads, 32 sectors/track, 2007 cylinders, total 513792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  97       513,791       513,695   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        2A948D2E948CFD97                       ntfs       OS                            
/dev/sda5        9890AF6A90AF4E16                       ntfs       Data                          
/dev/sda6        16B29C20B29C0701                       ntfs       BT4                           
/dev/sda7        a31f8705-b575-4b7e-9632-2ecded42c263   ext4                                     
/dev/sda8        636208c8-36cf-42cd-b6f4-7e3f7705de43   swap                                     
/dev/sdb1        E0FD-1813                              vfat       BOEING                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /media/cdrom0            iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/s                 vfat       (rw)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
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
search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a31f8705-b575-4b7e-9632-2ecded42c263 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a31f8705-b575-4b7e-9632-2ecded42c263 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a31f8705-b575-4b7e-9632-2ecded42c263 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a31f8705-b575-4b7e-9632-2ecded42c263 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a31f8705-b575-4b7e-9632-2ecded42c263
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 2a948d2e948cfd97
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a31f8705-b575-4b7e-9632-2ecded42c263 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=636208c8-36cf-42cd-b6f4-7e3f7705de43 none            swap    sw              0       0

/dev/sda2 /media/OS ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5 /media/Data ntfs-3g defaults,locale=en_US.utf8 0 0

=================== sda7: Location of files loaded by Grub: ===================


 299.6GB: boot/grub/core.img
 323.6GB: boot/grub/grub.cfg
 299.7GB: boot/initrd.img-2.6.32-21-generic
 300.3GB: boot/initrd.img-2.6.32-22-generic
 299.6GB: boot/vmlinuz-2.6.32-21-generic
 299.8GB: boot/vmlinuz-2.6.32-22-generic
 300.3GB: initrd.img
 299.7GB: initrd.img.old
 299.8GB: vmlinuz
 299.6GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-06-13
The uuid is correct, but as you said grub is looking for it in sda6 and it is sda7 now. I suspect if you burned a supergrub disc or reloaded the mbr and mounted sda7 from the grub2 wiki to get in, a few commands would get it going. I'm really not sure though. Since the script is up hopefully somebody knows some fixes. You need to have a disc of whatever distro your running, especially if you have grub2, and need the actual distro cd to reload something.

I don't know the parameters of backtrack others may as far as using it for help.

---

### Post by john newbuntu on 2010-06-13
Try these commands at rescue prompt:

```
ls -l (hd0,7)/
```You would ordinarily see the /boot directory as you have already shown. Keep typing:

```
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro quiet splash
initrd /initrd.img
boot

```Should you manage to get in this way, please run "sudo update-grub".

If you still run into boot problems, you will have to check your /etc/fstab for the existence of device names instead of UUIDs.

---

### Post by wilee-nilee on 2010-06-13
> **john newbuntu said:**
> Try these commands at rescue prompt:

```
ls -l (hd0,7)/
```You would ordinarily see the /boot directory as you have already shown. Keep typing:

```
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro quiet splash
initrd /initrd.img
boot

```Should you manage to get in this way, please run "sudo update-grub".

If you still run into boot problems, you will have to check your /etc/fstab for the existence of device names instead of UUIDs.

Thats what I was thinking just getting in, and running the grub-update would probably get it back in shape.

Supergrub would be the easiest or reloading the mbr and mounting sda7 from a live CD.

---

### Post by OOzypal on 2010-06-13
I just inserted my Ubuntu 10.4 CD & clicked on Try Ubuntu. Then opened terminal but I can not run grub

How can I run grub

---

### Post by wilee-nilee on 2010-06-13
> **OOzypal said:**
> I just inserted my Ubuntu 10.4 CD & clicked on Try Ubuntu. Then opened terminal but I can not run grub

How can I run grub

Follow this set of instructions to reload the MBR and mount sda7. If it seems confusing don't run it and I will post the codes. So sda=mbr sda7 in the partition to mount.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
The key is to run sudo update grub if Ubuntu reloads.

---

### Post by OOzypal on 2010-06-13
Bingo!

everything is working now.

Thank you all

---

### Post by wilee-nilee on 2010-06-13
> **OOzypal said:**
> Bingo!

everything is working now.

Thank you all

Hey thanks to john newbuntu eh, save that grub2 wiki.;)

---

### Post by MichealH on 2010-06-13
The Grub2 wiki is a good way of restoring in the future, I recommend bookmarking it.

---

