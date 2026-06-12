---
title: "Grub2 won't boot Windows 7"
date: 2010-11-18
forum: General Help
---

### Post by Canordis on 2010-11-18
I've installed Xubuntu 10.10 on a very new EeePC 1201HA. The netbook came preconfigured from the OEM with the disk split into two Windows partitions of about the same size, one with Windows 7 starter. I removed the second partition (Which was just empty) and have installed a series of different distros since then, to try and gauge their support for the 1201HA hardware. I finally settled on Xubuntu, which can support most of the laptop's features with some tweaks.

However, after this last install, and a Grub config change needed to make the framebuffer work on this hardware, I'm unable to boot Windows 7.Grub shows it on the menu normally, but when I select the Windows 7 entry, I get the message 'Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key,' which I understand isn't from the OS but rather a BIOS message which implies there is no loader.

I've tried using the Windows 7 system restore to do everything short of rewriting the Windows bootloader to the MBR (Which would, of course, remove Grub and thus not solve my problem, as I couldn't load Ubuntu from it). I attempted to fix the boot sector on the partition with the system restore tools, to no avail. And because this is a netbook with no optical drive, I'm unable to reinstall from a disk.

---

### Post by drs305 on 2010-11-18
Is it possible you installed Grub2 to the Windows partition? You can check using the boot info script found at [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net").

If you don't know how to interpret the contents you can post them here and we can look at them.

Here is a possible solution if Grub2 is installed on the Windows partition. There have been reports that in some cases the 'sixth' screen is different. If so and you cannot figure it out, abort the attempt and tell us what happened.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by Canordis on 2010-11-19
Thank you very much for the timely response, I'm sorry I haven't been able to get back immediately as my time today was extremely limited. I ran the script, and can't really identify the problem, so here is the output:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         480,583,680   488,396,799     7,813,120  82 Linux swap / Solaris
/dev/sda3         209,717,248   480,581,631   270,864,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C68E74AF8E74999F                       ntfs                                     
/dev/sda2        bc06be41-a3bb-497c-af9e-e48a3d718ac5   swap                                     
/dev/sda3        ec3b0f04-2887-4611-81dc-dc67655727f6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768x32
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_915resolution ###
insmod 915resolution
915resolution 58 1366 768 32
### END /etc/grub.d/01_915resolution ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ec3b0f04-2887-4611-81dc-dc67655727f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768x32
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ec3b0f04-2887-4611-81dc-dc67655727f6 ro single 
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
	search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ec3b0f04-2887-4611-81dc-dc67655727f6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c68e74af8e74999f
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
# / was on /dev/sda3 during installation
UUID=ec3b0f04-2887-4611-81dc-dc67655727f6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=bc06be41-a3bb-497c-af9e-e48a3d718ac5 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 204.2GB: boot/grub/core.img
 227.8GB: boot/grub/grub.cfg
 221.4GB: boot/initrd.img-2.6.35-22-generic
 204.2GB: boot/vmlinuz-2.6.35-22-generic
 221.4GB: initrd.img
 204.2GB: vmlinuz


```

Edit: As for testdisk, I attached a capture of the 'sixth screen.' Basically it tells me the boot sector on the partition is okay, but the backup is corrupted.

---

### Post by drs305 on 2010-11-19
I'm afraid I don't know enough about W7 to be of much assistance. Hopefully this will bump the thread someone else can answer.

I have one observation though. I know that W7 can come installed in either one partition or a small boot partition and then the main OS. I notice that your first partition starts at 2048. Is it possible there was a W7 boot partition prior to that which has now gone missing?

---

### Post by Quackers on 2010-11-19
If W7 is re-installed from an Install disc you can get everything on one partition, like yours is. Mine is the same. I don't see anything wrong with your Windows partition. All the necessary boot files are present and the boot flag is set correctly. The only thing I can think of is that one, or more, of them has been damaged in some way. With a cd drive you could run the startup repair from the cd. It may be possible to download a repair disc and put it on a usb stick, but I don't have any info on how you would do that.
drs305, does Lilo work with W7?

---

### Post by drs305 on 2010-11-19
> **Quackers said:**
> 
drs305, does Lilo work with W7?

As far as I know it does. 

The odd part is I don't know if it works with Ubuntu as I've never tried to point it to a linux distro. When we install it to help with a Windows boot all we do is tell it where the MBR is. I'm guessing guess it just points to the partition with the boot flag.

Update: Just using the standard "lilo -M /dev/sda mbr" and making the Ubuntu partition bootable does not work. Apologies to *Canordis* for the digression.

---

### Post by Quackers on 2010-11-19
Interesting.
Obviously grub's os-prober is picking up the Windows boot files. It seems to be the files themselves that are causing the boot failure.

---

### Post by Canordis on 2010-11-20
I've tried startup repair, to no avail. The automatic one doesn't detect any problems, and I've attempted the usual manual commands, also without effect.

Edit: I only have a 2GB USB drive. I'm going to have to get a larger one to be able to reinstall Windows from disk at all on this laptop...

---

### Post by Quackers on 2010-11-20
It may be better to try the automatic startup repair program 3 times, with reboots in between each one. The third one seems to pick up the installation that the first 2 do not. 
The fact that the first one did not pick up the installation would seem to confirm that something is wrong with your Windows boot files.
I have high hopes for the third run :-)

---

### Post by Canordis on 2010-11-20
That sounds highly illogical. But then again it *is* Windows. I'll give it a shot when I get back home.

---

### Post by Quackers on 2010-11-20
Illogical - yes, but as you say, we are talking about Windows :-)
Good luck with it.

---

### Post by Canordis on 2010-11-20
Well, I tried it and it didn't work. Oddly enough the first time around the recovery environment found a problem and purported to fix it, but after that nothing changed, so I guess I'm running out of options.

---

