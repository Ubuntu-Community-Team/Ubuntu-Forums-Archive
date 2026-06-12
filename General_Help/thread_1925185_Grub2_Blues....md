---
title: "Grub2 Blues..."
date: 2012-02-14
forum: General Help
---

### Post by 2CV67 on 2012-02-14
I recently converted from Legacy Grub to Grub2 & am still struggling.
I read a large part of these articles but all is not clear:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
[http://members.iinet.net.au/~herman546/p20.html](http://members.iinet.net.au/~herman546/p20.html)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The very length of those items is some indication of the problem.

Let me spell out my most recent moves, assuming the messier bits before don't count.

I made a clean install of Ubuntu 11.10 in primary partition sda3.
It came with Grub2 which found my existing XP & LTS10.04 OS's OK.
LTS is just a skeletal installation for emergencies.
I switched 11.10 to Lubuntu so will just call it that from now on.
I used Grub Customizer in Lubuntu to whittle down my Grub screen entries to simply: Lubuntu / Previous versions (hidden) / XP / LTS.
So far, so good.

LTS had been inside a now-superfluous extended partition, so I wiped that partition, created a new primary partition, sda4, & made a clean install of LTS in that partition.
After some hesitation, I accepted the 'non-advanced' option, which installed a bootloader there too.
My first question is: should/could I have chosen 'without bootloader' there?
What are the real choices & results?

After that, I lost all my Grub screen settings - I now saw all the LTS kernels at the top & all the Lubuntu ones at the bottom.

Switching back to Lubuntu, I ran 'sudo grub-install /dev/sda' & 'sudo update-grub' to get my prefered settings back.

After the next Lubuntu kernel upgrade, I expected to see just the latest kernel in grub screen with the previous one hidden in 'previous versions', but they are both shown in full.

After the next LTS kernel upgrade, LTS again took control of grub screen & I again had to do grub-install & update-grub to get control back.

Is this how things are supposed to happen?
I hope not!

How do I fix grub2 to:
Shift previous versions to 'previous versions'?
Leave control of grub in Lubuntu?

Repeat - should I have installed LTS without grub?
If so, can I fix that easily, or should I start that install again (no problem to do that).

Results from boot_info_script as of today, with control in Lubuntu.
By the way, what is that first line 'looks for csyn'?
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for csyn.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3    *    135,301,120   232,394,751    97,093,632  83 Linux
/dev/sda4         114,817,024   135,301,119    20,484,096  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2B1B-1302                              vfat       XP                            
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap                                     
/dev/sda3        31c1a1b4-1e0e-4e32-a19d-f5e245b285f2   ext4                                     
/dev/sda4        4996dffd-bf1e-4ad3-816a-9ff92ccd0048   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x400x8
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 3.0.0-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions"{
menuentry "Ubuntu, with Linux 3.0.0-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_os-prober_proxy ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2b1b-1302
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-38-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 ro quiet splash
	initrd /boot/initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/20_os-prober_proxy ###

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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  89.6GB: boot/grub/core.img
  89.4GB: boot/grub/grub.cfg
  71.0GB: boot/initrd.img-3.0.0-12-generic
  71.9GB: boot/initrd.img-3.0.0-14-generic
  84.0GB: boot/initrd.img-3.0.0-15-generic
  93.8GB: boot/initrd.img-3.0.0-16-generic
  78.0GB: boot/vmlinuz-3.0.0-12-generic
  69.9GB: boot/vmlinuz-3.0.0-14-generic
  75.3GB: boot/vmlinuz-3.0.0-15-generic
  93.7GB: boot/vmlinuz-3.0.0-16-generic
  93.8GB: initrd.img
  84.0GB: initrd.img.old
  93.7GB: vmlinuz
  75.3GB: vmlinuz.old

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
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
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4996dffd-bf1e-4ad3-816a-9ff92ccd0048
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b1b-1302
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-16-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=4996dffd-bf1e-4ad3-816a-9ff92ccd0048 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


  59.0GB: boot/grub/core.img
  65.7GB: boot/grub/grub.cfg
  59.9GB: boot/initrd.img-2.6.32-33-generic
  59.9GB: boot/initrd.img-2.6.32-38-generic
  59.7GB: boot/vmlinuz-2.6.32-33-generic
  59.0GB: boot/vmlinuz-2.6.32-38-generic
  59.9GB: initrd.img
  59.9GB: initrd.img.old
  59.0GB: vmlinuz
  59.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

Thanks for any suggestions!

---

### Post by Leppie on 2012-02-15
The issue you're having is because you've got Grub 2 installed in both Lubuntu and your LTS installation.
To prevent the LTS taking over the Grub 2 system after each kernel update, remove it from your LTS installation:
```
sudo apt-get purge grub-pc grub-common
```

---

### Post by oldfred on 2012-02-15
I think Leppie's uninstall will work, but not sure if os-prober in your 11.10 will then find the 10.04 install.

Grub2 also remembers where to reinstall on updates. 

Another way is to delete the memory of where to reinstall. If you unchoose everything then it will not save a reinstall location.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Leppie on 2012-02-15
> **oldfred said:**
> I think Leppie's uninstall will work, but not sure if os-prober in your 11.10 will then find the 10.04 install.
The trick is to run update-grub from the Lubuntu installation after each kernel update in the LTS installation.

---

### Post by oldfred on 2012-02-15
I am not totally clear if os-prober finds kernels to boot unless there is a grub menu. I know it searches for menu.lst, grub.cfg or other grub files as I have seen it post incorrect entries from aother installs grub files. (This was a while ago so maybe it is now fixed?).

---

### Post by imachavel on 2012-02-15
> **Leppie said:**
> The issue you're having is because you've got Grub 2 installed in both Lubuntu and your LTS installation.
To prevent the LTS taking over the Grub 2 system after each kernel update, remove it from your LTS installation:
```
sudo apt-get purge grub-pc grub-common
```

if I use that command with my partition table looking like this:

[http://paste.ubuntu.com/843852/](http://paste.ubuntu.com/843852/)

what will happen?

---

### Post by 2CV67 on 2012-02-16
I hesitated a long time before my initial post, because I couldn't believe there was really a problem.
I thought that in all my (very lengthy) reading, I had just not seen or not understood the relevant paragraph(s).
I was pretty sure somebody would jump in with a polite RTFM & point me to the glaring examples showing what to do.

But from reactions so far - and from my continued searching - it looks as though Grub2 really does not handle what I would have thought was its basic function:
Coordinate several OS's & manage regular kernel upgrades without losing control & without requiring continuing manual intervention.
Legacy grub did this perfectly well with chainloading.

I still cannot see any clear instructions as to whether multi-booting OS's should each have Grub2, or only the main OS.

I am prepared to try the suggestions made so far, but will wait for the dust to settle before jumping in!

Thanks for those, and any future, comments & suggestions!

---

### Post by oldfred on 2012-02-16
If you want just one entry that will always boot the newest kernel in the other install you can add this to 40_custom. Ubuntu puts a link to the newest kernel in /. You can then turn off os-prober.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

