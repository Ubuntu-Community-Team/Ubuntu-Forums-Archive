---
title: "Grub wont boot windows XP after Ubuntu 10.04 installation"
date: 2011-02-15
forum: General Help
---

### Post by elfuego on 2011-02-15
When I select Windows XP at the grub menu, it doesnt start loading windows XP, but returns back to the grub menu instead. Selecting windows XP again returns it to boot menu again and again. Ubuntu loading (when ubuntu is selected) works fine.

The installation process and hardware looked like this:
1) only one brand new HDD, no other HDDs
2) created 1 NTFS Partition and installed windows XP on it
3) launched Ubuntu 10.04 LiveCD, used custom partitioning, created Swap and root partitions (as I always did)
*4*) I got asked where do I want the boot information stored and I selected the windows boot partition (I guess this created the problem?).

Ever since, I cannot enter windows, even though I can access the windows partition from within Ubuntu. I am quite unfamiliar with Grub 2. I know that there are already quite a few similar questions, but I havent found this type of issue before. I already installed and set up Ubuntu as nice as it can get and I dislike the idea of reinstalling the whole system just to get windows back. Is there a better way?

Thanks! ):P

---

### Post by coffeecat on 2011-02-15
This was a very big mistake, I regret to say:

> **elfuego said:**
> 
*4*) I got asked where do I want the boot information stored and I selected the windows boot partition (I guess this created the problem?).

Fortunately it should be relatively easily fixed. What has probably happened is that some grub files have overwritten Windows boot files in your Windows partition. You should not have any of grub in the Windows partition at all. What I don't understand is how you are getting the grub menu because if you installed grub stage 1 to the Windows partition instead of the mbr, you wouldn't see the grub menu.

So - rather than me making false assumptions :), let's see what is really going on. If you can boot into Ubuntu on your hard drive do so, or boot up a live Ubuntu CD, and then go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the results.txt file. Please post that within [noparse]```
 and 
```[/noparse] tags otherwise it is near-unreadable. You can use the # icon on the message toolbar for this.

Question: do you have a Microsoft XP install CD, **not** an OEM manufacturer's restore disc?

---

### Post by elfuego on 2011-02-17
> **coffeecat said:**
> This was a very big mistake, I regret to say: ...


I thought so. Ever since I started with ubuntu (feisty fawn) I never got that question before (it always installed automatically & correctly) so according to Murphys law I answered wrong. :(

I will do as you advise and I do have windows XP installation CD. I suppose I should run fixboot and fixmbr and then reinstall grub... right?

---

### Post by coffeecat on 2011-02-17
> **elfuego said:**
> I will do as you advise and I do have windows XP installation CD. I suppose I should run fixboot and fixmbr and then reinstall grub... right?

No, not yet. My guess is that you will have to run fixboot to repair the boot files in the Windows C: partition, but that is only a guess at the moment. By running fixmbr you could make the situation worse if you don't diagnose what is causing Windows to fail to boot first.

Run the boot script that I linked before so that we can see what the situation is, and then we can take it from there.

---

### Post by elfuego on 2011-02-18
OK, here are the contents of the boot script. What do you think?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 240391440 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sda2         156,280,830   312,580,095   156,299,266   5 Extended
/dev/sda5         156,280,832   160,280,575     3,999,744  82 Linux swap / Solaris
/dev/sda6         160,282,624   312,580,095   152,297,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9CA81FF5A81FCD20                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cf8055c6-e595-4dbc-bc7a-c9b632d81f17   swap                                     
/dev/sda6        faaf4203-94e4-424b-8831-b5c9012db859   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=faaf4203-94e4-424b-8831-b5c9012db859 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=faaf4203-94e4-424b-8831-b5c9012db859 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=faaf4203-94e4-424b-8831-b5c9012db859 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=faaf4203-94e4-424b-8831-b5c9012db859 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set faaf4203-94e4-424b-8831-b5c9012db859
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 9ca81ff5a81fcd20
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
UUID=faaf4203-94e4-424b-8831-b5c9012db859 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cf8055c6-e595-4dbc-bc7a-c9b632d81f17 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 123.0GB: boot/grub/core.img
 153.1GB: boot/grub/grub.cfg
  83.5GB: boot/initrd.img-2.6.35-22-generic
  83.5GB: boot/initrd.img-2.6.35-25-generic
 123.0GB: boot/vmlinuz-2.6.35-22-generic
 123.0GB: boot/vmlinuz-2.6.35-25-generic
  83.5GB: initrd.img
  83.5GB: initrd.img.old
 123.0GB: vmlinuz
 123.0GB: vmlinuz.old
```

