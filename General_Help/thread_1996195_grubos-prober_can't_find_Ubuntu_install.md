---
title: "grub/os-prober can't find Ubuntu install"
date: 2012-06-04
forum: General Help
---

### Post by Beryllium on 2012-06-04
I have three operating systems installed, Windows 7, Ubuntu 12.04 and Kubuntu 12.04, all on the same hard disk. Windows and Kubuntu boot fine.

They are arranged like this:
Win7 | Win7 | Win7 | Ubuntu | Swap space | Home part | Kubuntu

Windows 7 has three partitions (recovery env, etc), then Ubuntu 12.04, then swap space for Ubuntu and Kubuntu, then my home partition for Ubuntu, then Kubuntu. Both Windows 7 and Kubuntu see all these partitions fine.

I had some issues with grub and it's been reinstalled a couple of times. However, each time I reinstall or update grub, it doesn't list Ubuntu as a boot option. If I run "ls" at the grub command line, it lists:
(hd0,msdos1), (hd0,msdos2), (hd0,msdos3), (hd0,msdos5), (hd0, msdos6) ... to (hd0,msdos8).
It does not list (hd0,msdos4), where Ubuntu is located. using
```
set root=(hd0,msdos4)
```
gives "error: no such partition".

Running
```
sudo update-grub2
```
in Kubuntu returns
Windows...
Windows...
Windows...
Ubuntu ... kernel 3.2-24
Ubuntu ... kernel 3.2-24 (recovery)
Ubuntu ... kernel 3.2-23
Ubuntu ... kernel 3.2-23 (recovery)
(Something like that)
But all 4 entries are all Kubuntu.

I am stumped as to why grub or os-prober can't find my Ubuntu install. Any suggestions?

---

### Post by wilee-nilee on 2012-06-04
Download the link, extract it to the desktop in Ubuntu and run the command.

