---
title: "GRUB2: error: no such disk"
date: 2010-03-03
forum: General Help
---

### Post by Jimoid on 2010-03-03
I have a machine with two internal SATA drives sda and sdb. Winows XP is installed on sda and I installed Ubuntu 9.10 on sdb. After installation I rebooted and was able to choose either OS from the grub menu.

After shutting down and rebooting I was greated with the grub rescue prompt and the message

error: no such disk

I was able to boot to a live USB and use my system again. I thought the problem came from grub being installed to the MBR of sdb, rather than sda. Therefore I installed Ubuntu again, however installed grub to the MBR of sda.

Same thing happened again - the first reboot works fine, then subsequent reboots grub cannot find the disk and I am forced to boot from live usb.

Attempt 3 saw me install the root partition onto sda. A couple of reboots later and I was back at the grub rescue prompt. Two days later and after lots of reading I discovered that after doing a reinstall of Ubuntu, rebooting the system then doing a 'sudo update-grub' seemed to fix the disappearing grub problem.

I was wrong. It lasted about 6 reboots between Ubuntu and XP, but has broken again. I don't see what the problem is, can anyone help?

One point to note is that the BIOS does not let me choose which of the two internal drives to use as primary, infact it sees them as a single eSATA drive.

---

### Post by oldfred on 2010-03-03
Are you running raid or lvm to make the drives be as one? That would confuse a standard install.

Run this script so we can see your install:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

There have been issues with raid and HP computers running software that overwrites part of grub2 in the MBR .

---

### Post by Jimoid on 2010-03-04
The disks aren't raided or using LVM as far as I am aware. I inherited this PC with XP installed and two disks. I simply moved all data from disk sdb to sda and wanted to use sdb solely for Linux...


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd42ad42a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   452,085,164   452,085,102   7 HPFS/NTFS
/dev/sda2         463,202,145   488,375,999    25,173,855   7 HPFS/NTFS
/dev/sda3         452,085,165   463,202,144    11,116,980  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd42a1e42

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,097,884   206,097,822  83 Linux
/dev/sdb2    *    206,097,885   247,882,949    41,785,065  83 Linux
/dev/sdb3         247,882,950   264,719,069    16,836,120  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        68A0B0197B68A306                       ntfs                                     
/dev/sda2        420C2BE424A6B160                       ntfs       HP_RECOVERY                   
/dev/sda3        cacb4ae9-97d6-4234-8bb4-5de56fc44a7f   ext3                                     
/dev/sdb1        532d3460-5513-48a8-8c94-e3eb8314d740   ext3                                     
/dev/sdb2        5bc5da96-727f-4271-b977-fc3c517a46b6   ext3                                     
/dev/sdb3        76a285d1-a796-4848-9fab-e74162d9b4b2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /home                    ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional 3GB" /noexecute=optin /3GB /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set cacb4ae9-97d6-4234-8bb4-5de56fc44a7f
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
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cacb4ae9-97d6-4234-8bb4-5de56fc44a7f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cacb4ae9-97d6-4234-8bb4-5de56fc44a7f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cacb4ae9-97d6-4234-8bb4-5de56fc44a7f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cacb4ae9-97d6-4234-8bb4-5de56fc44a7f ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 68a0b0197b68a306
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 420c2be424a6b160
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=cacb4ae9-97d6-4234-8bb4-5de56fc44a7f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=532d3460-5513-48a8-8c94-e3eb8314d740 /home           ext3    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=76a285d1-a796-4848-9fab-e74162d9b4b2 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 236.6GB: boot/grub/core.img
 236.6GB: boot/grub/grub.cfg
 236.6GB: boot/initrd.img-2.6.31-14-generic
 236.6GB: boot/vmlinuz-2.6.31-14-generic
 236.6GB: initrd.img
 236.6GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
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
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 5bc5da96-727f-4271-b977-fc3c517a46b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 68a0b0197b68a306
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 420c2be424a6b160
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=5bc5da96-727f-4271-b977-fc3c517a46b6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=a2862267-3896-403d-846e-684156abea0f /home           ext3    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=76a285d1-a796-4848-9fab-e74162d9b4b2 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 119.3GB: boot/grub/grub.cfg
 119.2GB: boot/initrd.img-2.6.31-14-generic
 119.2GB: boot/initrd.img-2.6.31-19-generic
 119.2GB: boot/vmlinuz-2.6.31-14-generic
 119.2GB: boot/vmlinuz-2.6.31-19-generic
 119.2GB: initrd.img
 119.2GB: initrd.img.old
 119.2GB: vmlinuz
 119.2GB: vmlinuz.old

