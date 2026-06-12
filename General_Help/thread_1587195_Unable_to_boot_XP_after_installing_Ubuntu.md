---
title: "Unable to boot XP after installing Ubuntu"
date: 2010-10-03
forum: General Help
---

### Post by Shining KoW210 on 2010-10-03
Okay I have a netbook, I had Windows XP installed it. I created a USB bootable memory stick for the latest version of the netbook version of Ubuntu, everything installed correctly, but when I turn on my netbook to the boot screen and select Windows XP it just goes to a blank screen with a line, and it does nothing. I installed Windows XP via a USB memory stick aswell. Can anyone help me? If you need more information just ask and tell me how I can get it, I'm new to Ubuntu. I've read around and does the fix for this have to do with GRUB?

---

### Post by spiky001 on 2010-10-03
Hi did you want to install dual boot? on insterlation did you install ubuntu side by side with xp can you boot the live cd. can you give the output of 
```
sudo fdisk -l
``` from live cd

---

### Post by Shining KoW210 on 2010-10-03
> **spiky001 said:**
> Hi did you want to install dual boot? on insterlation did you install ubuntu side by side with xp can you boot the live cd. can you give the output of 
```
sudo fdisk -l
``` from live cd

Yes I installed it "side by side with XP" It allowed 420GB for XP and 80GB for Ubuntu.

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf68ff81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       51072   410235480+   7  HPFS/NTFS
/dev/sda2           51073       60802    78150657    5  Extended
/dev/sda5           51073       60400    74921984   83  Linux
/dev/sda6           60400       60802     3227648   82  Linux swap / Solaris

Ubuntu runs fine, and yes I do want to dual boot.

---

### Post by andrewthomas on 2010-10-03
I would boot from windows CD/USB  and select r for recovery, then fixmbr.

Boot into XP to make sure it works.

