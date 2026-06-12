---
title: "Repairing Vista From Ubuntu"
date: 2011-03-20
forum: General Help
---

### Post by skytreader on 2011-03-20
I'm sorry for such a Windows question on an Ubuntu forum but, as Ubuntu is the last bullet in my gun, I might as well try.

I'm having problems loading Vista. As it shows the loading screen, everything goes black and displays a "Windows Loading Error" message. It suggests that I repair Vista using my OS CD though it also gives me the option to load Vista in various Safe Modes and in Normal Mode as well. Choosing Safe Mode loads a lot of files from system32 and, after sometime, it shuts down abruptly.

Sometimes, this screen won't even get to load. My laptop promptly shuts down with no warning whatsoever.

I managed to load it in Normal Mode, shut down properly, then reboot again without the loading error screen showing up. But then after a few minutes of checking things in my normal boot, my laptop shuts down without warning. Reloading Vista restarts that vicious issue with the "Windows Loading Error" message.

Here comes Ubuntu. When I load Ubuntu (10.04 LL), everything is just fine. As of now I've managed to back up everything of importance in my Windows partition through Ubuntu. I'm currently running a SMART test on my partitioned hard drive through Ubuntu's Disk Utility and the most alarming thing I've seen in the report so far is a Read Error Rate with a value of 4.

Since Ubuntu is loading and running smoothly I am (optimistically) discounting hardware trouble. Now, I'm hoping to get the Vista CD to run at start-up so I can repair Vista. The problem is GRUB always kicks-in. I was hoping that the CD will load when I choose Vista but as my computer shuts down without warning when loading Vista, I can't get it to work. Loading in Ubuntu does nothing with the CD as well.

Any guidelines? Thanks!

---

### Post by Quackers on 2011-03-20
For a good starting place please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by abyrne on 2011-03-20
It sounds like your BIOS is set to boot straight to your hard drive. Usually, you can override this by pressing F11, F12, or Escape during the POST screen (your computer's manufacturer's logo is usually displayed during this), and then select your CD drive.

---

### Post by skytreader on 2011-03-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   272,446,334   272,444,287   7 HPFS/NTFS
/dev/sda2         272,446,335   488,392,064   215,945,730   5 Extended
/dev/sda5         272,446,398   479,524,184   207,077,787  83 Linux
/dev/sda6         479,524,248   488,392,064     8,867,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58BC7C55BC7C2F9C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        22b225d3-fa48-49a5-b0c8-d9de12767191   ext4                                     
/dev/sda6        390570ae-bdde-4522-8297-961644b8895f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=chad)
/dev/sda1        /media/58BC7C55BC7C2F9C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
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
search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 58bc7c55bc7c2f9c
	chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=390570ae-bdde-4522-8297-961644b8895f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 139.6GB: boot/grub/core.img
 140.6GB: boot/grub/grub.cfg
 141.0GB: boot/initrd.img-2.6.32-30-generic
 140.7GB: boot/vmlinuz-2.6.32-30-generic
 141.0GB: initrd.img
 140.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

I don't know if it matters but I clean up old Linux kernels every now and then using another script I downloaded from SourceForge (I forgot what). I think that it was the first time I loaded Vista after my most recent kernel-cleaning.

---

### Post by Quackers on 2011-03-20
Thanks. The boot script output looks fine. I see no problems there.
Can I ask firstly, have you re-installed Vista at some time, and, secondly, how did you create the free space for Ubuntu to install into?

---

### Post by skytreader on 2011-03-20
My laptop is second-hand from my uncle. Before giving it to me, he wiped it clean, presumably by reinstalling Vista. But that was over a year ago and as far as I know he doesn't partition his hard drive. When it came to me, I installed Ubuntu 9.10. I partitioned the drive by the partition option that goes when you install Ubuntu. That's how I created the free space for Ubuntu, unless I misunderstood your question. For the whole year I've been using this laptop, I haven't reinstalled Vista. (Ubuntu though, when I upgraded to 10.04).

---

### Post by Quackers on 2011-03-20
Ok, thanks.
When you try to boot Vista do you get an option to repair your system?

---

### Post by skytreader on 2011-03-20
> **Quackers said:**
> Ok, thanks.
When you try to boot Vista do you get an option to repair your system?

No. The only thing it tells me anything related to repair is through the Vista installer.

---

### Post by Quackers on 2011-03-20
I can only suggest that you run a chkdsk on the C: drive. However, it may not allow that from the Windows installation cd/dvd.
Firstly you will need to boot from the Windows install dvd. To do this you will need to change your bios settings so that the cd drive is the first boot device.
Once booted from the disc select the recovery console (maybe by pressing R at some time, the screen will tell you). Once in the recovery console choose the command prompt option and enter ```
 chkdsk C: /r
``` and press enter.
If it runs and reports errors, you need to keep running it again, until, no errors are reported. Then reboot and try to boot Vista.
If it won't let you run it, you may need to get Vista booting first (but this will over-write grub - which can be replaced later).
In the command prompt option again, enter ```
bootrec.exe /fixmbr
``` then if that runs ok, reboot and Vista should try to boot automatically.
See how these things go for now.

---

### Post by skytreader on 2011-03-20
Thanks a lot Quackers. I'll try that as soon as I get the time. I'll update when I've tried it. Again, thanks :D.

---

### Post by Quackers on 2011-03-20
You're welcome. Good luck :-)

---

### Post by skytreader on 2011-03-20
> **Quackers said:**
> I can only suggest that you run a chkdsk on the C: drive. However, it may not allow that from the Windows installation cd/dvd.
Firstly you will need to boot from the Windows install dvd. To do this you will need to change your bios settings so that the cd drive is the first boot device.
Once booted from the disc select the recovery console (maybe by pressing R at some time, the screen will tell you). Once in the recovery console choose the command prompt option and enter ```
 chkdsk C: /r
``` and press enter.


This seems to work. As of now, Vista is running smoothly again (I'm posting this from Vista). However, instead of /r, I used /F. Thanks much Quackers.

(I didn't really remember the /r part. After my first run of "chkdsk C:", it told me that it found errors but it cannot fix them until I run it with /F.)

From what I can gather of the errors, some unallocated memory blocks were marked as allocated. Does anyone know how this could've happened and how to prevent it? It wouldn't hurt not knowing but it'd be still handy as this problem is quite inconvenient. Thanks!

---

