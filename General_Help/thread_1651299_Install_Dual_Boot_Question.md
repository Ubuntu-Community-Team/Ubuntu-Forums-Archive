---
title: "Install Dual Boot Question"
date: 2010-12-22
forum: General Help
---

### Post by jwaclawsky on 2010-12-22
Installed Ubuntu 10.10 on my Dell Vostro 1015. Worked fine and running well. But I couldn't leave well enough alone and wanted to dual boot with windows 7. So next I resized the existing partition using the Ubuntu live disk to partition the drive and free space of 90 GB for installing windows (I have 61 GB partition for Ubuntu). I installed windows 7 in the 90GB partition and it boots up and runs fine. Now I am trying to get dual boot running following the instructions at:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I am getting an error that I can get past when I execute the command: 
sudo grub-install --root-directory=/media/a1b90625-8f23-42de-a136-41e3097c8f6d /dev/sda1  I am sure it is a "user issue"  :-)  so can someone tell me what I am doing wrong. The message is:
"warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.." Please see screen shot attachment of the terminal commands and messages executed in the exact sequence as suggested in the instructions at: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) The output from the first command (mount | tail -1) tells me the partition is correct and mounted. I believe that is correct??? The output of the second command (ls /media/a1b90625-8f23-42de-a136-41e3097c8f6d/boot) tells me this is a boot partition (is that correct?)  The third command I described above is where I get stuck. Any assistance is greatly appreciated.

---

