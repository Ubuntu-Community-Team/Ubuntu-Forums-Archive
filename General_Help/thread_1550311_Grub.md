---
title: "Grub"
date: 2010-08-10
forum: General Help
---

### Post by Bobscrachy on 2010-08-10
I'm trying to find out which hard drive my vista installation is labeled in ubuntu so I can finish editing the grub menu.1st file. 

All it says on the sourceforge page is 
[URL="http://www.howtoforge.com/working_with_the_grub_menu"]
> Root - You likely have something along these lines "(hd0,1)". "hd0" refers to the your hard drive while 1 points to the partition. Note that for GRUB, partitions start at 0 and not 1. for example 0=Partition 1, 1=Partition 2 and so on.[/URL]

It doesn't say how I can find out which one my vista is. So I need to know what my hard drive is in linux. Is it hd0,1 or hd0 or what?

---

### Post by Ozymandias_117 on 2010-08-10
> **Bobscrachy said:**
> I'm trying to find out which hard drive my vista installation is labeled in ubuntu so I can finish editing the grub menu.1st file. 

All it says on the sourceforge page is 
[URL="http://www.howtoforge.com/working_with_the_grub_menu"]
[/URL]

It doesn't say how I can find out which one my vista is. So I need to know what my hard drive is in linux. Is it hd0,1 or hd0 or what?

Use the command ```
sudo fdisk -l
``` If you aren't sure how to read it, post it here (In code brackets please).

Note: If you are using GRUB 2, you can just use ```
sudo update-grub
``` and it should find it.

---

### Post by Bobscrachy on 2010-08-10
Here it is. One of the 80s is the ubuntu drive, the other is the vista drive. The 1.5t is a media drive. 

```
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x289ff029

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465136128    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd85165b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78149517    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001956f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9328    74920960   83  Linux
/dev/sdc2            9328        9730     3227649    5  Extended
/dev/sdc5            9328        9730     3227648   82  Linux swap / Solaris
```

---

### Post by Ozymandias_117 on 2010-08-10
Then your Linux partiton (As far as GRUB is concerned) should be (hd3,0)

---

### Post by Bobscrachy on 2010-08-11
Ok, here the deal. Before I installed ubuntu I unplugged my vista hard drive and my two data drives. Ubuntu is now installed and I plugged the other hard drives back up. But, the grub that came with ubuntu doesn't recognize my vista drive. So, at the moment I'm stuck having to change the boot priority in the bios to shift between installations. How do I add the vista installation to the grub menu?

I've been fiddling with this all day trying to get it to work. When i originally went into the terminal it told me grub wasn't installed and asked me to install it. So i did, but i get the feeling that is not the grub that i need to edit.

---

### Post by Bobscrachy on 2010-08-11
*bump*

---

### Post by john newbuntu on 2010-08-11
Booting from your Ubuntu drive, did you run "sudo update-grub" as ozymandias suggested?  That should have picked up Vista.

Now if that does not work, read on...
You mentioned that you have installed grub.  Now the question is what version of grub got installed.  To get this info and more, go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instructions on this page to download and run the boot_info_script.  Post the output using code tags.

Edit: Your root value for grub legacy will be (hd2,0)

---

### Post by Ozymandias_117 on 2010-08-11
> **john newbuntu said:**
> Booting from your Ubuntu drive, did you run "sudo update-grub" as ozymandias suggested?  That should have picked up Vista.

Now if that does not work, read on...
You mentioned that you have installed grub.  Now the question is what version of grub got installed.  To get this info and more, go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instructions on this page to download and run the boot_info_script.  Post the output using code tags.

Edit: Your root value for grub legacy will be (hd2,0)

Thanks, I was half asleep :D 3-1 != 3 >.> :)

---

### Post by elliotn on 2010-08-11
Have da same problem

---

### Post by Bobscrachy on 2010-08-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,299,096   156,299,034   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        828facad-e0f1-43a9-ae68-e1ecb9957f29   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        33b518ee-d1b4-4808-b5fd-1645e35baa28   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3AE0519BE0515DE7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2294AFF994AFCD9B                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3AE0519BE0515DE7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3AE0519BE0515DE7

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		3AE0519BE0515DE7
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=3AE0519BE0515DE7 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		3AE0519BE0515DE7
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=3AE0519BE0515DE7 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		3AE0519BE0515DE7
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=3AE0519BE0515DE7 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		3AE0519BE0515DE7
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=3AE0519BE0515DE7 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title        Microsoft Windows Vista
root        (hd1,0)
makeactive
chainloader    +1

