---
title: "X-files problem with grub2 and a recovery partition..."
date: 2010-02-04
forum: General Help
---

### Post by Koramchad on 2010-02-04
So, here is a tough one. I'll invite for a beer to whoever solves this mistery! I've been going crazy for a couple of days...
So, I have a Samsung NC10 with multiple OS on it. I was using Ubuntu 9.10 with Grub2 to manage them all and for a while everything was fine (or so I thought).
One of the OS I have is Jolicloud. Recently I noticed that they updated their kernel, but grub2 would not recognize it after updating it and wouldn't set an entry on the boot menu. Digging deeper, I found out that I'd been using the same old kernel for a while....
Trying to fix this I decided to manage my OS from Jolicloud, so I installed grub legacy from Jolicloud. I had to set up the menu.lst manually, but I thought everything was ok when I came up with THE PROBLEM.
My computer has a recovery partition that is hidden, used only to restore Windows XP to its original state. Turns out that somehow, I managed to install grub2 on that partition, because every time I try to boot the recovery partition, I automatically jump to the old grub2 menu. WHY??
I'm attaching a screen print of my hard disk structure and here is the entries for my menu.lst:

title		Jolicloud robby, kernel 2.6.32-6-jolicloud
uuid		338587ef-dec5-4ade-ad8f-5fb44f90a3b7
kernel		/boot/vmlinuz-2.6.32-6-jolicloud root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-6-jolicloud
quiet

title		Ubuntu 9.10
uuid		8b443e0e-418f-419d-ac7b-72d89738c41a
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=8b443e0e-418f-419d-ac7b-72d89738c41a ro quiet splash 
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

title 		Windows 7
rootnoverify 	(hd0,1)
savedefault
chainloader +1

title         	Windows Vista (loader)
rootnoverify 	(hd0,0)
savedefault
chainloader +1


ANY IDEAS?
Thanks so much!

---

### Post by coldraven on 2010-02-04
My Compaq came "downgraded" from Vista to XPpro.
I dual booted Ubuntu  and Xp but it had the compaq restore partition which was NT/2000.
One day I accidentally booted into the restore partition so I did nothing until it had finished booting then pressed cancel.
Too late, it had overwritten Grub.
In your case you had your "backup" Grub on a different partition so my guess is that whats happened. Note, this is just a guess!
Beer always welcome here.:D

My solution, delete all partitions and run Xp in VirtualBox

---

### Post by Koramchad on 2010-02-04
I don't think that might be the problem. The thing is, it seems that I have grub installed fine on my mbr for sda, but it also seem that (somehow) i have grub2 installed on my sda1 partition!
It makes no sense, because I still have all the data in sda1 as I show in the picture. Grub2 somehow managed to get into sda1 and I want it to leave RIGHT NOW! :P

---

