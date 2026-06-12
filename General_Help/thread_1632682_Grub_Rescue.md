---
title: "Grub Rescue"
date: 2010-11-28
forum: General Help
---

### Post by pages on 2010-11-28
I have recently updated my Ubuntu software and was asked about the grub options , admittedly i was unsure of what its purpose was but the help of the software update seemed to indicate that grub would be beneficial to my system.

On the next page of the install it asked me select from a list of 2 options and again not really knowing which to select i looked and the help section seemed to indicate to select all the drives so i did and continued with the restart.

Now when i boot up my PC i see the DELL BIOS load up but straight away i go into a Grub Rescue console saying 
Error no such device  -- (some really long hex address)
Grub resuce>

Now i really have no clue what to do , most guides suggest a clean install of both operating systems but i am really trying to avoid that in case some of my thesis work is deleted ( yeah i know back up in multiple locations :( )

if anyone has any information which can help me to get back to as things were before i would really appreciate it

---

### Post by Rubi1200 on 2010-11-28
Hi and welcome to the forums :)

Why did you mark this Solved if you have a problem?

You need to boot the computer with a LiveCD and choose to try Ubuntu.

Click on the link at the bottom of my post and follow the instructions to run the boot info script.

Post the results back here and we will try and get things up and running again for you.

Thanks.

---

### Post by pages on 2010-11-28
Hi sorry marked the thread as resolved cause couldn't find the delete since i found a similar thread just in a different sub forum ..

But since you're hear i'm still having problems , i have downloaded the Ubuntu and using the tool put  the ISO  on a completely blank USB key . Putting that into my computer and choosing from the Boot menu 
* USB/ZIP
I select that and get the same problems of it entering Grub rescue


think i'm up **** creek without a paddle :(

---

### Post by sikander3786 on 2010-11-28
Hi.

> But since you're hear i'm still having problems , i have downloaded the Ubuntu and using the tool put the ISO on a completely blank USB key . Putting that into my computer and choosing from the Boot menu
* USB/ZIP
I select that and get the same problems of it entering Grub rescue

I hope you used the proper tool to burn the USB drive. Which one did you use?

And your USB might show up under the HDD list in your Bios Menu. Bring it to the top of list there ;-)

---

### Post by pages on 2010-11-28
> **sikander3786 said:**
> Hi.



I hope you used the proper tool to burn the USB drive. Which one did you use?

And your USB might show up under the HDD list in your Bios Menu. Bring it to the top of list there ;-)

I'll try look under hard drive now but while im checking the tool i used for the the ISO conversion was
Universal-USB-Installer-1.8.1.5.exe
it was the one in the 'show me how' part of downloading Ubuntu .. And i know its working since im even able to try a demo of Ubuntu from this laptop

---

### Post by sikander3786 on 2010-11-28
> And i know its working since im even able to try a demo of Ubuntu from this laptopp

Then where is the problem? You can use the same demo session to install Ubuntu.

Do you mean that you've already installed Ubuntu to your HDD and you are unable to boot that install? Or what :confused:

---

### Post by pages on 2010-11-28
Emm the problem lies on my desktop computer with has vista and Ubuntu dual booting on it, im currently working off a laptop with just XP running on it.

The desktop computer cannot get past the BIOS screen without failing to boot from its normal sequence of where to boot so it straight away goes into the 
Error no such device -- (some really long hex address)
Grub rescue > 
I've also  tried booting from a seperate instance of Ubuntu via the USB key but when i try to boot from that i still go into the same grub rescue error


thanks for trying to help btw , its really appreciated

---

### Post by sikander3786 on 2010-11-28
Ok, I get your situation now :P

So what OS is installed on that desktop previously?

And did you check under the HDD menu in Bios as I mentioned earlier?

---

### Post by pages on 2010-11-28
On the desktop i had Vista and Ubuntu 10.04(64 bit) i believe 

And yeah checked the HDD , the USB didnt appear there but just in case it was named differently than what i would have expected to be seeing , i tried booting from each option ... but to no avail as this Grep rescue came 