title		Chainload into GRUB 2
root		3AE0519BE0515DE7
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		3AE0519BE0515DE7
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
search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
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
search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
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
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=828facad-e0f1-43a9-ae68-e1ecb9957f29 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=828facad-e0f1-43a9-ae68-e1ecb9957f29 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=828facad-e0f1-43a9-ae68-e1ecb9957f29 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=828facad-e0f1-43a9-ae68-e1ecb9957f29 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 828facad-e0f1-43a9-ae68-e1ecb9957f29
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 3ae0519be0515de7
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33b518ee-d1b4-4808-b5fd-1645e35baa28 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  34.7GB: boot/grub/core.img
  64.9GB: boot/grub/grub.cfg
  64.9GB: boot/grub/menu.lst
  35.0GB: boot/initrd.img-2.6.32-21-generic
  35.7GB: boot/initrd.img-2.6.32-24-generic
  35.5GB: boot/vmlinuz-2.6.32-21-generic
  35.0GB: boot/vmlinuz-2.6.32-24-generic
  35.7GB: initrd.img
  35.0GB: initrd.img.old
  35.0GB: vmlinuz
  35.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-08-11
You have grub2 in the MBR booting sda1. The grub.cfg shows a Vista boot stanza. Does that boot work?

Was your Vista the first drive or the second drive when it was installed? It makes a difference. If it was first you may have to edit with bcdedit so it knows it is the second drive. You may also have to reupdate grub as it does not have the common drivemap command to map windows from drive 1 to drive 0 as windows likes to be and works best if it is drive 0 or sda.

You should delete grub legacy and the menu.lst as that may confuse grub2.

---

### Post by Bobscrachy on 2010-08-11
The vista option doesn't work. It just goes into ubuntu anyway when I try and use it. 

The linux drive is on an ide drive that was installed on by itself. Then I added the sata drive with an existing vista installation. The 1.5t drive is a media drive that was added with it. 

I uninstalled grub 1, but now its saying that grub isn't on at all. In the Ubuntu software center is saying Grand Unified boot loader, version 2 (common files) is installed. I imagine that's what is working, but in terminal its saying grub isn't installed at all.

---

### Post by Bobscrachy on 2010-08-11
How do i edit grub2 from the terminal?

```
diireno@diireno-desktop:~$ sudo update-grub
sudo: update-grub: command not found
diireno@diireno-desktop:~$ sudo grub2
[sudo] password for diireno: 
sudo: grub2: command not found
diireno@diireno-desktop:~$ sudo grub
sudo: grub: command not found


```

[http://img442.imageshack.us/img442/452/screenshotjtx.png]("http://img442.imageshack.us/img442/452/screenshotjtx.png")

---

### Post by john newbuntu on 2010-08-11
Looks like somehow "grub-pc" got removed.  You need to install that for grub2 to work.

---

### Post by Bobscrachy on 2010-08-11
Ok I installed grub-pc. Now I can update. How do I execute grub at the command line? Is it too much to think I'd be able to do this in two days? I couldn't imagine this being so bloody complicated. 

```
diireno@diireno-desktop:~$ sudo update-grub
[sudo] password for diireno: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done
diireno@diireno-desktop:~$ sudo grub2
sudo: grub2: command not found
diireno@diireno-desktop:~$ grub-pc
grub-pc: command not found
diireno@diireno-desktop:~$ sudo qemu
sudo: qemu: command not found
diireno@diireno-desktop:~$ sudo grub
sudo: grub: command not found
diireno@diireno-desktop:~$ sudo grub.cfg
sudo: grub.cfg: command not found
diireno@diireno-desktop:~$ 


```

---

### Post by oldfred on 2010-08-11
Does your Vista boot?

You do not execute grub from a command line, but can modify settings and add boot stanza's if required. But if Vista is not booting it is more than likely a Vista problem.

When you boot from sdb does Vista boot ok? 

What error message do you get from Vista. Have you removed the grub4dos from your Vista as it can confuse things - /grldr is in the root of your windows partition.

---

### Post by Bobscrachy on 2010-08-11
When I switch hard drive priorities it boots just fine. When I select vista from grub during boot it goes into ubuntu instead.

---

### Post by oldfred on 2010-08-11
Lets try adding a custom entry to 40_custom

menuentry "Windows Vista (loader) (on /dev/sdb1) with map" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3ae0519be0515de7
    drivemap -s (hd0) (hd1)
    chainloader +1
}