```

---

### Post by oldfred on 2010-03-04
The boot script shows yours drives as standard, I do not understand why you are seeing them as one drive in BIOS. Perhaps it is a setting in BIOS?

This lists the solutions to your problem. Sometimes all you have to do is reinstall grub, others required removing the "search" line.  Your UUID's do look correct to me but you have 2 installs and the sda3 also shows booting to the install  on sdb2.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

reinstall from live cd to sda
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

And if you can boot from sdb
reinstall from live cd
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

---

### Post by Jimoid on 2010-03-09
OK, I'm writing this post from a USB live disk. I followed the instructions - reinstall from live media to sda3, grub-install etc, booted into fresh install, commented out the search line from /usr/lib/grub/grub-mkconfig_lib and ran update-grub again. This lasted one reboot, then at the next it returned me to the grub rescue prompt as before.

The most annoying thing about this is that each time I am forced to reinstall, any updates and extra software packages I had previously installed are removed and I have to reinstall.

I am not ready to give up yet, but it seems to me that grub2 is a poor choice. I have installed Ubuntu, and many other Linux distros in my time and never had a problem like this. Is it possible to downgrade to grub 0.97? I am confident that that version works and is stable.

Cheers

---

### Post by Jimoid on 2010-03-09
> 
reinstall from live cd to sda
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda


I understand now that you mean reinstall grub to sda. This is mush simpler than a full reinstall, and negates my earlier gripe about updates disappearing.

---

### Post by psusi on 2010-03-09
What do you mean your bios only sees one drive?  Are you using bios fake raid?

---

### Post by Jimoid on 2010-03-09
In the BIOS I can see both drives independently under a menu titled 'devices' (sda is a WD drive called SATA0, and sdb is a Hitachi drive named eSATA). However when I go to the boot order in the BIOS I am only offered one choice for hard drive, and it doesn't specify a name it just says something like 'SATA drive'.

The machine is an HP Compaq dc7900 Small Form Factor. I have been on to the website and trawled the documentation but can't find anything of any use relating to the BIOS.

My ideal would be to have XP on sda and Ubuntu on sdb.

---

### Post by psusi on 2010-03-09
Is that boot info taken while grub was still working?  Or after it broke?  Which menu choice results in the error?  Did you try the others?

---

### Post by Jimoid on 2010-03-10
I did not think that grub would alter the BIOS of the system as grub is loaded from the MBR, whose location is determined by the boot order in the BIOS. I haven't made any changes to the BIOS however, and did not look at it until I found the problem with grub.

One thing that I do find a bit bizarre is that the second internal drive is described as being eSATA. Why not use a regular SATA connection, as according to the documentation the box can support up to 4 SATA drives? The DVD drive is labelled as SATA1. Also both drives are the same capacity, but from different manufacturers.

If the problem continues I fear I may have to try and wipe grub by using the xp recovery disk and install another distro, which is a shame as I am a big fan of Ubuntu but this is my work machine and the problem is affecting my productivity.

Cheers

---

### Post by Jimoid on 2010-03-10
OK, I have done some more investigations this morning and believe that my distrust of grub1.97 was misplaced. I have tried booting into Ubuntu several times and grub worked fine each time. I then tried xp and rebooted and was greated by the grub error. I booted from live usb and reinstalled grub, rebooted and everything was fine again. Theerfore I believe it is a problem with the windows bootloader rewriting the MBR possibly?

At the grub menu I am offered two choices for windows, and I have always chosen the first, which itself was a chainloader to the windows boot loader. At the windows boot loader there are two choices offered:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional 3GB" /noexecute=optin /3GB /fastdetect
```

This time I have chosen the second option from the grub menu (not the windows bootloader code above) for windows, and it turned out to be a recovery mode provided by HP. After exiting this grub has been removed from the MBR and I only have the windows bootloader installed (code above).

This gives me the opputunity to start again and install Ubuntu, however I want to know what the windows bootloader is doing to break grub, and how to stop it from doing this.

Any ideas?

---

### Post by oldfred on 2010-03-10
I thought this was more Vista and Win7

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

---

### Post by Jimoid on 2010-03-17
Thanks oldfred for those links - they are the exact same problem as I have. I followed the advice given in one of them (stop a certain service from starting at boot on XP), but can't report my findings as I haven't booted to windows since.

My only reason for using windows on that box was to use some specific software (matlab), which I have now installed on Ubuntu. I guess we can close this thread, although there is no definite answer. Thanks to all for helping me out, especially oldfred.

Cheers

---

### Post by denneyd on 2010-10-16
I loaded Mint9 (ubuntu 10.04) onto a second SATA drive which had Windows XP Professional on the first drive (/dev/sda).  Grub2 (ver 1.98) recongnized the XP partition correctly, but booting from the Grub2 menu consistently failed, giving a message "autochk not found-skipping autochk" followed by the "blue death" and a system halt.

Lo and behold, Grub2 apparently had flagged the partition with XP as "hidden", revealed by Gparted.(partition>manage flags).  Clearing the hidden-flag immediately solved the booting problem!

I don't know if your problem was different than mine, but its certainly a simple trouble-shoot.

---