fun fun fun :) but any new ideas ?

---

### Post by sikander3786 on 2010-11-28
> On the desktop i had Vista and Ubuntu 10.04(64 bit) i believe 

And those OS are no longer there but Grub is still in the MBR thats why it shows the Grub Rescue prompt I believe.

And that means that Bios is not trying to/not able to boot from the USB drive. Why, I don't know. Are you sure that machine is capable of booting the USB? Have you ever done that before?

Please list your motherboard so we can take a look at the manual for you :-)

Or if you've got a CD/DVD drive, try boot from a CD...

---

### Post by robn30 on 2010-11-28
I have had the same issue a few times now.  Use Unetbootin, point it to the .iso you downloaded, and it will create a bootable USB.  I have also found that the USB must be formatted FAT32 for it to work.  Once you get it booted off the USB just reinstall Ubuntu the same way you did it originally and that will get your boot up back in order.  When done it will provide you the ability to choose your Vista boot or Ubuntu.

---

### Post by pages on 2010-11-28
Just to update it might be able to help others ...

On your advice i put the ISO on a CD and was planning to runthe 'Demo' on Ubuntu to find the boot files for you but ran into some complications.
When i clicked the 'try out Ubuntu' everyone would disappear except the background page and it would stay like this for 20 minutes or so which was annoying.
Then i tried to just install Ubuntu again which was fine up until it completed and required a restart when errors appeared when trying to shut down . In frustration i just turned off the computer and started it again hoping it had worked .
When the computer was restarting the boot menu appeared and it now seems that I have 2 versions of Ubuntu 10.04 on my PC and 1 version of Windows Vista 

Not sure how im going to delete the spare version of Ubuntu but at least i have access to my files now

---

### Post by sikander3786 on 2010-11-28
> I have 2 versions of Ubuntu 10.04 on my PC and 1 version of Windows Vista 

There might be 2 entries for Ubuntu. 1 for the Normal Kernel and 2nd for the Recovery Mode. If Recovery is listed at the end of 2nd line, believe me, you only have one version of Ubuntu installed :P

---

### Post by robn30 on 2010-11-28
> **pages said:**
> Just to update it might be able to help others ...

On your advice i put the ISO on a CD and was planning to runthe 'Demo' on Ubuntu to find the boot files for you but ran into some complications.
When i clicked the 'try out Ubuntu' everyone would disappear except the background page and it would stay like this for 20 minutes or so which was annoying.
Then i tried to just install Ubuntu again which was fine up until it completed and required a restart when errors appeared when trying to shut down . In frustration i just turned off the computer and started it again hoping it had worked .
When the computer was restarting the boot menu appeared and it now seems that I have 2 versions of Ubuntu 10.04 on my PC and 1 version of Windows Vista 

Not sure how im going to delete the spare version of Ubuntu but at least i have access to my files now

Yeah mine does the same after install, but there appears to be no problem.  As the other poster stated make sure the other line you see is not the recovery mode.  If it is not I would get whatever stuff you have off the Linux partition, then reboot into Vista and delete the Linux partition using Disk Management, which will create free space, lastly reboot with CD you made and reinstall Ubuntu.  After that you should be good.

---