I added a line drivemap which grub uses to make windows think it is the first drive.

Copy above stanza into and then update grub :
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

You will have two windows entries the one from the osprober and this new one. See if this works.

---

### Post by Bobscrachy on 2010-08-12
It added another vista option in grub. When I selected the new option grub booted the vista hard drive and 3 seconds later restarted the computer. It acted like it was booting straight into it, but just restarted. When I boot directly to the vista hard drive it goes right into windows.

---

### Post by oldfred on 2010-08-12
I do not have an exact answer but some more examples that have worked in some cases.

Lets edit it & remove the entire search line.
You can do this also from the grub menu. press e for edit and delete the line there as a one time change.
Or you can use the 
gksudo gedit /etc/grub.d/40_custom 
after any changed run this:
sudo update-grub 


menuentry "Windows Vista (loader) (on /dev/sdb1) with map" {
    insmod ntfs
    set root='(hd1,1)'
    [COLOR=Red]search --no-floppy --fs-uuid --set 3ae0519be0515de7[/COLOR]
    drivemap -s (hd0) (hd1)
    chainloader +1
}

And one more edit if you are willing. This will chainload to sdb and try booting. But I think windows still thinks the windows drive is first and this may make it think it is second.

menuentry "windows (from sda) Chainboot sdb MBR" {
set root=(hd1)
chainloader +1
}

You can, with the one time edit in the grub menu modify the menu entry we added to be identical to the one above if you do not want to add it to 40_custom. Just edit the boot lines to match, you can include or delete the drivemap line also.

I have seen others with issues of mixed SATA & PATA drives as the drive order is not consistent between systems.

---

### Post by john newbuntu on 2010-08-12
@oldfred: On a related note, Herman's notes mention that running a "grub-install /dev/sda" would also run the "grub-mkdevicemap" and "grub-probe", which might correct this issue. Has a newer GRUB2 version stopped/started doing this?  Your opinion?
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install")

Edit: the /grldr might also be causing problems.

---

### Post by Bobscrachy on 2010-08-12
Is there a boot file similar to boot.ini I can edit directly? If so what is the command to edit it?


I did both of these edits and restarted after each to no avail. 

> **oldfred said:**
> I do not have an exact answer but some more examples that have worked in some cases.

Lets edit it & remove the entire search line.
You can do this also from the grub menu. press e for edit and delete the line there as a one time change.
Or you can use the 
gksudo gedit /etc/grub.d/40_custom 
after any changed run this:
sudo update-grub 


menuentry "Windows Vista (loader) (on /dev/sdb1) with map" {
    insmod ntfs
    set root='(hd1,1)'
    [COLOR=Red]search --no-floppy --fs-uuid --set 3ae0519be0515de7[/COLOR]
    drivemap -s (hd0) (hd1)
    chainloader +1
}

And one more edit if you are willing. This will chainload to sdb and try booting. But I think windows still thinks the windows drive is first and this may make it think it is second.

menuentry "windows (from sda) Chainboot sdb MBR" {
set root=(hd1)
chainloader +1
}

You can, with the one time edit in the grub menu modify the menu entry we added to be identical to the one above if you do not want to add it to 40_custom. Just edit the boot lines to match, you can include or delete the drivemap line also.

I have seen others with issues of mixed SATA & PATA drives as the drive order is not consistent between systems.

---

### Post by Bobscrachy on 2010-08-12
Problem solved. 

Whoever said it might be on the windows side was right. Evidently uncle grub didn't like me fiddling around with the boot settings of vista. I had diagnostic settings enabled in vista's default operating system settings. Now I can boot up perfectly with the original vista entry in grub's startup. 

The fix
```

Go to the control panel 
--> System 
--> Advanced system settings 
--> Advanced Tab 
--> Default operating system

Make sure this is set to vista and uncheck the two time delay boxes right below. 

```

Thank you all for your help.

---

