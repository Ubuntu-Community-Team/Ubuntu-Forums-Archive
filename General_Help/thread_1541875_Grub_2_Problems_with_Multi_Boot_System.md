---
title: "Grub 2 Problems with Multi Boot System"
date: 2010-07-29
forum: General Help
---

### Post by grimreap3r on 2010-07-29
Running i7 desktop with the following setup:

2TB WD HD, partitioned in 8 partitions.  So far I have:

sda1 windows7 x64

sda2 Ubuntu 10.04 x64

sda3 Bactrack 4 Final

sda4 (extended)

sda5 Windows XP x64  (just added)

The rest of the partitions are empty as of now. Everything has been fine with the windows, ubuntu, and backtrack, but when I add XP in the mix it won't boot windows 7 anymore.  Although in the grub menu it shows:

Ubuntu 
Windows 7
Backtrack (backtrack shows up at Ubuntu 8.10 in grub)

XP does not show up on the menu, but when I choose windows 7 at boot, it boots XP instead.  Weird I know.  This is the second time I have attempted this, and it has done the same thing each time.  I ran the boot script as well.  Here are the results:



[SIZE="2"]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 3,094,359,974 3,094,359,912   7 HPFS/NTFS
/dev/sda2       3,094,359,975 3,406,422,599   312,062,625  83 Linux
/dev/sda3       3,406,422,600 3,511,278,854   104,856,255  83 Linux
/dev/sda4       3,511,278,855 3,907,024,064   395,745,210   5 Extended
/dev/sda5       3,511,278,918 3,616,135,109   104,856,192   7 HPFS/NTFS
/dev/sda6       3,616,135,173 3,720,991,364   104,856,192  83 Linux
/dev/sda7       3,720,991,428 3,727,288,844     6,297,417  82 Linux swap / Solaris
/dev/sda8       3,727,288,908 3,907,024,064   179,735,157   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,525,167 1,953,525,105   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8032 MB, 8032092160 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    15,679,439    15,679,377   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F0E2102CE20FF59E                       ntfs                                     
/dev/sda2        4ff60099-cf6f-4cf5-9adc-837509d86358   ext4       UBUNTU                        
/dev/sda3        4466c7b2-9917-49c9-94e9-47d9c9238e63   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8EA41D69A41D54D5                       ntfs       winxp                         
/dev/sda6        11e00616-b3bc-4f4c-9e78-485b671d41c1   ext3       FEDORA                        
/dev/sda7        b712beb8-eb28-45e5-8d17-ac24b1d2d258   swap                                     
/dev/sda8        128C3D138C3CF2B9                       ntfs       SUSE                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        030A9D5656CBBD1F                       ntfs       INTERNAL-STORAGE              
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1CC4E597C4E57384                       ntfs       MONSTER_DRIVE                 
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        58E4A4B5E4A496B2                       ntfs       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/PENDRIVE          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/MONSTER_DRIVE     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/F0E2102CE20FF59E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4ff60099-cf6f-4cf5-9adc-837509d86358
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4ff60099-cf6f-4cf5-9adc-837509d86358
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
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 4ff60099-cf6f-4cf5-9adc-837509d86358
insmod png
if background_image /boot/grub/skull.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4ff60099-cf6f-4cf5-9adc-837509d86358
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=4ff60099-cf6f-4cf5-9adc-837509d86358 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4ff60099-cf6f-4cf5-9adc-837509d86358
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4ff60099-cf6f-4cf5-9adc-837509d86358 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set /dev/sda1
	chainloader +1
}
menuentry "Memory Test (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4466c7b2-9917-49c9-94e9-47d9c9238e63
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4466c7b2-9917-49c9-94e9-47d9c9238e63
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4466c7b2-9917-49c9-94e9-47d9c9238e63
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro single
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4466c7b2-9917-49c9-94e9-47d9c9238e63
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=4ff60099-cf6f-4cf5-9adc-837509d86358 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b712beb8-eb28-45e5-8d17-ac24b1d2d258 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


1633.8GB: boot/grub/core.img
1704.7GB: boot/grub/grub.cfg
1633.9GB: boot/initrd.img-2.6.32-21-generic
1634.0GB: boot/initrd.img-2.6.32-23-generic
1633.8GB: boot/vmlinuz-2.6.32-21-generic
1598.4GB: boot/vmlinuz-2.6.32-23-generic
1634.0GB: initrd.img
1598.4GB: vmlinuz

=========================== sda3/boot/grub/menu.lst: ===========================

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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4466c7b2-9917-49c9-94e9-47d9c9238e63 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b712beb8-eb28-45e5-8d17-ac24b1d2d258 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


1792.8GB: boot/grub/menu.lst
1792.8GB: boot/grub/stage2
1792.8GB: boot/initrd.img-2.6.30.9
1792.8GB: boot/vmlinuz-2.6.30.9
1792.8GB: initrd.img
1792.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh [/SIZE]

---

### Post by giddyup306 on 2010-07-29
When I had 2000, XP, Ubuntu, one-of-the-other-buntus on my system I had to install one windows OS immediately after the other first.  When I was in grub I had to exit it and go to the windows boot loader.  I don't even know if there is a way to fix this...

---

### Post by wilee-nilee on 2010-07-29
Could you edit your post by putting the script in code tags. This creates a scrolling window that is easier to read. Two ways to do it, edit-advanced highlight the text then click on # in edit panel resubmit. Or; [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by oldfred on 2010-07-29
Windows really needs to be installed to a primary partition. A second install will work in a logical only if you boot though the windows install in a primary partition. If you look at sda1 you will now see both your win7 and XP boot files. You may be better off with the XP install in one of your other drives. If your win7 does not boot you may need to run repairs so it sees both installs with bcdedit.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

