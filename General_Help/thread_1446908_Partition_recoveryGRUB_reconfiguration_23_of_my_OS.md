---
title: "Partition recovery/GRUB reconfiguration/ 2/3 of my OSes won't boot"
date: 2010-04-04
forum: General Help
---

### Post by basketballler77 on 2010-04-04
First off, I apologize if I am posting this in the incorrect place. Not only possibly in the wrong board, but also possibly in the wrong forum. Due to the complex nature of the crap I've dug myself into, it may fit into many different places. The reason I am posting here is because my desktop Ubuntu partition is the one that will still boot up, and therefore likely how I will fix this problem.

I believe I have a rather novel problem. After upwards of 10 hours of attempts by myself to correct the problems, I now turn to your guidance. I first will explain the background and details of my problem, and then provide possible diagnostic information that may help you in understanding my problem. I hope it is not too much information and I extremely appreciate your help and wish this to be as easy as possible for both of us. =]

I have a computer I recently built with a 250GB hard drive, specifically for fooling around with Linux. I originally installed Ubuntu 9.10 desktop edition for normal use. I later decided to install the beta of 10.04, server edition, to get more experience with the CLI and to do some testing of the new release. Both of these installs inhabited my hard drive successfully for weeks. Then one day last week I decided to install Fedora 12 as well. The installation appeared to go well, including resizing my 10.04 partition. I booted into Fedora, spent a few hours downloading applications which I wanted to try (including the FEL spin ([https://spins.fedoraproject.org/fel/](https://spins.fedoraproject.org/fel/))). I rebooted the computer, and this time it booted straight into Fedora. I read online that, in order to fix this problem, I should boot Ubuntu with a live CD and run "sudo update-grub," or something like that. I wish I could find the original post so that I could have exactly what the instructions were. This allowed me to boot into the Ubuntu desktop edition again, but now I cannot boot into 10.04 or Fedora.

Inside 9.10 I have been able to back up all important data from all of my partitions, so I would not loose any physical data by reinstalling anything; however, I would extremely prefer, if at all possible, to fix GRUB so that it will boot my other partitions, so that I do not have to spend the hours re-doing all of the custom installations and settings.

I tried booting in manually from the GRUB prompt in various ways (It admittedly took me a while to figure out that GRUB1 commands, which were many of the examples I found, would not work in my GRUB because GRUB2 is installed...) but they all failed. At one point the logo showed up, but the boot still failed. The message was always either something along the lines of "/dev/sdaX could not be mounted because mtab says it is already mounted. Check mtab and /sysroot for /dev/sdaX," or it simply reported "Boot failed. Permanently sleeping" (Again, I cannot remember the phrases exactly.)

Lucid's problems are during the startup. It shows fsck beginning and reports what it is checking, but then it hangs during the check. If there are certain files for any of the operating systems that would contain crash logs, I can likely access them.

I was able to boot up with the same live CD that I installed Fedora with, and it acted differently than Ubuntu regarding the hard drives. I have uploaded a screenshot of Palimpsest Disk Utility running from the live CD to [http://imgur.com/5n86g](http://imgur.com/5n86g) (apparently I haven't been a member long enough to attach files). As I mentioned earlier, I have only a 250GB Hard drive, but the disk utility thinks I have 3 drives totaling over 310GB. (also notice that I have 15.3GB of swap space...) The first two hard drives listed in the picture are the ones that do not show up in Ubuntu and are located at /dev/dm-{0-3}.

I will now give you some details that I have based upon data I have access to in my 9.10 installation.

sudo fdisk -l returns:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d645

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61440000   83  Linux
/dev/sda2           15234       30401   121831105+   5  Extended
/dev/sda3   *        7649        7675      204800   83  Linux
/dev/sda4            7675       15234    60719104   8e  Linux LVM
/dev/sda5           29652       30401     6024343+  82  Linux swap / Solaris
/dev/sda6           15234       29060   111055872   83  Linux
/dev/sda7           29060       29651     4749312   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Based upon mounting the devices and looking at the contents, I believe SDA1 to be my Ubuntu Desktop, SDA2 to be a partition containing only sub-partitions (why?), SDA3 to be where grub information was installed (look at the contents below), SDA4 I have no clue, SDA5 is swap, SDA6 is my Lucid installation, and SDA7 is more swap. I also noted that the major number is 8, although I do not know what that means...


This is the result of running ls in the SDA3 partition:
```
config-2.6.31.5-127.fc12.x86_64
config-2.6.32.10-90.fc12.x86_64
efi
elf-memtest86+-4.00
grub
initramfs-2.6.31.5-127.fc12.x86_64.img
initramfs-2.6.32.10-90.fc12.x86_64.img
initrd-2.6.31.5-127.fc12.x86_64kdump.img
lost+found
memtest86+-4.00
System.map-2.6.31.5-127.fc12.x86_64
System.map-2.6.32.10-90.fc12.x86_64
vmlinuz-2.6.31.5-127.fc12.x86_64
vmlinuz-2.6.32.10-90.fc12.x86_64
```



My /boot/grub/grub.cfg in 9.10 looks like:
```
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
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

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash
	initrd /boot/initrd.img-2.6.32-18-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro single
	initrd /boot/initrd.img-2.6.32-18-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash
	initrd /boot/initrd.img-2.6.32-16-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro single
	initrd /boot/initrd.img-2.6.32-16-generic-pae
}
menuentry "Chainload into GRUB 2 (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/grub/core.img 
}
menuentry "Ubuntu lucid (development branch), memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora 2.6.32 on SDA6" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/FED/vmlinuz-2.6.32.10-90.fc12.x86_64 root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet
	initrd /boot/FED/initramfs-2.6.32.10-90.fc12.x86_64.img
}
### END /etc/grub.d/40_custom ###
```


The last entry I added in an attempt to boot up Fedora. I edited it using the /etc/grub.d/40_custom file and have grub be reconfigured. (I tried it on various partitions, but it always failed. More on that later)

Running "ls -la /dev/disk/by-uuid" returns:
```
total 0
drwxr-xr-x 2 root root 180 2010-04-04 15:46 .
drwxr-xr-x 6 root root 120 2010-04-04 15:46 ..
lrwxrwxrwx 1 root root  34 2010-04-04 15:46 0d8311f9-06ae-413f-8774-67dd08a3377f -> ../../mapper/vg_jackserver-lv_root
lrwxrwxrwx 1 root root  10 2010-04-04 15:45 29212f89-2ed8-49e6-bb5b-8212a6609729 -> ../../sda6
lrwxrwxrwx 1 root root  34 2010-04-04 15:46 7ef9a669-8de4-4b69-84ed-b853885b62f0 -> ../../mapper/vg_jackserver-lv_swap
lrwxrwxrwx 1 root root  10 2010-04-04 15:45 8ef226cf-6c87-474f-93db-eda0aac11205 -> ../../sda7
lrwxrwxrwx 1 root root  10 2010-04-04 15:45 a74245c7-d450-4399-85bd-3ba3273ef054 -> ../../sda5
lrwxrwxrwx 1 root root  10 2010-04-04 15:45 c7910854-7167-4f03-b1f3-6b1108dbf8ef -> ../../sda3
lrwxrwxrwx 1 root root  10 2010-04-04 15:45 d83e50bd-d724-4a1c-9b2f-df9033796201 -> ../../sda1
```

One thing I managed to find was a copy of GRUB that Fedora installed on a separate partition that I mounted. It was located at /Fedora-12-x86_64/boot/grub/grub.conf (menu.lst links there):
```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_jackserver-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.32.10-90.fc12.x86_64)
	root (hd0,2)
	kernel /vmlinuz-2.6.32.10-90.fc12.x86_64 ro root=/dev/mapper/vg_jackserver-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.32.10-90.fc12.x86_64.img
title Fedora (2.6.31.5-127.fc12.x86_64)
	root (hd0,2)
	kernel /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_jackserver-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
```



I thank you VERY VERY MUCH for your replies. If you think other information would be helpful, I can get it and post it.

Thank you very much,
~Jack

---

### Post by oldfred on 2010-04-04
To reinstall the Ubuntu boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

While you have posted a lot of the info this script will output it also check for boot loader in the MBR and PBRs, UUIDs and boot files in partition. I recommend any user with multiple installs use this before and after any changes and check that everything installed where you expected.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by basketballler77 on 2010-04-04
I followed the instructions on restoring the bootloader. Unfortunately, the other options still do not function. I'm going to attempt doing the same thing using my 10.4 cd, and see what happens. Here is the content of RESULTS.TXT (Sorry for not using code tags earlier; I'll edit it right now):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000d645

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   122,880,062   122,880,000  83 Linux
/dev/sda2         244,729,854   488,392,064   243,662,211   5 Extended
/dev/sda5         476,343,378   488,392,064    12,048,687  82 Linux swap / Solaris
/dev/sda6         244,729,856   466,841,599   222,111,744  83 Linux
/dev/sda7         466,843,648   476,342,271     9,498,624  82 Linux swap / Solaris
/dev/sda3    *    122,880,063   123,289,662       409,600  83 Linux
/dev/sda4         123,289,663   244,727,870   121,438,208  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d83e50bd-d724-4a1c-9b2f-df9033796201   ext4                                     
/dev/sda3        c7910854-7167-4f03-b1f3-6b1108dbf8ef   ext4                                     
/dev/sda4        jifjL7-WE4W-H7HA-Ex7S-Dbp8-Jiri-X8Vbfx LVM2_member                               
/dev/sda5        a74245c7-d450-4399-85bd-3ba3273ef054   swap                                     
/dev/sda6        29212f89-2ed8-49e6-bb5b-8212a6609729   ext4                                     
/dev/sda7        8ef226cf-6c87-474f-93db-eda0aac11205   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d83e50bd-d724-4a1c-9b2f-df9033796201

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

title		Ubuntu 9.10, kernel 2.6.31-20-server
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-server

title		Ubuntu 9.10, kernel 2.6.31-20-server (recovery mode)
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro  single
initrd		/boot/initrd.img-2.6.31-20-server

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		d83e50bd-d724-4a1c-9b2f-df9033796201
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-server root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
	initrd	/boot/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single 
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

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash
	initrd /boot/initrd.img-2.6.32-18-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro single
	initrd /boot/initrd.img-2.6.32-18-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash
	initrd /boot/initrd.img-2.6.32-16-generic-pae
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro single
	initrd /boot/initrd.img-2.6.32-16-generic-pae
}
menuentry "Chainload into GRUB 2 (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/grub/core.img 
}
menuentry "Ubuntu lucid (development branch), memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora 2.6.32 on SDA6" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux /boot/FED/vmlinuz-2.6.32.10-90.fc12.x86_64 root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet
	initrd /boot/FED/initramfs-2.6.32.10-90.fc12.x86_64.img
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a74245c7-d450-4399-85bd-3ba3273ef054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.4GB: boot/grub/core.img
   6.1GB: boot/grub/grub.cfg
  23.0GB: boot/grub/menu.lst
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.6GB: boot/initrd.img-2.6.31-20-generic
   7.6GB: boot/initrd.img-2.6.31-20-server
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.4GB: boot/vmlinuz-2.6.31-20-generic
   4.1GB: boot/vmlinuz-2.6.31-20-server
   7.6GB: initrd.img
   1.6GB: initrd.img.old
   4.1GB: vmlinuz
   1.4GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29212f89-2ed8-49e6-bb5b-8212a6609729

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

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae
uuid		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-18-generic-pae

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (recovery mode)
uuid		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/vmlinuz-2.6.32-18-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro  single
initrd		/boot/initrd.img-2.6.32-18-generic-pae

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae
uuid		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-16-generic-pae

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (recovery mode)
uuid		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro  single
initrd		/boot/initrd.img-2.6.32-16-generic-pae

title		Chainload into GRUB 2
root		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/grub/core.img

title		Ubuntu lucid (development branch), memtest86+
uuid		29212f89-2ed8-49e6-bb5b-8212a6609729
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,6)'
search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
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
set root='(/dev/sda,6)'
search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(/dev/sda,6)'
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux	/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(/dev/sda,6)'
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	echo	Loading Linux 2.6.32-16-generic-pae ...
	linux	/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(/dev/sda,6)'
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(/dev/sda,6)'
	search --no-floppy --fs-uuid --set 29212f89-2ed8-49e6-bb5b-8212a6609729
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda1)" {
	insmod ext2
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
	insmod ext2
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set d83e50bd-d724-4a1c-9b2f-df9033796201
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d83e50bd-d724-4a1c-9b2f-df9033796201 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=29212f89-2ed8-49e6-bb5b-8212a6609729 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8ef226cf-6c87-474f-93db-eda0aac11205 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 151.3GB: boot/grub/core.img
 228.5GB: boot/grub/grub.cfg
 151.3GB: boot/grub/menu.lst
 151.4GB: boot/initrd.img-2.6.32-16-generic-pae
 151.5GB: boot/initrd.img-2.6.32-18-generic-pae
 151.2GB: boot/vmlinuz-2.6.32-16-generic-pae
 151.4GB: boot/vmlinuz-2.6.32-18-generic-pae
 151.5GB: initrd.img
 151.5GB: initrd.img.old
 151.4GB: vmlinuz
 151.4GB: vmlinuz.old

