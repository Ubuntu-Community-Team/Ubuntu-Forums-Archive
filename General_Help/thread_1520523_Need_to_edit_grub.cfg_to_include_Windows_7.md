---
title: "Need to edit grub.cfg to include Windows 7"
date: 2010-06-29
forum: General Help
---

### Post by LeapingLlama on 2010-06-29
Hey everyone, I just did a fresh install of Lucid Lynx 10.4, but now whenever I boot up, at the boot loader, Windows 7 is no longer on the list. I want to now how to properly edit grub.cfg in /boot/grub so that I can boot into Windows 7 from the boot loader. The Windows partition is found in /dev/sda2. The folder name is 2EB2621EB261EB33. If anyone could tell me how write the entry in grub.cfg for Windows 7 to boot that would be awesome!

---

### Post by dabl on 2010-06-29
Except for testing your theory of how to fix the menu, there is no point in editing /boot/grub/grub.cfg, as those edits will be lost in the next "update-grub".  The script file for definition of the Win 7 boot entry is in the file /etc/grub.d/30_os-prober.  That's where you can make a permanent edit that will be picked up in /boot/grub/grub.cfg at each update.

---

### Post by wilee-nilee on 2010-06-29
First try in the terminal.
```
sudo-update-grub
```
If this does not load W7 and you can't boot W7 then post the bootscript in my signature in code tags as described before doing anything else.

There is no reason you should have to load W7 in the grub.cfg with grub2 if everything is set up correctly and it's not a wubi install, then grub2 is a auto-loading program.

---

### Post by LeapingLlama on 2010-06-29
So would I simply run the script, or edit it to include the Windows 7 entry? And if I am to edit it, how would I go about editing it?

---

### Post by linux-hack on 2010-06-29
> **LeapingLlama said:**
> So would I simply run the script, or edit it to include the Windows 7 entry? And if I am to edit it, how would I go about editing it?

Why dont you juste read the doc about Grub2 ? 