### Post by garvinrick4 on 2010-12-22
IN live Cd. I am using sda1 for this example (you use your own) where linux is installed.
such as sda1 or sda2 or sda5 just use your own.
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```go into ubuntu on HD and
```
sudo update-grub
```### If you have a  independent boot partition it is a different set of instructions!!!!
sudo fdisk -l 
Lower case L
will give sda#'s

---

### Post by Quackers on 2010-12-22
If you are trying to install grub to the mbr of the hard drive that should be sda - not sda1.
Unless you have a separate /boot partition, maybe.

---

### Post by jwaclawsky on 2010-12-23
To the two responses: I am not sure what is meant by an "independent boot partition" or a "separate boot partition"???  How can I tell?  

Note: I don't want anything fancy and I want just one MBR that allows me to boot either windows7 or Ubuntu 10.10. I installed Ubuntu first, then windows. But now when I boot up I don't get a choice and can only boot windows. Ubuntu is there in a partition on the hard drive.  Are you telling me that all I need to do is change the command from my previous post. 

Change the command FROM:

"sudo grub-install --root-directory=/media/a1b90625-8f23-42de-a136-41e3097c8f6d /dev/sda1"  

TO:

"sudo grub-install --root-directory=/media/a1b90625-8f23-42de-a136-41e3097c8f6d /dev/sda" 

Is that correct?

---

### Post by Quackers on 2010-12-23
I would try that first (if I were using the UUID).
See if that works first.

---

### Post by wilee-nilee on 2010-12-23
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

This script will give us more information.

---

### Post by garvinrick4 on 2010-12-23
Yes what quackers said is right you always put grub in sda never sda1 or sda5 always to sda
If you want to run 
```
sudo fdisk -l
``` (small L)
and post it we can make sure what you got going anyway.
#wilee-nilees bootscript is the purest form of seeing what is going on in your drive.

---

### Post by jwaclawsky on 2010-12-23
Ok thanks, I will do the command with sda (NOT sda1) and see what results.

---

### Post by jwaclawsky on 2010-12-23
I did the command: 

"sudo grub-install --root-directory=/media/a1b90625-8f23-42de-a136-41e3097c8f6d /dev/sda" 

The command finished with no errors. When I booted, it appears Grub did not load, but the system now comes up successfully in Ubuntu instead of windows. I tried rebooting again and used F12 on start up to see if there was a boot selection but again no OS selection possibilities. When I selected the hard disk (from bios) to boot from it came up in Ubuntu (no windows choices available). Now I can't find or boot from my windows partition on start up. I guess dual boot is not working unless there is a special command to use on boot-up to get to a dual boot menu of some type to run???  

I ran the command sudo fdisk -l and a screen shot of the output is attached. Notice the output shows Linux as sda1 and windows is supposed to be in sda3. That is the partition that was loaded when I previously booted before I did the "sudo grub-install...." command. 

I also downloaded and ran the boot info script from: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/). 
That output is shown below, and it sees an ubuntu 10.10 partition and a windows 7 partition. So everything appears to be there and I just need to get dual boot going? Thanks again for everyone's assistance:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   118,650,485   118,648,438  83 Linux
/dev/sda2    *    118,650,880   118,855,679       204,800   7 HPFS/NTFS
/dev/sda3         118,855,680   300,292,095   181,436,416   7 HPFS/NTFS
/dev/sda4         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a1b90625-8f23-42de-a136-41e3097c8f6d   ext4                                     
/dev/sda2        5014698914697340                       ntfs       System Reserved               
/dev/sda3        8C4A6C924A6C7B3A                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8ff2d9e8-ef4b-4d9d-8f86-40333e0957da   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/8C4A6C924A6C7B3A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a1b90625-8f23-42de-a136-41e3097c8f6d ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a1b90625-8f23-42de-a136-41e3097c8f6d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=8ff2d9e8-ef4b-4d9d-8f86-40333e0957da none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/core.img
   3.2GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-23-generic
   1.0GB: boot/initrd.img-2.6.35-24-generic
    .6GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: boot/vmlinuz-2.6.35-23-generic
    .6GB: boot/vmlinuz-2.6.35-24-generic
   1.0GB: initrd.img
    .8GB: initrd.img.old
    .6GB: vmlinuz
    .6GB: vmlinuz.old

---

### Post by jwaclawsky on 2010-12-23
I am sorry for my long prior post but it is mostly the output of the boot info script.It seems the information from the boot info script and the screen shot of the sudo fdisk -l output show both Ubuntu 10.10 and windows 7 on my hard drive. So everything appears to be there and I just need to get dual boot going? I must be missing something simple? Thanks for any advice?

...BTW, I can't find a menu list file for Grub ...but then again I am at the edge of my knowledge of this.

---

### Post by garvinrick4 on 2010-12-23
#You have a boot partition in sda2 and that is where your boot flag is. Notice
the small partition in sda2 must be mounted when installing grub. (Usually in sda1 boot partition and sda2 Windows install.)
#Oh that is right you installed Windows 7 after Ubuntu, most of time computers come with windows and users put Ubuntu as 2nd install.
##In live cd open terminal:
```

[CODE]sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda2 /media/boot
``````
sudo mount /dev/sda1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
``````
sudo umount /media/boot
```[/code]Now reboot and you should be looking good. Go into Ubuntu on HDD and 
```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-12-23
> **jwaclawsky said:**
> I am sorry for my long prior post but it is mostly the output of the boot info script.It seems the information from the boot info script and the screen shot of the sudo fdisk -l output show both Ubuntu 10.10 and windows 7 on my hard drive. So everything appears to be there and I just need to get dual boot going? I must be missing something simple? Thanks for any advice?

...BTW, I can't find a menu list file for Grub ...but then again I am at the edge of my knowledge of this.
If you highlight the whole thing and hit the little # in upper right hand corner it will put
in nice little box. Called code tags.

---

### Post by wilee-nilee on 2010-12-23
OP you have grub2 menu.list is grub legacy.

---

### Post by jwaclawsky on 2010-12-23
garvinrick4 - that did it! I can now boot windows 7 or Ubuntu 10.10. Problem solved!  :D   Many Many Thanks to everyone for walking me through this and all the excellent information and insight. I learned a lot too. Warm Regards to you all.

BTW, anyone know how to mark this thread solved?

---

### Post by garvinrick4 on 2010-12-24
You will find a lot of nice users in these forums and is a good place to learn no matter what skill level, see ya around. Have a Merry Chistmas and a Happy New Year.

---

