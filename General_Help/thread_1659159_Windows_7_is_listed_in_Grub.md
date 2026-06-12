---
title: "Windows 7 is listed in Grub"
date: 2011-01-03
forum: General Help
---

### Post by axept on 2011-01-03
I have some question:

1: In my grub menu Windows 7 is listed, I don't know why. Win7 was installed on this computer before, but I formatted the HDD before I did a clean install of Ubuntu 10.10. How to remove it?

2: When I boot I don't get a boot image, only a blinking cursor in the upper left corner. Not a big deal, but I would like to have a normal boot image. Any ideas how to fix it? I tried googling but I only find old threads.

My laptop is a Acer Aspire 7735Z

Graphic card is ATI Radeon HD 4570.

BTW; I got no other problems what so ever. Everything works great really.

---

### Post by Verbeck on 2011-01-03
for #1: could you run the following from a terminal (applications>accessories) and post the output```
*sudo fdisk -l && sudo update-grub*
```edit: do as [cipherboy_loc]("http://ubuntuforums.org/member.php?u=1066963") posted below. it's more informative that way

---

### Post by cipherboy_loc on 2011-01-03
For 1, run the boot info script in my signature.

For 2, open up a terminal and type:
```

sudo nano -w /etc/defalt/grub

```
and on the line that states something like:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
make sure it lists splash as the last argument. Then run:
```
sudo update-grub2
```
and everything will be fixed.



Cipherboy

> **axept said:**
> I have some question:

1: In my grub menu Windows 7 is listed, I don't know why. Win7 was installed on this computer before, but I formatted the HDD before I did a clean install of Ubuntu 10.10. How to remove it?

2: When I boot I don't get a boot image, only a blinking cursor in the upper left corner. Not a big deal, but I would like to have a normal boot image. Any ideas how to fix it? I tried googling but I only find old threads.

My laptop is a Acer Aspire 7735Z

Graphic card is ATI Radeon HD 4570.

BTW; I got no other problems what so ever. Everything works great really.

---

### Post by axept on 2011-01-03
For the

```
sudo fdisk -l && sudo update-grub
```

I got this:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a2f9ac4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275        1288      102400    7  HPFS/NTFS
/dev/sda3            1288       42985   334925824   83  Linux
/dev/sda4           42985       60802   143116288    7  HPFS/NTFS
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done

```


Hm, found Win7 loader on my second partition?? did not think that had anything to do with my earlier win7 install..

---

### Post by axept on 2011-01-03
And for the Boot script: 

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048    20,686,847       204,800   7 HPFS/NTFS
/dev/sda3          20,686,848   690,538,495   669,851,648  83 Linux
/dev/sda4         690,538,496   976,771,071   286,232,576   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        489ab7ff-2109-4c08-84ba-d1b92fdaa1e0   swap                                     
/dev/sda2        C09679609679583C                       ntfs       System Reserved               
/dev/sda3        4b63805f-b759-493e-acc4-d7f30728b15f   ext3                                     
/dev/sda4        460CF7DF0CF7C7C7                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda2        /dos                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/460CF7DF0CF7C7C7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
set locale_dir=($root)/boot/grub/locale
set lang=nb
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro single  vga=792 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4b63805f-b759-493e-acc4-d7f30728b15f ro single  vga=792 splash
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 4b63805f-b759-493e-acc4-d7f30728b15f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c09679609679583c
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
# /dos was on /dev/sda2 during installation
UUID=C09679609679583C /dos            ntfs    defaults,umask=007,gid=46 0       0
/dev/sda1       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 326.7GB: boot/grub/core.img
 326.7GB: boot/grub/grub.cfg
 326.7GB: boot/initrd.img-2.6.35-22-generic
 326.6GB: boot/initrd.img-2.6.35-23-generic
 326.7GB: boot/initrd.img-2.6.35-23-generic-pae
 326.7GB: boot/initrd.img-2.6.35-24-generic
 326.8GB: boot/initrd.img-2.6.35-24-generic-pae
 326.7GB: boot/vmlinuz-2.6.35-22-generic
 326.6GB: boot/vmlinuz-2.6.35-23-generic
 326.7GB: boot/vmlinuz-2.6.35-23-generic-pae
 326.7GB: boot/vmlinuz-2.6.35-24-generic
 326.7GB: boot/vmlinuz-2.6.35-24-generic-pae
 326.8GB: initrd.img
 326.7GB: initrd.img.old
 326.7GB: vmlinuz
 326.7GB: vmlinuz.old
```


For 2:


I have this on 2 lines:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=12$
GRUB_CMDLINE_LINUX=" vga=792 splash"

```

---

### Post by cipherboy_loc on 2011-01-03
> 
I have this on 2 lines:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=12$
GRUB_CMDLINE_LINUX=" vga=792 splash"

```

Interesting, I realized that I had the sqlash option enabled in the /etc/defaults/grub, and I have always seen the cursor (I like that type of stuff):

```

$ grep -i 'splash' /boot/grub/grub.cfg 
    linux    /boot/vmlinuz-2.6.37-9-generic root=UUID=5ff920f6-fdcf-4a32-bed3-40a3ea35158e ro   quiet splash
    linux /boot/kernel-2.6.36-gentoo-rc5 root=/dev/sda6 ro quiet splash

```Which shows that I have splash enabled for both my Ubuntu and my Gentoo installs (Custom kernel for Gentoo), and Gentoo gives a little tux logo at the top, with lots of output to the console, but the Ubuntu just gives a cursor (with one line of text because of the hibernation stuff that I added). 

Almost like the kernel ignores the splash option. Is it a possible bug?

As for the output of the boot script, it shows that you have a swap partition at the front of your disk, followed by (most likely) a system restore partition, then your Ubuntu install, and finally a Windows (of some sorts) install. 

I have a few questions:
1) What type of computer is it,
2) Are you sure you completely removed the Windows 7 install, and
3) Can you still boot Windows 7?


--EDIT--
Oh, I just checked the output of the boot script and it says that you indeed have the splash option added to the kernel boot.
--/EDIT--

Cipherboy

---

### Post by Verbeck on 2011-01-03
/dev/sda2 is probably the separate boot partition the windows installer makes (starting from vista and onwards)
so if you no longer boot into windows, you may delete that partition (also remove the fstab entry)
and run* sudo update-grub* again

---

### Post by axept on 2011-01-03
1:

The computer is a Acer Aspire 7735Z as mention. A laptop.

Intel Pentium Dual Core T4200 (I think)
4 GB DDR3 RAM 
500 GB HDD
ATI Radeon HD 4570 - 512 MB
Original installed with Vista.

And I've installed the "PAE" kernel because I want all my memory, since I run 32bit Ubuntu.

2:

I thought so... But clearly I didn't :P

3:

Have not tried, but I doubt it... :P 

Can I delete that partition /dev/sda2 without messing things up??

---

### Post by Smart Viking on 2011-01-03
> **axept said:**
> 1:
Can I delete that partition /dev/sda2 without messing things up??

Yes, if you don't have/use windows.

Open gparted and format the partition(make sure it's not mounted), then run "update-grub".

EDIT: Nice, a fellow Norwegian. :P

---

### Post by axept on 2011-01-03
Okay, then that problem was solved..

Is there a way to get a splash screen then? Or do I have to live with the blinking cursor ?

EDIT: Jepp, prøver så godt jeg kan å lære :P

---