### Post by Leppie on 2010-02-04
could you please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by Koramchad on 2010-02-05
See? Grub2 is installed on sda1!
I can see a beer coming soon, though... :)
DO you see anything useful Leppie?

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 103899668 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #3 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Jolicloud robby
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fa8a755

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960    96,582,779    83,987,820   7 HPFS/NTFS
/dev/sda3          96,582,780   116,117,819    19,535,040  83 Linux
/dev/sda4         116,117,820   312,576,704   196,458,885   f W95 Ext d (LBA)
/dev/sda5         116,117,946   135,652,859    19,534,914  83 Linux
/dev/sda6         135,652,923   155,187,899    19,534,977  83 Linux
/dev/sda7         304,769,178   312,576,704     7,807,527  82 Linux swap / Solaris
/dev/sda8         155,187,963   304,769,114   149,581,152   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0AA04890A04883E3                       ntfs       RECOVERY                      
/dev/sda2        281C4A201C49E980                       ntfs                                     
/dev/sda3        8b443e0e-418f-419d-ac7b-72d89738c41a   ext4       Ubuntu                        
/dev/sda5        45cd81c9-7db9-4a26-83a9-bc6bb53994c5   ext3                                     
/dev/sda6        338587ef-dec5-4ade-ad8f-5fb44f90a3b7   ext4                                     
/dev/sda7        cd7c01a4-6470-48d9-9425-82bc57e16022   swap                                     
/dev/sda8        9C63-67C7                              vfat       /datos                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda8        /datos                   vfat       (rw,utf8,umask=007,gid=46)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 8b443e0e-418f-419d-ac7b-72d89738c41a
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 8b443e0e-418f-419d-ac7b-72d89738c41a
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8b443e0e-418f-419d-ac7b-72d89738c41a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0aa04890a04883e3
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 281c4a201c49e980
	chainloader +1
}
menuentry "Memory Test (on /dev/sda5)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 45cd81c9-7db9-4a26-83a9-bc6bb53994c5
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda5)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 45cd81c9-7db9-4a26-83a9-bc6bb53994c5
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda5)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 45cd81c9-7db9-4a26-83a9-bc6bb53994c5
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro single
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda5)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 45cd81c9-7db9-4a26-83a9-bc6bb53994c5
	linux /boot/memtest86+.bin 
}
menuentry "Jolicloud robby, kernel 2.6.32-6-jolicloud (on /dev/sda6)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 338587ef-dec5-4ade-ad8f-5fb44f90a3b7
	linux /boot/vmlinuz-2.6.32-6-jolicloud root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro quiet splash
	initrd /boot/initrd.img-2.6.32-6-jolicloud
}
menuentry "Jolicloud robby, kernel 2.6.32-6-jolicloud (recovery mode) (on /dev/sda6)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 338587ef-dec5-4ade-ad8f-5fb44f90a3b7
	linux /boot/vmlinuz-2.6.32-6-jolicloud root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro single
	initrd /boot/initrd.img-2.6.32-6-jolicloud
}
menuentry "Jolicloud robby, memtest86+ (on /dev/sda6)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 338587ef-dec5-4ade-ad8f-5fb44f90a3b7
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Backtrack 4" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 45cd81c9-7db9-4a26-83a9-bc6bb53994c5
	linux /boot/vmlinuz-2.6.30.9 ro vga=0x317
	initrd /boot/initrd.img-2.6.30.9
}
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=8b443e0e-418f-419d-ac7b-72d89738c41a /               ext4    errors=remount-ro 0       1
# /Jolicloud was on /dev/sda6 during installation
#UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 /Jolicloud      ext4    defaults        0       2
# /Moblin was on /dev/sda5 during installation
#UUID=cf63231f-8fb8-4182-b0de-38b9426b19a2 /Moblin         ext3    defaults        0       2
# /datos was on /dev/sda8 during installation
UUID=9C63-67C7  /datos          vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda2 during installation
UUID=281C4A201C49E980 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda7       none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  53.2GB: boot/grub/core.img
  49.6GB: boot/grub/grub.cfg
  54.8GB: boot/initrd.img-2.6.31-17-generic
  54.3GB: boot/vmlinuz-2.6.31-17-generic
  54.8GB: initrd.img
  54.3GB: vmlinuz

=========================== sda5/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

vga=0x317image=/boot/grub/bt4.xpm.gz


title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a76c7835-eb6f-459f-a891-496f16bc00eb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

splashimage=a76c7835-eb6f-459f-a891-496f16bc00eb/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.30.9
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=45cd81c9-7db9-4a26-83a9-bc6bb53994c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=cd7c01a4-6470-48d9-9425-82bc57e16022 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  63.6GB: boot/grub/menu.lst
  63.5GB: boot/grub/stage2
  63.7GB: boot/initrd.img-2.6.30.9
  63.5GB: boot/vmlinuz-2.6.30.9
  63.7GB: initrd.img
  63.5GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## debug [on | off | normal | status | INTEGER]
# Turn on/off or display/set the debug level.
debug		off

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=338587ef-dec5-4ade-ad8f-5fb44f90a3b7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Jolicloud robby, kernel 2.6.32-6-jolicloud
uuid		338587ef-dec5-4ade-ad8f-5fb44f90a3b7
kernel		/boot/vmlinuz-2.6.32-6-jolicloud root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-6-jolicloud
quiet

title		Ubuntu 9.10
uuid		8b443e0e-418f-419d-ac7b-72d89738c41a
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=8b443e0e-418f-419d-ac7b-72d89738c41a ro quiet splash 
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