============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_jackserver-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.32.10-90.fc12.x86_64)
	root (hd0,2)
	kernel /vmlinuz-2.6.32.10-90.fc12.x86_64 ro root=/dev/mapper/vg_jackserver-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.32.10-90.fc12.x86_64.img
title Fedora (2.6.31.5-127.fc12.x86_64)
	root (hd0,2)
	kernel /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_jackserver-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.31.5-127.fc12.x86_64.img

=================== sda3: Location of files loaded by Grub: ===================


  62.9GB: grub/grub.conf
  62.9GB: grub/menu.lst
  62.9GB: grub/stage2
  62.9GB: initramfs-2.6.31.5-127.fc12.x86_64.img
  62.9GB: initramfs-2.6.32.10-90.fc12.x86_64.img
  62.9GB: initrd-2.6.31.5-127.fc12.x86_64kdump.img
  62.9GB: vmlinuz-2.6.31.5-127.fc12.x86_64
  62.9GB: vmlinuz-2.6.32.10-90.fc12.x86_64

```

---

### Post by oldfred on 2010-04-04
I do not see your 9.04, but just 9.10 and lucid.  Are you able to boot either? I have seen where having menu.lst and grub.cfg means both grub legacy and grub2 still exist and create conflicts. It is usually best to totally unstall both grub legacy and grub2 and reinstall grub2.

If you cannot boot then you will have to chroot into your system from a liveCD or another install that boots and update it.

Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#purge old and reinstall new to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by basketballler77 on 2010-04-04
Unfortunately, that did not work either. I did notice that Lucid says "Mountall failed: Could not find Plymouth" before hanging at fsck. It is only visible for a fraction of a second, but perhaps that is why it fails.

---

### Post by oldfred on 2010-04-04
If you want help with Lucid I would suggest the Lucid forum, it is still beta and has some issues. I have seen some postings discussing plymouth. I had initial trouble getting it to boot because of video issues but it has worked ok since.

Can you boot 9.10 and does sudo update-grub find fedora?

---

### Post by basketballler77 on 2010-04-04
I will definitely check over there next. 9.10 is still successfully booting, but the sudo update-grub does not find Fedora. I will look into the Plymouth issue, and if that does not lead anywhere, I will next be attempting to figure out how Grub determines if an OS is installed, to see if perhaps adding a configuration file on one of the partitions would solve the problem

~Jack

---

### Post by oldfred on 2010-04-04
I do not know fedora but I did copy these as solutions to boot issues, It looks like the newer grub2 - 1.98 that is with Lucid may be better than the 1.97 beta:

Fix for Fedora:
sudo apt-get install --reinstall libdebian-installer4

See Kansasnoob comments 40 & 42 Install grub 1.98  & to fix major grub issues
here was a BIOS option setting in the boot loader device selection in the Fedora installer. Comment #44
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

[http://ubuntuforums.org/showthread.php?t=1367305](http://ubuntuforums.org/showthread.php?t=1367305)
If the linux has no bootloader, the os-prober will look for the kernel file name that starts with vmlinu[zx] and the initrd file name that starts with initrd.
In my case, I have installed fedora without bootloader and the initrd file name starts with initramfs. I have made a simple change to the os-prober by make it looking for the file starts with initr instead of initrd.

---

### Post by basketballler77 on 2010-04-05
Again, I have had no luck. I thank you very much for your help with my problem, but the more time I spend thinking about it, the more sure I am that Fedora decided to install itself on the same partition as where Lucid was located. I believe I will attempt to erase all of the partitions other than my 9.10 partition and be more explicit with my partitioning in the future. I guess I'll reinstall the other two later.

Thanks again,
~Jack

---

