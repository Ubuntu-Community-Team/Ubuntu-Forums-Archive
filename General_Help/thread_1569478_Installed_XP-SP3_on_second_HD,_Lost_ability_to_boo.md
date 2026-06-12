---
title: "Installed XP-SP3 on second HD, Lost ability to boot to Ubuntu"
date: 2010-09-06
forum: General Help
---

### Post by BothEyesShut on 2010-09-06
Hi all and thanks in advance,

I've been running Jaunty on my drive D: with XP Professional on a separate partition.

Today I formatted a different drive, C:, which had previously shown up in GRUB as XP Home Edition, and placed a new XP Professional on it.

Now when both HDs are connected, C: boots without GRUB starting, and when I disconnect C:, the GRUB on D: starts, but cannot find the XP Professional NTDLR.

I don't want to take up too much of anyone's time here with this; I'm mostly just curious as to what may have happened?

Thanks, everyone.

---

### Post by 73ckn797 on 2010-09-06
If you want the Ubuntu boot selection menu follow this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The Windows installation rewrote the MBR on the Windows drive and if is drive C:\ then it will be the first boot disk. You could go into BIOS and select which drive to boot from but that would require pressing F8 or some other key during the initial boot process.

---

### Post by oldfred on 2010-09-07
73ckn797 link is to grub legacy which is correct if you are still running 9.04.

This covers both old grub and new grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


If you changed windows this sometimes works with old grub.
sudo update-grub

Grub2 almost always finds other operating systems. Sometimes with old grub we had to update the boot stanza in menu.lst as grub could not find other systems.

If you want more help run this script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by BothEyesShut on 2010-09-08
Gentlemen!

Thank you so much for your detailed replies and suggestions.  My favorite thing about using Linux has always been the incredible community support.

To [73ckn797]("http://ubuntuforums.org/member.php?u=641480"): I have tried switching the boot order in BIOS, but my BIOS does not differentiate between the two hard drives.  It simply gives me options for USB, CD/DVD, HD, and a couple random options which do not seem at all applicable.

To [oldfred]("http://ubuntuforums.org/member.php?u=852711"): I'm fairly certain that I'm still running Jaunty (therefore, GRUB Legacy).  Someone told me that Ubuntu updates itself to higher versions, though, in which case I may be running Karmic or something -- not real important; I can unhook C: to boot to D: and find out which version.

I will try these options.  Won't have a chance until this weekend at earliest.

If I were to blow out my Linux partition and install Natty on it, do you think I could fix my GRUB problem that way?  Gosh, it'd be a nice excuse to check out the new version, anyhow.

Thank you so much, gentlemen.

Cheers!

-Both

---

### Post by oldfred on 2010-09-08
If your BIOS is new enough to let you boot USB it should have a choice for which hard drive. Some have it as part of choosing the hard drive then choosing which hard drive, others have a totally separate choice somewhere else that lets you choose which drive is first as the default. 

Also what choices do you get with a one time boot key (often f12), BIOS screen should tell you which key.

Older BIOS with only PATA/IDE support relied on the jumpers on the hard drive for master/slave and primary/seconday and only booted primary master. Or you could set jumpers to cable select (with 80 conductor cables) and the connector on the cable determined master.

---

### Post by BothEyesShut on 2010-09-08
Dear Oldfred, 

Thank you very much for your replies.

I will experiment more with my BIOS, which is whatever BIOS shipped with Gigabyte's EP45 Ultra Durable series motherboard that season (fall 2009, I think).

I toyed with the idea of playing with the jumpers, but I've long forgotten how those settings used to work.  I started building my own comps at about the same time that slave/master stopped mattering.

Thanks again.

---

### Post by oldfred on 2010-09-08
I only have SATA drives with the Gigabyte EP43. I have one choice that chooses hard drive order and then first boot device, second boot device.

It was very strange that the USB-HD setting would not let me select my flash drive to boot. But under hard drives there was the flash drive.

---

### Post by BothEyesShut on 2010-09-11
OK fellas, 

