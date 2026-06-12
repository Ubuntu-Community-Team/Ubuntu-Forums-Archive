---
title: "Ubuntu 10.04 Dual Boot Help!.."
date: 2010-07-02
forum: General Help
---

### Post by zeromx on 2010-07-02
Hey everyone,
Im trying to do a dual boot setup Ubuntu 10.04 x64 and Windows 7 x64, I hope someone can help.

I have 3 hdd's, 
sda - 500gb
sdb - 1TB (downloads drive)
sdc - 500gb

Here is a list in order what i did,
> formatted all 2 hdd's (sda, sdc)
> installed Ubuntu 10.04 x64 on sdc
> then installed windows 7 x64 on sda
> now when i try to select boot from sdc it just gives me a blank screen.

any help greatly appreciated...

---

### Post by zeromx on 2010-07-03
Bump, Anyone?...

---

### Post by Rubi1200 on 2010-07-03
Hi,
Windows is quite fussy about its bootloader, so if you installed Windows AFTER Ubuntu you will have a problem.

You need to boot your computer using the Ubuntu CD and instead of installing use the option to try Ubuntu in live mode.

Then click on the link at the bottom of my post, follow the instructions there and post the results back here.

---

### Post by zeromx on 2010-07-03
> **Rubi1200 said:**
> Hi,
Windows is quite fussy about its bootloader, so if you installed Windows AFTER Ubuntu you will have a problem.

You need to boot your computer using the Ubuntu CD and instead of installing use the option to try Ubuntu in live mode.

Then click on the link at the bottom of my post, follow the instructions there and post the results back here.

Below is the results
> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   940,922,879   940,920,832  83 Linux
/dev/sdc2         940,924,926   976,773,119    35,848,194   5 Extended
/dev/sdc5         940,924,928   976,773,119    35,848,192  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CA7815E87815D3D3                       ntfs       System Reserved               
/dev/sda2        A49C18249C17F012                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        180C168D0C1665D2                       ntfs       Downloads                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        d86bdce8-620c-49a8-869a-c5fb1ba63b10   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        87ef989b-10ab-40f0-99d9-ba1769a283bf   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d86bdce8-620c-49a8-869a-c5fb1ba63b10 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d86bdce8-620c-49a8-869a-c5fb1ba63b10 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d86bdce8-620c-49a8-869a-c5fb1ba63b10 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d86bdce8-620c-49a8-869a-c5fb1ba63b10 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set d86bdce8-620c-49a8-869a-c5fb1ba63b10
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=d86bdce8-620c-49a8-869a-c5fb1ba63b10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=87ef989b-10ab-40f0-99d9-ba1769a283bf none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 414.6GB: boot/grub/core.img
 234.6GB: boot/grub/grub.cfg
 414.6GB: boot/initrd.img-2.6.32-21-generic
 414.6GB: boot/initrd.img-2.6.32-23-generic
 414.6GB: boot/vmlinuz-2.6.32-21-generic
    .8GB: boot/vmlinuz-2.6.32-23-generic
 414.6GB: initrd.img
 414.6GB: initrd.img.old
    .8GB: vmlinuz
 414.6GB: vmlinuz.old


---

### Post by wilee-nilee on 2010-07-03
So you haven't really given any information as to how the computers booting if at all other then the blank sdc boot. But you have the W7 bootloader in the mbr of sda, and grub installed in sdb, and Ubuntu installed in sdc1, but it looks like you did a custom install your extended is around the swap, no big deal.

Put sdc 1st in the boot from sda next from the bios and use this link with a live Ubuntu 9.10 or later cd to load grub to sdc and mount the Ubuntu partition reboot. 


Read the link, basically from the live cd you will run from the terminal.
```
sudo mount /dev/sdc1 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```
[Step #11](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
All this after rearranging the bios, so after this command set reboot then run the ```
sudo update-grub
``` in the mounted booted Ubuntu.

This way will leave you with the ability to boot W7 from sda or the grub menu brought up from a sdc boot. If you want to keep W7 out of Grub remove the os-prober in Ubuntu from synaptic.

If your choosing the boot from with a key prompt it doesn't matter in what order the HD's are in, but if you want grub from sdc to give you a choice put it first to be read to have a choice.

---

### Post by zeromx on 2010-07-03
How is it that grub is installed in sdb?... i installed it on sdc and dont understand why it would be installed there?...

ideally i would like to boot and press F8 to give me boot options and i usually choose what os i like from there, rather then grub.

---

### Post by wilee-nilee on 2010-07-03
> **zeromx said:**
> How is it that grub is installed in sdb?... i installed it on sdc and dont understand why it would be installed there?...

ideally i would like to boot and press F8 to give me boot options and i usually choose what os i like from there, rather then grub.

The only way you would have assured grub in sdc is using the advanced tab on the last install screen and pointing it at sdc, maybe you did and misclicked or who knows what really.

If you just install grub2 to sdc with the commands which are from the # 11 link you can choose your boot. And if you want remove the os-prober from Ubuntu in synaptic and Windows wont be in the grub menu.

F8 is usually the prompt for the safe mode in windows, is this also a preboot key prompt for choice of boot devices?

---

### Post by zeromx on 2010-07-04
> **wilee-nilee said:**
> The only way you would have assured grub in sdc is using the advanced tab on the last install screen and pointing it at sdc, maybe you did and misclicked or who knows what really.

If you just install grub2 to sdc with the commands which are from the # 11 link you can choose your boot. And if you want remove the os-prober from Ubuntu in synaptic and Windows wont be in the grub menu.

F8 is usually the prompt for the safe mode in windows, is this also a preboot key prompt for choice of boot devices?

Yes on a asus p6t, if you press f8 in the post, it gives you boot from device option. 

i will give that a try and report back.

Thanks

---