title 		Windows 7
rootnoverify 	(hd0,1)
savedefault
chainloader +1

title         	Windows Vista (loader)
rootnoverify 	(hd0,0)
savedefault
chainloader +1

title		Jolicloud robby, kernel 2.6.32-6-jolicloud (recovery mode)
uuid		338587ef-dec5-4ade-ad8f-5fb44f90a3b7
kernel		/boot/vmlinuz-2.6.32-6-jolicloud root=UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 ro  single
initrd		/boot/initrd.img-2.6.32-6-jolicloud

title		Jolicloud robby, memtest86+
uuid		338587ef-dec5-4ade-ad8f-5fb44f90a3b7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=338587ef-dec5-4ade-ad8f-5fb44f90a3b7 /               ext4    relatime,errors=remount-ro 0       1
# /datos was on /dev/sda8 during installation
UUID=9C63-67C7  /datos          vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=654d6e22-446d-440e-813a-9178e705cd1a none            swap    sw              0       0
```

---

### Post by Leppie on 2010-02-05
ok, it seems you only did install grub2 to the mbr of sda1.
first make a backup of the mbr of sda1:
```
sudo mount /sda3 /mnt
sudo dd if=/dev/sda1 of=/mnt/home/backup_mbr.dd bs=446 count=1
```
now we can reset the mbr of sda1:
```
sudo dd if=/dev/zero of=/dev/sda1 bs=446 count=1
```

continuing with the same terminal session, to re-install grub2 to the mbr of the drive (no partition):
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
after this you should be able to boot into ubuntu again, once in ubuntu you can update your grub2 menu:
```
sudo update-grub
```

---

### Post by Koramchad on 2010-02-05
My problem is with sda1, not sda3. I am using Jolicloud with grub legacy on sda6 (after not being able to make grub2 recognize the latest kernel on jolicloud) and I'm fine with that one. What I want to remove is that &%$&& grub2 from sda1... Can I do that without damaging the partition?

---

### Post by meierfra. on 2010-02-05
> sudo mount /sda3 /mnt
sudo dd if=/dev/sda1 of=/mnt/home/backup_mbr.dd bs=446 count=1
This won't help and only cause harm, you won't be able to mount the recovery partition any more.

 
I suggest to use  testdisk to restore  the boot sector of  recovery partition. Boot into your Ubuntu 9.10

Install testdisk via:

   ```
sudo apt-get install testdisk
```
If "apt-get" cannot find "testdisk" you  need to enable the universe repository.

Start testdisk via

```
  sudo testdisk /dev/sda
```


First   screen:  Press enter to "proceed".
Second    screen:  "intel"
Third  screen:  "advanced",
Fourth  screen:  Select the recovery partition (although it should be  selected already) and choose "boot"
Fifth  screen:  "BackupBS" 
Type "Y" to confirm.

Then press "q" a few times to quit testdisk.



After that Jolicloud's  Legacy Grub  should be able boot your recovery partition.


> Digging deeper, I found out that I'd been using the same old kernel for a while....
You needed to run "update-grub" from Ubuntu 9.10. Or did you try that?


Would you like to keep using Jolicoud's Grub Legacy or would you like to switch back  Ubuntu's Grub 2?  

The Legacy grub should work just fine, but the menu.lst needs some fixing to avoid problems after kernel updates.

Either way, with little bit of work, one can configure menu.lst/grub.cfg so that it automatically boots the newest kernel of each OS.

Just asked, and we can help you with that.

---

### Post by Koramchad on 2010-02-05
Thanks so much meierfra, I was looking for a tool like that.
First problem. I don't get the option Boot when selecting my recovery partition... Any ideas?

PS: First I want to get this fixed, I will deal with grub2 when all is settled...  I did do the update-grub AND edit the file manually, but still wouldn't boot with the newest kernel... Oh well, I'll deal with that later! ;)

THANKS!!

---

### Post by meierfra. on 2010-02-05
>  I don't get the option Boot when selecting my recovery partition... Any ideas?

I'm not sure. But maybe testdisk gets confused since your recovery partition has type "12". At the same screen, with the recovery partition selected, choose "type" . At the new screen hit 'enter" to proceed. Type "07" and press enter. 
Does this give you the "boot" tab? If not quit testdisk and try again.

---

### Post by Koramchad on 2010-02-05
It does give me the Boot tab, but under it I get the options "Org. BS" "Rebuild BS" and "Dump"
I'm tempted to click on Rebuild, but I want to confirm first...

---

### Post by Koramchad on 2010-02-05
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1   783 254 63   12594897

Boot sector
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]

```