so I finally found a way to boot to D:, but it says my NTLDR is missing and I still can't get to my windows files and programs.  To experiment with GRUB2, I installed Natty on C:, but I still can't boot to windows on D:, which I guess isn't surprising.  I've done what you said, OldFred, and am going to post my bootinfo script results here.  Thank you so, so much for your advice.  Without it I think I'd lose everything on that drive.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1    *             63   780,339,925   780,339,863   7 HPFS/NTFS
/dev/sda2         780,341,246   976,773,119   196,431,874   5 Extended
/dev/sda5         780,341,248   968,693,759   188,352,512  83 Linux
/dev/sda6         968,695,808   976,773,119     8,077,312  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,745,157,014 1,745,156,952   7 HPFS/NTFS
/dev/sdb2    *  1,745,157,015 1,940,475,284   195,318,270  83 Linux
/dev/sdb3       1,940,475,346 1,953,520,064    13,044,719   5 Extended
/dev/sdb5       1,940,475,348 1,953,520,064    13,044,717  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0858AA0158A9EE1E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7466e7fc-a6f7-477d-b4c5-4506a62e49d4   ext4                                     
/dev/sda6        cb41854b-4edf-4136-801e-62b4449b3702   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        86D4B3D5D4B3C629                       ntfs                                     
/dev/sdb2        5c1963af-87a4-45b4-918d-36be9043c73d   ext3                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        d5ee87d4-5a5a-40ad-a1dd-20d8a7b58846   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/SC2-L100-D1       udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7466e7fc-a6f7-477d-b4c5-4506a62e49d4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7466e7fc-a6f7-477d-b4c5-4506a62e49d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7466e7fc-a6f7-477d-b4c5-4506a62e49d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0858aa0158a9ee1e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro single
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb2)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5c1963af-87a4-45b4-918d-36be9043c73d
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7466e7fc-a6f7-477d-b4c5-4506a62e49d4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cb41854b-4edf-4136-801e-62b4449b3702 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 459.8GB: boot/grub/core.img
 483.5GB: boot/grub/grub.cfg
 459.8GB: boot/initrd.img-2.6.32-24-generic-pae
 459.8GB: boot/vmlinuz-2.6.32-24-generic-pae
 459.8GB: initrd.img
 459.8GB: vmlinuz

=========================== sdb2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5c1963af-87a4-45b4-918d-36be9043c73d

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
# howmany=all

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=5c1963af-87a4-45b4-918d-36be9043c73d ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, memtest86+
uuid        5c1963af-87a4-45b4-918d-36be9043c73d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=5c1963af-87a4-45b4-918d-36be9043c73d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d5ee87d4-5a5a-40ad-a1dd-20d8a7b58846 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 931.2GB: boot/grub/menu.lst
 931.2GB: boot/grub/stage2
 931.1GB: boot/initrd.img-2.6.31-16-generic
 946.8GB: boot/initrd.img-2.6.31-17-generic
 962.0GB: boot/initrd.img-2.6.31-19-generic
 934.8GB: boot/initrd.img-2.6.31-20-generic
 931.1GB: boot/vmlinuz-2.6.31-16-generic
 931.4GB: boot/vmlinuz-2.6.31-17-generic
 962.0GB: boot/vmlinuz-2.6.31-19-generic
 942.2GB: boot/vmlinuz-2.6.31-20-generic
 934.8GB: initrd.img
 962.0GB: initrd.img.old
 942.2GB: vmlinuz
 962.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  70 a8 4f 45 2c bb 0f 8d  f4 20 04 c0 80 06 00 0f  |p.OE,.... ......|
