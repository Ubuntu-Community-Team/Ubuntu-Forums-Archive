---
title: "Ubuntu doesn't boot anymore"
date: 2010-12-17
forum: General Help
---

### Post by GammaPoint on 2010-12-17
Bah, like I didn't have enough to deal with today :(

I was watching a video on my computer and the computer display started messing up (I think my video card is a bit buggy but I don't think that's the cause of the current problem). Anyway, so I restarted the computer by pressing the power button. Ubuntu booted up normally. However, shortly thereafter the display started looking messed up again (these types of errors usually come in pairs every 3 weeks or so). So I restarted the computer again by pressing the power button.

However, this time instead of booting up into Ubuntu it went to the GRUB boot menu. From there I was given the option to choose Ubuntu to boot up into, but it wouldn't actually accept my "Enter" press in order to boot. So basically I don't know what's going on, it just seems to not be letting me boot into anything.

Anyone have an idea what might be going on? I can get a LIVE CD of Ubuntu from my laptop if need be, but I'm curious as to what might be the problem.

Thanks in advance!

---

### Post by Hippytaff on 2010-12-17
Do you have an Nvidia graphics card?

---

### Post by dabomb1022 on 2010-12-17
try this, sounds like this happened to me. I fixed it though.
[http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub](http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub)

---

### Post by GammaPoint on 2010-12-17
> **Hippytaff said:**
> Do you have an Nvidia graphics card?

Yep, I believe I do.


> **dabomb1022 said:**
> try this, sounds like this happened to me. I fixed it though.
[http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub](http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub)

Hmm, interesting. I'll try this within the hour and see if it fixes the problem. Thanks for the suggestion.

---

### Post by Hippytaff on 2010-12-17
> **dabomb1022 said:**
> try this, sounds like this happened to me. I fixed it though.
[http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub](http://ubuntuhelp.tumblr.com/post/2109035000/how-to-fix-grub)

Cool and helpful and that...but a bit dangerous without knowing more about the situation...if it is a boot thing rather than a graphics driver thing it is best to see the output of the boot script - [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
:-)

---

### Post by GammaPoint on 2010-12-17
> **Hippytaff said:**
> Cool and helpful and that...but a bit dangerous without knowing more about the situation...if it is a boot thing rather than a graphics driver thing it is best to see the output of the boot script - [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
:-)

I see, so I can boot into a LiveCD and run that script I gander? Looks like it. I'll post the results soon. Thanks.

---

### Post by GammaPoint on 2010-12-17
Here is the output of the boot script:

```


ubuntu@ubuntu:~/Downloads$ more RESULTS.txt 
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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd05dd05d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,238,193,809 1,238,193,747  83 Linux
/dev/sda2       1,238,193,810 1,250,258,624    12,064,815   5 Extended
/dev/sda5       1,238,193,873 1,250,258,624    12,064,752  82 Linux swap / Solar
is


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/loop0                                              squashfs                
                 
/dev/sda1        8b99ad28-6553-4ce2-ba77-6817d7c7e801   ext4                    
                 
/dev/sda5        894433f2-d02b-4b53-ab2d-5d50556ce19f   swap                    
                 

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env reco
rdfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=8b99ad28-6553-4ce2-ba7
7-6817d7c7e801 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8b99ad28-6553-4ce2-ba77-6817d7c7e801
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8b99ad28-6553-4ce2-ba77-6817d7c7e801 /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda5 during installation
UUID=894433f2-d02b-4b53-ab2d-5d50556ce19f none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   1.8GB: boot/grub/grub.cfg
 292.1GB: boot/initrd.img-2.6.31-21-generic
 312.7GB: boot/initrd.img-2.6.32-25-generic
 613.0GB: boot/initrd.img-2.6.35-22-generic
 513.8GB: boot/initrd.img-2.6.35-23-generic
 282.3GB: boot/vmlinuz-2.6.31-21-generic
  65.2GB: boot/vmlinuz-2.6.32-25-generic
 289.9GB: boot/vmlinuz-2.6.35-22-generic
  37.4GB: boot/vmlinuz-2.6.35-23-generic
 513.8GB: initrd.img
 613.0GB: initrd.img.old
  37.4GB: vmlinuz
 289.9GB: vmlinuz.old


```

See anything useful?

---

### Post by Hippytaff on 2010-12-17
I think, from the results.txt, that your not dual booting with windows? but apart from that it looks like a graphics card issue. try pressing shift at boot to get the grub menu, then highlight ubuntu, press e then change 'quiet splash' to 'nomodeset' then do CTRL+X to boot. If that works go to system -> Adminisration -> additional drivers

Bear in mind I might be wildly wrong in my diagnosis :-s

---

### Post by GammaPoint on 2010-12-17
> **Hippytaff said:**
> I think, from the results.txt, that your not dual booting with windows?

What's windows? :D

> but apart from that it looks like a graphics card issue. try pressing shift at boot to get the grub menu, then highlight ubuntu, press e then change 'quiet splash' to 'nomodeset' then do CTRL+X to boot. If that works go to system -> Adminisration -> additional drivers

Bear in mind I might be wildly wrong in my diagnosis :-s

Is there something in RESULTS.txt that makes you think it's a graphics card issue, or does my RESULTS.txt look okay?  

And what does nomodeset do exactly? Something with the video card drivers? 

Also, does my RESULTS.txt suggest that what dabomb mentioned might work or does it suggest that that isn't the problem?

Thanks for your help.

---

### Post by Hippytaff on 2010-12-17
I looked at what was mentioned, and I don't think that is the problem.

nomodeset just prevents your nividia card taking precedent when booting,

worth a try

---

### Post by GammaPoint on 2010-12-17
Well, I was trying to do as you said but the computer just booted into Ubuntu normally and now it seems like it's working just fine. I'll have to keep an eye on it (and should probably try to replace my video card before it goes out of warranty). 

I'll update this thread if something new happens.

Thanks again :)

---

### Post by Hippytaff on 2010-12-17
As long as it works :-D

---