Copy and paste all the text from the results.txt to a reply. Before submitting the reply highlight all the text and click on the # in the reply panel to wrap the text in code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by Beryllium on 2012-06-04
Here is the output:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    37,750,783    37,748,736  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     37,750,784    37,955,583       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          37,955,584   767,383,551   729,427,968   7 NTFS / exFAT / HPFS
/dev/sda4         767,385,598 1,465,147,391   697,761,794   5 Extended
/dev/sda5         767,385,600   865,040,383    97,654,784  83 Linux
/dev/sda6         865,042,432   872,853,503     7,811,072  82 Linux swap / Solaris
/dev/sda7         872,855,552 1,361,136,801   488,281,250  83 Linux
/dev/sda8       1,361,137,664 1,465,147,391   104,009,728  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8E2C54222C54079B                       ntfs       PQSERVICE
/dev/sda2        24EE56B7EE5680CA                       ntfs       SYSTEM RESERVED
/dev/sda3        4CEC70F7EC70DD20                       ntfs       Acer
/dev/sda5        e3c40504-83e4-4542-8d48-586870b1e5bc   ext4       
/dev/sda6        1412fc46-01d2-40c5-a24d-a654bd04f1fb   swap       
/dev/sda7        3ced8320-97e4-496e-98fa-f1730c9d33dd   ext4       
/dev/sda8        a03d0488-fe70-4bd6-9401-ba4d6aecf427   ext4       
/dev/sr0                                                udf        GRANTURISMO4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root e3c40504-83e4-4542-8d48-586870b1e5bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768x24
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root e3c40504-83e4-4542-8d48-586870b1e5bc
  set locale_dir=($root)/boot/grub/locale
  set lang=en_NZ
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root e3c40504-83e4-4542-8d48-586870b1e5bc
insmod png
if background_image /usr/share/backgrounds/mountains2.png; then
  set color_normal=light-gray/black
  set color_highlight=black/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Kubuntu" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
	linux /boot/vmlinuz-3.2.0-24-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-24-generic
}
menuentry "Windows 7" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 24EE56B7EE5680CA
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e3c40504-83e4-4542-8d48-586870b1e5bc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=3ced8320-97e4-496e-98fa-f1730c9d33dd /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1412fc46-01d2-40c5-a24d-a654bd04f1fb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 390.072387695 = 418.837037056  boot/grub/grub.cfg                             1
 368.066406250 = 395.208294400  boot/initrd.img-3.2.0-23-generic               2
 376.886718750 = 404.679032832  boot/initrd.img-3.2.0-24-generic               2
 390.135295868 = 418.904584192  boot/vmlinuz-3.2.0-23-generic                  1
 373.364002228 = 400.896544768  boot/vmlinuz-3.2.0-24-generic                  1
 367.816471100 = 394.939928576  initrd.img                                     3
 368.066406250 = 395.208294400  initrd.img.old                                 2
 373.364002228 = 400.896544768  vmlinuz                                        1
 390.135295868 = 418.904584192  vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
  set locale_dir=($root)/boot/grub/locale
  set lang=en_NZ
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root a03d0488-fe70-4bd6-9401-ba4d6aecf427
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 8E2C54222C54079B
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 24EE56B7EE5680CA
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 4CEC70F7EC70DD20
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Kubuntu (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root e3c40504-83e4-4542-8d48-586870b1e5bc
	linux /boot/vmlinuz-3.2.0-24-generic root=UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-24-generic
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a03d0488-fe70-4bd6-9401-ba4d6aecf427 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1412fc46-01d2-40c5-a24d-a654bd04f1fb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 691.353729248 = 742.335414272  boot/grub/core.img                             1
 667.238288879 = 716.441657344  boot/grub/grub.cfg                             1
 650.068542480 = 698.005782528  boot/initrd.img-3.2.0-23-generic               1
 650.939517975 = 698.940985344  boot/initrd.img-3.2.0-24-generic               3
 667.174545288 = 716.373213184  boot/vmlinuz-3.2.0-23-generic                  1
 689.780017853 = 740.645654528  boot/vmlinuz-3.2.0-24-generic                  2
 650.939517975 = 698.940985344  initrd.img                                     3
 650.068542480 = 698.005782528  initrd.img.old                                 1
 689.780017853 = 740.645654528  vmlinuz                                        2
 667.174545288 = 716.373213184  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

---

### Post by wilee-nilee on 2012-06-04
So the sda5 partition is missing this.
```
/boot/grub/core.img
```It looks like the sda8, has the boot control, by having its grub in the mbr, but we can chroot to the sda5 and purge and reload grub there, and put it as the controlling grub, I will give you the commands as well to have either as the controller as well. What ever release is first in the grub menu is the controlling boot.

From a live Ubuntu cd in the desktop, run these commands.

```
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
apt-get purge grub-pc grub-common
```Here you will be asked if you want to completely remove grub say yes.
```
apt-get install grub-pc grub-common
```Here you will be asked were you want grub, choose sda only tick it with the space key.
```
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```Now if you want either to be the controlling boot you run from that, one in the terminal```

sudo grub-install /dev/sda
``````
then sudo update-grub
```I will add here as well that if you get a kernel update in the non controlling install of ubuntu or kubuntu you run a update-grub there then in the controlling OS to have that kernel show in the controlling grub menu.

---

### Post by wilee-nilee on 2012-06-04
I removed two sudo's that were not needed in the purge and install of grub-pc grub common.

You will get errors with them as the were, now it is correct, my bad. :oops:

---

### Post by Beryllium on 2012-06-05
Thank you very much, this worked flawlessly. I knew chroot was the key to getting into Ubuntu and running grub, I just wasn't sure how to do it. If you don't mind, could you please explain what
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```
does? I'm guessing it makes the chroot aware of devices attached to my system, is that it? Anyway, thanks again.

---

### Post by idoitprone on 2012-06-05
> **Beryllium said:**
> Thank you very much, this worked flawlessly. I knew chroot was the key to getting into Ubuntu and running grub, I just wasn't sure how to do it. If you don't mind, could you please explain what
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```does? I'm guessing it makes the chroot aware of devices attached to my system, is that it? Anyway, thanks again.

it an ingenious way of avoiding typing mount like 5 times and the variable 5 times

he makes a loop for that store in a list of values "/dev /dev/pts /proc /sys" in the variable i
in each loop you bind each directory to the proper place

mount {bind} /sourceDir+variable$i /destinationDir+variable$i

when you chroot those filesystems are important or else the commands will confuse itself with the host system. You might end up with undesirable behaviour because the sys is on /mnt/ not on /

**[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)**

---

### Post by Beryllium on 2012-06-05
Ah, thanks.

---

