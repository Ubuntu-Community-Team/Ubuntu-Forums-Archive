---
title: "Install Windows after Ubuntu"
date: 2010-09-08
forum: General Help
---

### Post by baddnady23 on 2010-09-08
I'm about reinstall windows on a second drive in my computer.  I am a full time Ubuntu user but I need windows for a certain task.  I will be using the following guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Has anyone had any success with this method (1st one) and is there anything else I should be aware of?

---

### Post by Rubi1200 on 2010-09-08
Make backups first!
[]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by TNT1 on 2010-09-08
Get ready to re-install GRUB...

---

### Post by shanep-server on 2010-09-08
yah after you install windows your gonna have to boot from livecd and google tutorial on reinstalling grub bootloader to over ride windows bootloader so u can access either partiton from boot menu

side note i would find the tutorial first then save to disk so u can access it from windows partition while on live boot in case for some strange reason u can access web from livecd without tweaking... rare but crazier stuff has happened.

---

### Post by howefield on 2010-09-08
> **baddnady23 said:**
> Has anyone had any success with this method (1st one) and is there anything else I should be aware of?

That is easy enough to do and you shouldn't have any issues following that process.

You may also be able to disconnect the Ubuntu drive, then install windows, and select which drive to boot from at startup. Keeping the installs completely separate.

---

### Post by baddnady23 on 2010-09-08
> You may also be able to disconnect the Ubuntu drive, then install windows, and select which drive to boot from at startup. Keeping the installs completely separate

I already have the old windows install on a separate disk.  If I do this, and then plug the ubuntu drive back in after reinstalling windows, would grub still work like usual or will I still need to put grub back in its little home?

---

### Post by Joe of loath on 2010-09-08
> **baddnady23 said:**
> I already have the old windows install on a separate disk.  If I do this, and then plug the ubuntu drive back in after reinstalling windows, would grub still work like usual or will I still need to put grub back in its little home?

That would most probably work. There's no harm in trying, anyway.

---

### Post by TNT1 on 2010-09-08
> **baddnady23 said:**
> I already have the old windows install on a separate disk.  If I do this, and then plug the ubuntu drive back in after reinstalling windows, would grub still work like usual or will I still need to put grub back in its little home?

I would think you would have to re-do GRUB. Even if you remove the linux drive completely, install windows, insert x drive, your pc will boot to windows only. longhorn loader wont even know linux/GRUB is there.

---

### Post by baddnady23 on 2010-09-08
OK thanks.  This doesn't seem too terribly bad.  Just more of an inconvenience than anything.  I appreciate the input.:)

---

### Post by howefield on 2010-09-08
> **baddnady23 said:**
> I already have the old windows install on a separate disk.  If I do this, and then plug the ubuntu drive back in after reinstalling windows, would grub still work like usual or will I still need to put grub back in its little home?

Grub will work as normal, but won't know about your windows install, unless you do a sudo update-grub. (As I mentioned, to boot windows, you'd need to select the disk to boot from at startup or do the sudo update-grub)

---

### Post by TNT1 on 2010-09-08
> **baddnady23 said:**
> OK thanks.  This doesn't seem too terribly bad.  Just more of an inconvenience than anything.  I appreciate the input.:)

now that's linux/ubuntu spirit right there. well done that dude.;)

---

### Post by baddnady23 on 2010-09-08
> **howefield said:**
> Grub will work as normal, but won't know about your windows install, unless you do a sudo update-grub. (As I mentioned, to boot windows, you'd need to select the disk to boot from at startup or do the sudo update-grub)

This seems like the easiest method :p

---

### Post by baddnady23 on 2010-09-08
Well I did it and ran sudo update-grub once I got back into ubuntu, but it won't boot up into grub when I turn on the computer, it goes straight to windows.  I listed the boot-info script below...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    48,828,415    48,826,368  83 Linux
/dev/sdb2          48,828,416    83,984,383    35,155,968  83 Linux
/dev/sdb3          83,984,384   107,421,695    23,437,312  82 Linux swap / Solaris
/dev/sdb4         107,421,696 1,953,523,711 1,846,102,016  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6f23b0ac-0650-49da-9c4b-cacda4dcec57   xfs        storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b9d5171c-0d54-4bef-b2a3-613a922f656b   ext4                                     
/dev/sdb2        80efe95e-677e-4689-9f40-7da2866b9c4b   ext4                                     
/dev/sdb3        4151f5bd-04d6-416c-969c-fb41c0444435   swap                                     
/dev/sdb4        794c6ff5-df36-462e-a2db-6184f8f50618   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        178C148D5D7947A6                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb4        /home                    ext4       (rw)
/dev/sda1        /media/storage           xfs        (rw)
/dev/sr1         /media/Ubuntu 10.04 LTS amd64 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
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
search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b9d5171c-0d54-4bef-b2a3-613a922f656b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 178c148d5d7947a6
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b9d5171c-0d54-4bef-b2a3-613a922f656b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=794c6ff5-df36-462e-a2db-6184f8f50618 /home           ext4    defaults        0       2
/dev/sdb3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/storage	auto	defaults	0	0
# Entry for andrew-server NFS share
192.168.1.70:/media/data	/media/andrew-server	nfs	rsize=8192,wsize=8192,timeo=14,intr

=================== sdb1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  22.0GB: boot/grub/grub.cfg
  22.6GB: boot/initrd.img-2.6.32-23-generic
  23.0GB: boot/initrd.img-2.6.32-24-generic
  24.1GB: boot/vmlinuz-2.6.32-23-generic
  22.6GB: boot/vmlinuz-2.6.32-24-generic
  23.0GB: initrd.img
  22.6GB: initrd.img.old
  22.6GB: vmlinuz
  24.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by baddnady23 on 2010-09-08
Ha, got it.  I never did lose my origional GRUB install, the issue was that the order of hard disks that the BIOS boots in got changed and make the Windows 7 disk boot first, preventing GRUB from ever loading.  All I needed to do was swith the order of the drives and update-grub.  Now everything is peachy.  :-)

---

### Post by howefield on 2010-09-09
> **baddnady23 said:**
> All I needed to do was swith the order of the drives and update-grub.  Now everything is peachy.  :-)

Well done !

Nice place to be :)

---

