---
title: "Grub2 problem"
date: 2010-02-10
forum: General Help
---

### Post by Jzz5 on 2010-02-10
Hi all,

I have this problem with Grub2. I have a dualboot on 2 HDD's, the first containing WinXP and the 2nd containing Ubuntu 9.10 and 10.04. Both 9.10 and 10.04 boot flawlessly, but since installing 10.04 (only yesterday), I cannot boot into XP any more.

When I try the 'windows' option it shows the word 'GRUB' and a blinking cursor...

I ran meierfra's boot info script, here's the output:

```

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks for 
(UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1)/boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
partition #6 for /boot/grub.
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and 
looks at sector 302288255 of the same hard drive for 
core.img, but core.img can not be found at this 
location. No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda5 starts 
at sector 63.
Operating System: 
Boot files/dirs: 

sdb1: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb1 and 
looks at sector 302285247 of the same hard drive for 
core.img, core.img is at this location on /dev/sdb and 
looks on partition #1 for /boot/grub.
Operating System: Ubuntu lucid (development 
branch)
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sdb5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

sdb6: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb6 and 
looks at sector 302288191 of the same hard drive for 
core.img, core.img is at this location on /dev/sdb and 
looks on partition #1 for /boot/grub.
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xbcc1bcc1

Partition Boot Start End Size Id System

/dev/sda1 * 63 163,846,934 163,846,872 7 HPFS/NTFS
/dev/sda2 163,846,935 976,751,999 812,905,065 f W95 Ext d (LBA)
/dev/sda5 163,846,998 976,751,999 812,905,002 7 HPFS/NTFS


Drive: sdb ___________________ __________________________________________________ ___

Schijf /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x000b2c74

Partition Boot Start End Size Id System

/dev/sdb1 63 594,340,739 594,340,677 83 Linux
/dev/sdb2 594,340,740 976,768,064 382,427,325 5 Extended
/dev/sdb5 957,120,633 976,768,064 19,647,432 82 Linux swap / Solaris
/dev/sdb6 594,340,866 942,324,704 347,983,839 83 Linux
/dev/sdb7 942,324,768 957,120,569 14,795,802 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/sda1 1EA014DEA014BE69 ntfs 
/dev/sda5 EA78EDD078ED9C17 ntfs 
/dev/sdb1 c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ext4 
/dev/sdb5 fc52e245-6210-4feb-ba71-03921ad0558f swap 
/dev/sdb6 e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ext4 
/dev/sdb7 3a3eeabc-2283-4001-acc6-62b2e56c514a swap 

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sdb6 / ext4 (rw,errors=remount-ro)
/dev/sda5 /media/windows/D fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permis sions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Home Edition" /noexecute=optin /fastdetect

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ ${recordfail} = 1 ]; then
set timeout=-1
else
set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, met Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro quiet splash
initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, met Linux 2.6.32-12-generic (herstelmodus)" {
recordfail
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
echo	Loading Linux 2.6.32-12-generic ...
linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro single 
echo	Loading initial ramdisk ...
initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, met Linux 2.6.32-10-generic" {
recordfail
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro quiet splash
initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, met Linux 2.6.32-10-generic (herstelmodus)" {
recordfail
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
echo	Loading Linux 2.6.32-10-generic ...
linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro single 
echo	Loading initial ramdisk ...
initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1ea014dea014be69
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb6)" {
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sdb1 during installation
UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb5 during installation
UUID=fc52e245-6210-4feb-ba71-03921ad0558f none swap sw 0 0
# swap was on /dev/sdb7 during installation
UUID=3a3eeabc-2283-4001-acc6-62b2e56c514a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


.0GB: boot/grub/core.img
.0GB: boot/grub/grub.cfg
.0GB: boot/initrd.img-2.6.32-10-generic
.0GB: boot/initrd.img-2.6.32-12-generic
.0GB: boot/vmlinuz-2.6.32-10-generic
.0GB: boot/vmlinuz-2.6.32-12-generic
.0GB: initrd.img
.0GB: initrd.img.old
.0GB: vmlinuz
.0GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
have_grubenv=true
load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
saved_entry=${prev_saved_entry}
save_env saved_entry
prev_saved_entry=
save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
insmod gfxterm
insmod vbe
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
fi
fi
if [ ${recordfail} = 1 ]; then
set timeout=-1
else
set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
insmod png
if background_image /usr/share/images/grub/blauwwit.png ; then
set color_normal=black/black
set color_highlight=magenta/black
else
set menu_color_normal=white/black
set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
#	search --no-floppy --fs-uuid --set 1ea014dea014be69
drivemap -s (hd0) ${root}
chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sdb6 during installation
UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb7 during installation
UUID=3a3eeabc-2283-4001-acc6-62b2e56c514a none swap sw 0 0
/dev/sda5 /media/windows/D ntfs-3g rw,auto,user,fmask=0111,dmask=0000 0	 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

I think it's not good that grub is installed on both sda and sdb, but how to solve it?

Thanks in advance for any reply's.
Jzz

---

### Post by oldfred on 2010-02-10
You seem to have grub2 installed everywhere. You can reinstall windows to the MBR of your second drive but you also have to install the second part of the windows boot loader into the PBR where grub2 overwrote it.
It would be best to have the windows drive still set up to boot windows when/if it was the first drive in BIOS and have ubuntu/grub set to boot the other drive and have it set to boot first as it will find windows and boot it ok.

Temporary make the windows drive sda first in BIOS and use the windows CD to repair the windows drive.
Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:

Boot windows and check that it is ok. Then you can switch the ubuntu drive back to first in BIOS and run this to find the windows install.
sudo update-grub

---

### Post by Jzz5 on 2010-02-10
Oldfred,

Thanks for the quick response! That seems more than logical. Do I understand well that grub only needs to be installed on the drive where Ubuntu lives, as long as the BIOS points to that drive?

To be on the safe side, is it a good idea to physically disconnect the Ubuntu drive for the repair?

Thanks for the response,

Jzz

---

### Post by Jzz5 on 2010-02-11
Oldfred,

The solution worked, I'll mark the tread as solved. I disconnected the Ubuntu HDD and ran fixmbr and fixboot from the recovery disk. Then I re-connected the Ubuntu HDD and pointed the BIOS to that disk.

This also solved the older problem that Grub was taking a long time to load. Grub is now as fast as it was before the Grub2 upgrade. Furthermore I am again one step further in understanding how things work inside that metal case under my desk...

Thanks again!

Jzz

---

### Post by oldfred on 2010-02-11
Glad it worked. There was a minor bug in grub that adds 20 sec or so for searching if it is not on the same drive as the ubuntu install. You probably did not have to disconnect the drive as long as you changed the BIOS (not one time boot with f12), but it was safer that way.

---