---

### Post by meierfra. on 2010-02-05
RebuildBS won't help.

Could you post a screen shot?

---

### Post by meierfra. on 2010-02-05
You are reading my mind. 

> Backup boot sector
Status: Bad

That's the problem.  There is something wrong with the backup boot sector. So testdisk  refuses to use it. Do you have a Window 7 CD/DVD?

---

### Post by Koramchad on 2010-02-05
I can get it on a usb drive... Can I fix it with that? Even if it's the recovery partition? It supposedly has a backup of Windows XP on it, but still...

---

### Post by meierfra. on 2010-02-05
Edit:  Just saw your latest post.  Please ignore this until further notice.


Since testdisk did not work, lets try "bootsect" from Windows CD/DVD. (if you don't have  one,you get  a recovery CD from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"))


Boot from the Window 7 CD.
At the first screen select your favorite language.
At the second screen choose "Repair your Computer".
If a pop up  appears, offering  to repair a problem with the "Startup options",   decline the offer,
On the next screen, choose  "Use recovery tools ..." and click on "Next".
Choose "Command Prompt"  and click on "Next".

Type 
```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your recovery  partition and your CDrom drive.  Type

```
 exit
``` to exit the ``diskpart'' prompt.

Then 
```
E:\boot\bootsect.exe /nt60  D:
```
But replace 'E:' and "D:" by the actual drive letters of your CDRom drive and Recovery partition.

Edit:  The actual location of bootsect.exe depends the Window 7 CD. If you use the CD from my link just do

```
bootsect  /nt60  D:
```

---

### Post by meierfra. on 2010-02-05
> It supposedly has a backup of Windows XP on it, but still...

XP?  Did you used to have XP on the computer and upgraded to Window 7?  Did you ever booted into your recovery partition?

You have "bootmgr" and "/boot/bcd" on that partition. So Window 7 or Vista put some boot files on that partition. Since you also have "bootmgr" and "boot/bcd" on  your Window 7 partition, I assumed that those files are for booting the recovery  partition.

So now I'm not sure what kind of boot sector your need for the recovery partition. Either an XP boot sector or  Vista/Window 7.

Did you every move any boot files?

---

### Post by Koramchad on 2010-02-05
Yeah, the computer came with Windows XP, so the recovery partition holds a backup of Windows XP. I upgraded later to Windows 7, but without modifying the recovery partition.
There is an application from Samsung (Samsung Recovery) that allows you to restore the system using the recovery partition. When I try to use it now, it says that it can't detect the recovery partition. That might be why of the bootmgr and /boot/bcd...
I never touched the recovery partition, always accessed it throught Samsung Recovery, so I'm guessing it will still be like Windows XP. Does this change the method to restore the MBR you described before?

---

### Post by meierfra. on 2010-02-05
Let's  have a look at your current extended boot sector

```

cd ~/Desktop
sudo dd if=/dev/sda1 of=boot_sector.bin count=16
tar -czvf boot_sector.bin.tar.gz boot_sector.bin

```
Be very careful with the "dd" command. If it runs for more than just a couple of seconds, kill the process with "ctrl+c".

This creates the files boot_sector.bin.tar.gz and  boot_sector.bin on your Desktop.  Attach  "boot_sector.bin.tar.gz" to your next post.

---

### Post by Koramchad on 2010-02-05
Here it is!
Again, thanks so much for all your help!


This is the output for the dd command:
```
gandhi@nc10:~/Desktop$ sudo dd if=/dev/sda1 of=boot_sector.bin count=16
[sudo] password for gandhi: 
16+0 records in
16+0 records out
8192 bytes (8.2 kB) copied, 0.059029 s, 139 kB/s

```

---

### Post by meierfra. on 2010-02-05
Ok. /dev/sda1 has a  Vista/Win 7 boot sector.   So my instruction from post 16 should work. But as long as I already made you use "dd",  you could also  just use dd  to the copy  the boot sector  from /dev/sda2 to /dev/sda1:


```
sudo dd if=/dev/sda2 of=/dev/sda1 bs=1 count=16
sudo dd if=/dev/sda2 of=/dev/sda1 bs=1 seek=96 skip=96 count=416 
```

(As before, be very careful with the "dd" command. If it runs for more than just a couple of seconds, kill the process with "ctrl+c".


This copies the first 16  and the last 416 bytes of the boot sector of /dev/sda2 to /dev/sda1 (the 80 bytes in between contain information  about your files system, and so are different for different ntfs partition. Luckily Grub 2  was smart enough not to overwrite that part of the boot sector.

---

### Post by Koramchad on 2010-02-05
ahhhhhhhhhhhhhhhhh!!!
It didn't work... I tried to boot from the recovery partition and got a black screen. Samsung recovery also gave me an error when I tried to execute it from Windows 7.
I'm going to try with the recovery tools from the Windows 7 cd... Wish me luck! :)

---

### Post by Leppie on 2010-02-05
good luck ;)

---

### Post by meierfra. on 2010-02-05
> It didn't work.
Did you ever access the recovery partition since you installed Window 7?  Maybe the problem  was already  caused by Window 7 overwriting the XP boot sector. 


> try with the recovery tools from the Windows 7 cd... 

Are you using  the Window 7 CD from my link?  I just realized that  the procedure to run "bootsect" from that CD is slighly different. See my edit in post 16.

---

### Post by Koramchad on 2010-02-05
This is getting interesting!
I'm on diskpart now, and it recognized the Windows 7 as a NTFS partition as my C, the FAT32 I use for data as D and the usb I'm booting Windows 7 from as E. Then it says that there is a NTFS RECOVERY partition with is Healthy and Hidden, but without a Letter... I'm trying to figure out how to mount that partition from diskpart or from the command line... Any suggestions?

---

### Post by Koramchad on 2010-02-05
> **meierfra. said:**
> Did you ever access the recovery partition since you installed Window 7?
I never did. Maybe that is the problem, maybe it was evil Windows and not nice Grub2 and I've been blaming it the whole time. Makes more sense, though... :)

---

### Post by Koramchad on 2010-02-05
YAAAAAAY!!!
It worked like a charm!
I had to tweak diskpart a little bit to mount the recovery partition, but after I Got that done (more info here --> [http://technet.microsoft.com/en-us/library/cc770877%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc770877%28WS.10%29.aspx)) then I just had to follow meierfra's instructions.
Thank you both so much!!

PS: Where should I send the beers to? ;)

---

### Post by meierfra. on 2010-02-05
Deleted. Just saw your new post.

---

### Post by meierfra. on 2010-02-05
> I had to tweak diskpart a little bit to mount the recovery partition, but after 
Can you tell me exactly what you did? Maybe I can learn something. Did you change the "hidden" attribute?

> YAAAAAAY!!!
It worked like a charm!
Great. So it was evil Grub and not nice Window 7 :)

> Where should I send the beers to?


1600 Pennsylvania Avenue NW
Washington, DC 20500

---

### Post by Koramchad on 2010-02-05
> **meierfra. said:**
> Can you tell me exactly what you did? Maybe I can learn something. Did you change the "hidden" attribute


No, the hidden attribute didn't turn out to be significant. What I did was:
diskpart
list volume
[INDENT]Saw that the Recovery partition was volume 3[/INDENT]
select volume=3
[INDENT]active[/INDENT]
[INDENT]assign letter=j[/INDENT]

And voila! My Recovery partition was active and accesible through J.

---

### Post by meierfra. on 2010-02-05
> select volume=3

    assign letter=j
Nice. I didn't know one could just assign letters.

---

### Post by Leppie on 2010-02-06
good to know.
learned a lot in this thread. thanks both :)

---

### Post by Koramchad on 2010-02-06
I know, me too!
So if anybody has the same problem with a Samsung NC10 and the Samsung Recovery partition, here is the solution! (index it google! :P)

---