00000010  c1 03 f3 81 03 f2 f8 ff  80 3c 00 79 fe d4 ca ed  |.........<.y....|
00000020  70 03 bb 2f 99 1f a4 0e  59 70 9b e6 34 a1 ed db  |p../....Yp..4...|
00000030  ec f2 7e 51 96 37 07 be  5f 69 54 b6 ff b0 80 17  |..~Q.7.._iT.....|
00000040  7b e3 96 d9 47 f9 b9 fc  3f 85 ca 1d 43 e2 53 62  |{...G...?...C.Sb|
00000050  92 db 9a 00 49 fd e9 ee  00 78 00 ee e3 e2 cb 36  |....I....x.....6|
00000060  88 16 2b 71 f1 4f 96 c8  fd 99 6c a5 50 86 f0 a0  |..+q.O....l.P...|
00000070  80 07 9f 3c de 33 bc ef  e9 ee ea 9b 9d 49 db c8  |...<.3.......I..|
00000080  13 6d 8f c0 30 f4 b0 db  29 4d d5 04 00 2a e3 dc  |.m..0...)M...*..|
00000090  01 48 02 80 07 dc fb e7  16 2c dc 14 47 fc b9 cf  |.H.......,..G...|
000000a0  b6 54 59 b2 da 90 6a 46  ed 96 6c 2d 63 7c fe bb  |.TY...jF..l-c|..|
000000b0  71 f1 2e 50 c0 96 df 52  b1 29 61 60 32 18 c7 2d  |q..P...R.)a`2..-|
000000c0  da 05 96 18 d4 c2 95 48  6a cb 62 a7 89 44 26 25  |.......Hj.b..D&%|
000000d0  69 46 db 72 96 06 da 42  e4 00 ed b3 13 4e 25 96  |iF.r...B.....N%.|
000000e0  d7 2a 01 cc 4a b1 94 21  36 d1 2a b0 ca 88 1a cb  |.*..J..!6.*.....|
000000f0  85 8c 52 11 cd 21 50 bf  42 da a3 4c 2d 1b 45 5f  |..R..!P.B..L-.E_|
00000100  50 92 9a d8 5c 1c 5a 00  70 d4 21 43 6f a1 0d 6b  |P...\.Z.p.!Co..k|
00000110  3e 53 60 f5 1c cc f6 11  1b 6c 95 68 17 16 32 d0  |>S`......l.h..2.|
00000120  ea 59 41 27 b0 26 a1 5e  be 31 ac 85 2f ab 36 84  |.YA'.&.^.1../.6.|
00000130  6d ce 8a 90 60 49 44 96  df 15 f4 28 6b 50 5a 8d  |m...`ID....(kPZ.|
00000140  24 35 d5 74 2c b6 29 6c  46 db 30 b9 7d 5a ac 5c  |$5.t,.)lF.0.}Z.\|
00000150  96 55 3b d5 ad a5 80 0d  da bd a8 80 5f 83 5d 64  |.U;........._.]d|
00000160  39 b6 00 43 00 55 1e 03  e6 e4 2d 89 07 fa 37 66  |9..C.U....-...7f|
00000170  ab ad 01 fb 71 40 71 20  43 41 cd ac 0f 6c 24 36  |....q@q CA...l$6|
00000180  42 db 78 04 f5 b9 e4 db  1b 64 9e 70 7d 2d 99 ec  |B.x......d.p}-..|
00000190  22 36 bf 29 8a 80 32 59  ea d9 61 48 06 9b 41 72  |"6.)..2Y..aH..Ar|
000001a0  16 14 12 d8 40 71 20 48  00 fd 9b 10 b0 a6 cb 2a  |....@q H.......*|
000001b0  52 c0 64 d3 03 e0 e5 3d  14 31 a9 c5 ca 35 00 fe  |R.d....=.1...5..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 3a 0b 00 fe  |............:...|
000001d0  ff ff 05 fe ff ff 02 08  3a 0b 00 48 7b 00 00 00  |........:..H{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-09-11
When you installed the second windows did it see the first copy of windows? If so it will delete the boot files from the second install and update the first installs boot.ini or BCD to boot the second install. Windows can only boot thru one partition that is active (boot flag).

Your NTFS in the 1000GB drive has no boot files. But the install in sda1 only shows drive 0 and partition 1 as boot choices. You could try repairing the install in sdb1 if it is a full install. You can copy your 
/boot.ini /ntldr /NTDETECT.COM files from sda1 to sdb1. You probably will have to edit boot.ini. You will also need to move the boot flag from sdb2 to sda1. Grub does not use the flag but if you have to directly boot or repair the partition window's will only work with the boot flag.

set boot flag on for sdb1(off for others on sdb)
sudo sfdisk -A1 /dev/sdb

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by BothEyesShut on 2010-09-14
Dear OldFred,

That's got it!  I can happily report that, once again, Ubuntu community has proven itself.

I followed your suggestions and copied the NTLDR and NTDETECT.com files to my root directory on the Windows side, and yes, I did have to edit the boot.ini, as well as move the boot flag (I had never heard of this before; I come from the DOS era, and this was still far beyond my experience).

I looked around at Multibooters.co.uk, also, and that was, if nothing else, comforting.

Everything's running swell now, and Ubuntu is happily doing all my networking while my Win allows my girlfriend to use her cherished programs that won't run in WINE.

Can't tell you how much I appreciate all this help, Mr. Fred.  I hadn't intended to take up so much time -- I was really ready to just blow it out and start over!  Thanks so very much!

Cheers, 


-BothEyes

---

### Post by oldfred on 2010-09-14
Glad you got it working.:)

---