### Post by drs305 on 2010-11-28
If you can now boot to a normal installation and still need help with determining what you have on your system just run the boot info script from the following site and post the contents of the RESULTS.txt file it generates. It will show us what you now have on your system regarding boot files and menu items.
[_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net")

---

### Post by pages on 2010-11-30
> **drs305 said:**
> If you can now boot to a normal installation and still need help with determining what you have on your system just run the boot info script from the following site and post the contents of the RESULTS.txt file it generates. It will show us what you now have on your system regarding boot files and menu items.
[_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net")

gonna put this in code tags so hopefully it doesn't make the  post be stupidly long !
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3          21,084,160   488,278,015   467,193,856   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   259,355,430   259,353,383   7 HPFS/NTFS
/dev/sdb2         259,356,670   488,280,063   228,923,394   5 Extended
/dev/sdb5         259,356,672   478,889,983   219,533,312  83 Linux
/dev/sdb6         478,892,032   488,280,063     9,388,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       b38aa7ba-97e6-47c7-b6b9-c7c325c7f726   ext4                                     
/dev/sda1        07D7-0603                              vfat       DellUtility                   
/dev/sda2        C4BEB402BEB3EAD6                       ntfs       RECOVERY                      
/dev/sda3        3A6CB9CA6CB98165                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E2C8C10FC8C0E341                       ntfs       DATAPART1                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d50ec377-9e14-4683-9cb5-2106a5cecbef   ext4                                     
/dev/sdb6        912e1c86-c278-4621-a50b-6d8887b2d1f5   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e2c8c10fc8c0e341
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0603
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3a6cb9ca6cb98165
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


  10.9GB: boot/grub/core.img
   4.7GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.32-24-generic
   2.9GB: boot/initrd.img-2.6.32-25-generic
   2.8GB: boot/initrd.img-2.6.32-26-generic
   1.1GB: boot/vmlinuz-2.6.32-24-generic
  10.9GB: boot/vmlinuz-2.6.32-25-generic
  11.1GB: boot/vmlinuz-2.6.32-26-generic
   2.8GB: initrd.img
   2.9GB: initrd.img.old
  11.1GB: vmlinuz
  10.9GB: vmlinuz.old

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=d50ec377-9e14-4683-9cb5-2106a5cecbef ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=d50ec377-9e14-4683-9cb5-2106a5cecbef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d50ec377-9e14-4683-9cb5-2106a5cecbef ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d50ec377-9e14-4683-9cb5-2106a5cecbef ro single 
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d50ec377-9e14-4683-9cb5-2106a5cecbef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0603
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3a6cb9ca6cb98165
	drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf5 during installation
UUID=d50ec377-9e14-4683-9cb5-2106a5cecbef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf6 during installation
UUID=912e1c86-c278-4621-a50b-6d8887b2d1f5 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 240.3GB: boot/grub/core.img
 216.8GB: boot/grub/grub.cfg
 134.3GB: boot/initrd.img-2.6.35-22-generic
 134.6GB: boot/initrd.img-2.6.35-23-generic
 240.4GB: boot/vmlinuz-2.6.35-22-generic
 240.4GB: boot/vmlinuz-2.6.35-23-generic
 134.6GB: initrd.img
 134.3GB: initrd.img.old
 240.4GB: vmlinuz
 240.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```


So is the prognosis good or bad ? :)

---

### Post by drs305 on 2010-11-30
> **pages said:**
> When the computer was restarting the boot menu appeared and it now seems that I have 2 versions of Ubuntu 10.04 on my PC and 1 version of Windows Vista 

Not sure how im going to delete the spare version of Ubuntu but at least i have access to my files now

> So is the prognosis good or bad ?

What are you trying to use - Wubi within Windows or an independent Ubuntu installation on it's own partition?

If you are using an independent Ubuntu, did you want to keep the Wubi install?

And finally, what are you currently able to use? Windows, Ubuntu, Ubuntu Wubi? All, two, etc?

The RESULTS.txt is a bit ambivalent. It appears you booted into a normal Ubuntu installation on sdb5. If you are booting to Ubuntu, use the following command to confirm /  is on sdb5:
```
mount | grep "/ " 
```
Next run this, using the result from the previous command (it should be sdb, but change it if it's sda):```

sudo grub-install /dev/sd**b**
sudo update-grub
```

To remove older kernels (and also remove them from the menu), I'd recommend you use Ubuntu Tweak. Here is a link to a guide I wrote about removing older kernels. It's probably best to keep at least one older kernel as a backup.
[_HOWTO: Remove Older Kernels via GUI_]("http://ubuntuforums.org/showthread.php?t=1587462")

You can hide the recovery menuentries if you wish, although you may want to keep that option displayed. If you don't, go to /etc/default/grub and uncomment the #GRUB_DISABLE_LINUX_RECOVERY="true line. (gksu gedit /etc/default/grub).

After reading this and doing the parts of it you wish, let us know what you still need accomplished.

---