Or check this out : [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by LeapingLlama on 2010-06-29
Okay I just ran the boot info script and got these results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /bootmgr /Boot/BCD 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30942895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   116,293,631   115,881,984   7 HPFS/NTFS
/dev/sda3         281,638,912   312,581,807    30,942,896  12 Compaq diagnostics
/dev/sda4         116,295,678   281,636,863   165,341,186   5 Extended
/dev/sda5         116,295,680   128,012,287    11,716,608  82 Linux swap / Solaris
/dev/sda6         128,014,336   281,636,863   153,622,528  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CB06002B05FD146                       ntfs                                     
/dev/sda2        2EB2621EB261EB33                       ntfs                                     
/dev/sda3        709A6BBB9A6B7C8A                       ntfs       LENOVO_PART                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        cbacfc9e-c4c1-4751-b343-b95739e331ca   swap                                     
/dev/sda6        271a824c-ed10-43e4-8924-69707edd6b66   ext3                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /media/2EB2621EB261EB33  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/2CB06002B05FD146  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1ac39e86-555a-4855-bcf0-f267bee8cb2b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=1ac39e86-555a-4855-bcf0-f267bee8cb2b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1ac39e86-555a-4855-bcf0-f267bee8cb2b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2cb06002b05fd146
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 709a6bbb9a6b7c8a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.32-21-generic
    ??GB: boot/initrd.img-2.6.32-22-generic
    ??GB: boot/vmlinuz-2.6.32-21-generic
    ??GB: boot/vmlinuz-2.6.32-22-generic

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=271a824c-ed10-43e4-8924-69707edd6b66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=271a824c-ed10-43e4-8924-69707edd6b66 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=271a824c-ed10-43e4-8924-69707edd6b66 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=271a824c-ed10-43e4-8924-69707edd6b66 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 271a824c-ed10-43e4-8924-69707edd6b66
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 709a6bbb9a6b7c8a
	chainloader +1
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
UUID=271a824c-ed10-43e4-8924-69707edd6b66 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cbacfc9e-c4c1-4751-b343-b95739e331ca none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  98.4GB: boot/grub/core.img
  98.3GB: boot/grub/grub.cfg
  98.3GB: boot/initrd.img-2.6.32-21-generic
  98.3GB: boot/initrd.img-2.6.32-22-generic
  98.3GB: boot/vmlinuz-2.6.32-21-generic
  98.4GB: boot/vmlinuz-2.6.32-22-generic
  98.3GB: initrd.img
  98.3GB: initrd.img.old
  98.4GB: vmlinuz
  98.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by LeapingLlama on 2010-06-29
I looked in the thread about grub2, [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), and I looked under item 6, the part about adding custom entries. So far, I have edited the first three lines correctly, but I'm unsure what to put on the last two lines:
```
menuentry "Windows 7 (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
linux /sysrcd/rescuecd subdir=sysrcd setkmap=us
initrd /sysrcd/initram.igz
}
```

---

### Post by wilee-nilee on 2010-06-29
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   **/boot/grub/grub.cfg** /bootmgr /Boot/BCD 
                       **/boot/grub/core.img**


First you have grub in the windows partition, loading windows to anything will not work.

Use this link to clear out grub.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

In the future don't just read threads and peck at the OS you may lose the whole thing, every boot problem is different and needs to be examined with the bootscript at the least.

And remember that if you get a where to install grub it only goes to the master boot record which would be sda in this case.

---

### Post by oldfred on 2010-06-29
+1 on wilee-nilee suggestion

the windows boot flag is on sda1 and the windows files required for booting at in that partition. The osprober and perhaps the script are not seeing it totally as a windows partition. You also need to delete the files wilee-nilee highlighted. The run:
sudo update-grub

---

### Post by LeapingLlama on 2010-06-30
> **wilee-nilee said:**
> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   **/boot/grub/grub.cfg** /bootmgr /Boot/BCD 
                       **/boot/grub/core.img**


First you have grub in the windows partition, loading windows to anything will not work.

Use this link to clear out grub.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

In the future don't just read threads and peck at the OS you may lose the whole thing, every boot problem is different and needs to be examined with the bootscript at the least.

And remember that if you get a where to install grub it only goes to the master boot record which would be sda in this case.

Okay I followed the link and followed their directions, however in the step labeled "sixth screen," it says choose the option "BackupBS." My only options are Quit, List, Rebuild BS, Repair MFT, and Dump. I would choose Rebuild BS, but I am unsure if it is the same, and do not want to cause further trouble. Could anyone confirm whether I should choose this option?

---

### Post by wilee-nilee on 2010-06-30
> **LeapingLlama said:**
> Okay I followed the link and followed their directions, however in the step labeled "sixth screen," it says choose the option "BackupBS." My only options are Quit, List, Rebuild BS, Repair MFT, and Dump. I would choose Rebuild BS, but I am unsure if it is the same, and do not want to cause further trouble. Could anyone confirm whether I should choose this option?

here are the instructions from the link.
>  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm
then press "q" a few times to quit testdisk, reboot and see whether you can boot into Windows. If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem. But it could also mean that your backup boot sector is corrupted, in which case you will of to use "fixboot" from a Windows CD to repair the boot sector.

After you fixed the Windows boot sector, you might have to update the Grub Menu. For Grub 2 just run

  sudo update-grub



---

### Post by LeapingLlama on 2010-06-30
But my problem is that I do not have the option BackupBS when I should. I only have the options I listed in my last post.

Edit: Hehe, nvm I see what I need. Sorry!

---

### Post by LeapingLlama on 2010-06-30
Apparently my problem had a rather simple fix. I had had a previous problem when I accidentally deleted an important boot file, and was using the installation cd to boot. I copied /boot to a boot partition I thought was associated with Linux. Turns out, it was Windows' boot partition. I simply deleted the /boot copy and now everything works fine. I looked inside and saw a grub folder, and I knew that had to be it, since wilee-nilee said I had grub in the Windows partition. Thank you very much for the help!

PS: How do I mark this thread as solved?

---

### Post by wilee-nilee on 2010-06-30
> **LeapingLlama said:**
> Apparently my problem had a rather simple fix. I had had a previous problem when I accidentally deleted an important boot file, and was using the installation cd to boot. I copied /boot to a boot partition I thought was associated with Linux. Turns out, it was Windows' boot partition. I simply deleted the /boot copy and now everything works fine. I looked inside and saw a grub folder, and I knew that had to be it, since wilee-nilee said I had grub in the Windows partition. Thank you very much for the help!

PS: How do I mark this thread as solved?

Good deal I think the solve is in thread tools, somewhere on this page not really sure.

---