---

### Post by coffeecat on 2011-02-18
First of all:

> **elfuego said:**
> OK, here are the contents of the boot script. What do you think?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
```

It looks as though you already ran fixmbr from the Windows CD. If so, this wasn't necessary and you'll need to reinstall grub. More in a moment. 

Next thing:

> **elfuego said:**
> ```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 240391440 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

You do indeed have grub in the Windows partition. This is what is preventing Windows from booting. Running fixboot from the Windows install CD command prompt, **but not fixmbr**, should solve this.

If that doesn't work, have a look at this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can repair the Windows boot files from the Ubuntu live CD if you install testdisk in the live session. Then follow the instructions on that link.

Lastly, you need to reinstall grub to the mbr to get the grub menu. See this link:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Your Ubuntu root partition is sda6, so the terminal commands you need from the live Ubuntu CD are:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Once you've done that, reboot into Ubuntu on the hard drive and run:

```
sudo update-grub
```Looking at your grub.cfg file, that last is probably unnecessary, but run it anyway - it won't do any harm.

---

### Post by elfuego on 2011-02-19
Yup, that did it. Ran testdisk - fixed windows. Ran LiveCD with the two commands and restored ubuntu. Both work fine now. Thanks! :)
 
And no, I havent been doing anything before that (not running fixmbr). Thats the mess that was created by (*4*). I did say I will wait :)

Oh one more thing, after each kernel update I get a new entry in grub. In old grub it was enough to remove the few lines of grub.cfg and they were gone, but how do I do that in grub 2 ? :confused:

---

### Post by coffeecat on 2011-02-19
> **elfuego said:**
> Oh one more thing, after each kernel update I get a new entry in grub. In old grub it was enough to remove the few lines of grub.cfg and they were gone, but how do I do that in grub 2 ? :confused:

It's best to keep at least the previous version of the  kernel in case you have problems with the latest, but a collection of three or more does get unwieldy. The best way is to uninstall the unwanted kernel(s). That way, not only does the grub menu entry get automagically removed, but all the unwanted kernel files get removed as well, freeing up about 100MB of space.

To uninstall; say the kernel you want to remove is the 2.6.23-24 one, simply search Synaptic with that string. There will be 3 or 4 installed packages corresponding to that version of the kernel. Mark them all for complete removal and click on apply.

---

### Post by elfuego on 2011-02-19
> **coffeecat said:**
> It's best to keep at least the previous version of the  kernel in case you have problems with the latest, but a collection of three or more does get unwieldy. The best way is to uninstall the unwanted kernel(s). That way, not only does the grub menu entry get automagically removed, but all the unwanted kernel files get removed as well, freeing up about 100MB of space.

To uninstall; say the kernel you want to remove is the 2.6.23-24 one, simply search Synaptic with that string. There will be 3 or 4 installed packages corresponding to that version of the kernel. Mark them all for complete removal and click on apply.

Thanks! I actually really didn't know that. I always thought that was a bug and not a feature to have all those kernels listed :)

---

### Post by elfuego on 2011-05-20
Thread bump because I have just experienced exactly the same problem with Ubuntu 11.04 upgrade on the same computer. 11.04 upgrade failed miserably and completely messed up grub. Solution was to enter live CD, back up data, completely wipe out messed up installation and do a clean install of 11.04. 

After that, the same thing explained above happened (yet this time there was no prompt where do I want boot info stored). This is officially the first time, that Windows XP survives and over-ages two Ubuntu distros in install-stability. Maybe there will be indeed apocalypse tomorrow :P

---

### Post by coffeecat on 2011-05-20
Boot info script time again, I think! :)

I'll give you the link again because there's a new version compatible with 11.04, here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run that in Natty and post the output as before and we can take it from there. It's a bit odd because a fresh install of Natty will install grub to the mbr, not the Windows partition, so let's see what the boot script says.

I'll have to log off soon, but I'll pick this thread up again in the morning.

---

### Post by elfuego on 2011-05-21
Thanks man, but no need for that :) I already fixed the problem in exactly the same way as before. I just posted and refreshed the thread for others that may experience the similar issue.

To be honest, this time it was sufficient to run testdisk only and fix windows, without grub-update, but the procedure is still the same and the links are still up-to-date. :popcorn:

---