Then reinstall grub2 using [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Shining KoW210 on 2010-10-03
> **andrewthomas said:**
> I would boot from windows CD/USB  and select r for recovery, then fixmbr.

Boot into XP to make sure it works.

Then reinstall grub2 using [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

When I tried booting Windows XP from USB it just loads up Windows XP on my computer. When I tried booting Windows 7 from USB and tried to repair the MBR it says that it couldn't find any Windows Installations.

---

### Post by wilee-nilee on 2010-10-03
Boot a live cd of ubuntu and run the script in my signature and post the text in code tags. Code tags can be made by clicking on the # in the reply and putting the text in between.

---

### Post by Shining KoW210 on 2010-10-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   820,471,023   820,470,961   7 HPFS/NTFS
/dev/sda2         820,471,806   976,773,119   156,301,314   5 Extended
/dev/sda5         820,471,808   970,315,775   149,843,968  83 Linux
/dev/sda6         970,317,824   976,773,119     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D05CB90F5CB8F0F8                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b1f2d543-fb42-4a83-b94f-32ab5991307b   ext4                                     
/dev/sda6        c6f7842f-dac9-428d-baed-980d40e99785   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Home Edition" /fastdetect

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
search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
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
search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b1f2d543-fb42-4a83-b94f-32ab5991307b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b1f2d543-fb42-4a83-b94f-32ab5991307b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b1f2d543-fb42-4a83-b94f-32ab5991307b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b1f2d543-fb42-4a83-b94f-32ab5991307b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b1f2d543-fb42-4a83-b94f-32ab5991307b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d05cb90f5cb8f0f8
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b1f2d543-fb42-4a83-b94f-32ab5991307b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c6f7842f-dac9-428d-baed-980d40e99785 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 446.0GB: boot/grub/core.img
 420.2GB: boot/grub/grub.cfg
 476.3GB: boot/initrd.img-2.6.32-21-generic
 446.1GB: boot/initrd.img-2.6.32-25-generic
 445.9GB: boot/vmlinuz-2.6.32-21-generic
 446.1GB: boot/vmlinuz-2.6.32-25-generic
 446.1GB: initrd.img
 476.3GB: initrd.img.old
 446.1GB: vmlinuz
 445.9GB: vmlinuz.old
```

According to the results Windows XP is still there.

---

### Post by wilee-nilee on 2010-10-03
If you resized the XP partition with the install for Ubuntu all at the same time this might have caused a glitch. The script looks basically correct.

I would run a chkdsk /r.

You can do this in two ways by booting the XP install usb and choosing repair and running that chkdsk /r command, it will actually run on reboot, just say yes to this option.


You can also maybe get to the safemode screen and the choose command and run this command. Hit f8 repeatedly after choosing XP at the grub menu for safe mode.

So to reload the MS bootloader if needed, use the XP install usb, and just in the command run fixmbr.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

This link shows getting to the command line with a install disc.

---

### Post by Shining KoW210 on 2010-10-04
> **wilee-nilee said:**
> If you resized the XP partition with the install for Ubuntu all at the same time this might have caused a glitch. The script looks basically correct.

I would run a chkdsk /r.

You can do this in two ways by booting the XP install usb and choosing repair and running that chkdsk /r command, it will actually run on reboot, just say yes to this option.


You can also maybe get to the safemode screen and the choose command and run this command. Hit f8 repeatedly after choosing XP at the grub menu for safe mode.

So to reload the MS bootloader if needed, use the XP install usb, and just in the command run fixmbr.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

This link shows getting to the command line with a install disc.

I ran a chkdisk, then I booted XP with command prompt, fix the MBR using the command using fixmbr. Booted up my computer went down to try to boot Windows XP, and it doesn't boot, it just sits there, I can only boot Windows XP if I boot from my USB stick.

Think I should try a fixboot?

---

### Post by wilee-nilee on 2010-10-04
> **Shining KoW210 said:**
> I ran a chkdisk, then I booted XP with command prompt, fix the MBR using the command using fixmbr. Booted up my computer went down to try to boot Windows XP, and it doesn't boot, it just sits there, **I can only boot Windows XP if I boot from my USB stick.**

Think I should try a fixboot?

Lets look at the script again, make sure all the thumbs are plugged in when you run it, so information about it and their MBR is shown. Since you have 2 sticks one with XP one with the netbook version be very specific about which one you used to do what with.

Did you try to access XP from the grub menu after running the chkdsk, I think you did I'm just making sure. It sounds like you can boot XP from the Ubuntu thumb, which may just mean that grub will boot XP now and just needs to be put back in the MBR=sda if it has been replaced with the MS bootloader.

I am a little confused about the highlighted part, as the previous paragraph shows, boot means the installed XP or the installation gui.

---

### Post by Shining KoW210 on 2010-10-04
> **wilee-nilee said:**
> Lets look at the script again, make sure all the thumbs are plugged in when you run it, so information about it and their MBR is shown. Since you have 2 sticks one with XP one with the netbook version be very specific about which one you used to do what with.

Did you try to access XP from the grub menu after running the chkdsk, I think you did I'm just making sure. It sounds like you can boot XP from the Ubuntu thumb, which may just mean that grub will boot XP now and just needs to be put back in the MBR=sda if it has been replaced with the MS bootloader.

I am a little confused about the highlighted part, as the previous paragraph shows, boot means the installed XP or the installation gui.

Yes I tried to access XP from the GRUB menu after running the chkdsk and it still doesn't load. I can boot XP using my Windows XP USB bootable memory stick used to install XP. With the XP USB bootable memory stick, I can either go to the instillation menu or boot Windows XP that is installed onto my harddrive.

---

### Post by wilee-nilee on 2010-10-04
> **Shining KoW210 said:**
> Yes I tried to access XP from the GRUB menu after running the chkdsk and it still doesn't load. I can boot XP using my Windows XP USB bootable memory stick used to install XP. With the XP USB bootable memory stick, I can either go to the instillation menu or boot Windows XP that is installed onto my harddrive.

Since you have changed things the best way I can help, if I can, is by seeing the script again with the XP and other thumb plugged in. Thanks for confirming that information, I try to be very careful with this stuff.;)

---

### Post by Shining KoW210 on 2010-10-04
> **wilee-nilee said:**
> Since you have changed things the best way I can help, if I can, is by seeing the script again with the XP and other thumb plugged in. Thanks for confirming that information, I try to be very careful with this stuff.;)

I've only been using 1 USB stick, I've been using another computer to switch between Windows XP and the Ubuntu Live CD.

So what you are asking me to do is run the script with both an XP USB and an Ubuntu USB, and run the Ubuntu USB and run the script?


I tried running this code and restarting but it still didn't work 
> sudo update-initramfs -u -k all
sudo update-grub


I just tried this - [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But I end up with the problem of 
> If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem. But it could also mean that your backup boot sector is corrupted, in which case you will of to use "fixboot" from a Windows CD to repair the boot sector.

I'm going to try fixboot.


After I did fixboot I restarted my computer and at GRUB I now had two options for Windows XP, one for Windows XP and one for Windows XP Loader, I first selected the loader and it was a line and nothing happened, so I restarted and chose the regular Windows XP and it gave me this error

> Error: No Such Device: acdd - 4199.
Error: hd1,1 cannot get C/H/S values.
Press any button to continue...

So I did and it took me back to the GRUB menu.


I tried doing this again

> sudo update-initramfs -u -k all
sudo update-grub

And now in GRUB, only the Windows Loader option appears, not the regular Windows XP option.

---

### Post by Shining KoW210 on 2010-10-05
Can anyone else help me?

---

### Post by oldfred on 2010-10-05
Is the windows loader the install on sda1? that is the install you want to boot.

If the USB boots the windows install I would experiment with editing the grub entries. Use e at the grub menu and delete various lines.

The only lines it should absolutely need are in red.

menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
   [COLOR=Red] set root='(hd0,1)'[/COLOR]
    search --no-floppy --fs-uuid --set d05cb90f5cb8f0f8
    drivemap -s (hd0) ${root}
    [COLOR=Red]chainloader +1[/COLOR]
}

---

### Post by Shining KoW210 on 2010-10-06
> **oldfred said:**
> Is the windows loader the install on sda1? that is the install you want to boot.

If the USB boots the windows install I would experiment with editing the grub entries. Use e at the grub menu and delete various lines.

The only lines it should absolutely need are in red.

menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
   [COLOR=Red] set root='(hd0,1)'[/COLOR]
    search --no-floppy --fs-uuid --set d05cb90f5cb8f0f8
    drivemap -s (hd0) ${root}
    [COLOR=Red]chainloader +1[/COLOR]
}

I am not sure if it is or not. When I went to edit in GRUB it was just like that above. When I just had Windows XP installed onto my computer and it would load up the loader I always had the option to either boot Windows XP or repair Windows XP, so it wasn't the standard boot sequence.

Here's the BOOT.INI for the Windows XP USB - 

> [Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="2. GUI Mode Setup Windows XP, Continue Setup + Start XP" /FASTDETECT

C:\SETUPLDR.bs="1. TXT Mode Setup Windows XP, Never unplug USB-Drive Until After Logon"


When I select the GUI Mode Setup Windows XP, it boots up Windows XP, when I select the TXT Mode Setup Windows XP it loads up the instillation menu and recovery menu.

---

### Post by @lpha on 2010-10-06
I remember something similar to this happened to me. XP wouldn't even show up in the bootloader. After working inside ubuntu a little bit, then restarting the computer from ubuntu, it appeared and everything worked.

---

### Post by Shining KoW210 on 2010-10-06
> **@lpha said:**
> I remember something similar to this happened to me. XP wouldn't even show up in the bootloader. After working inside ubuntu a little bit, then restarting the computer from ubuntu, it appeared and everything worked.

What exactly did you do to make it work?

---

