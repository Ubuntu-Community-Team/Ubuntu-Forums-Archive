---
title: "can't access Windows partition"
date: 2010-06-07
forum: General Help
---

### Post by meanmrmustard on 2010-06-07
I've just done a new install of Lucid (on hda/hd0) but the install didn't recognize the Windows 7 install (on sda - recognized by Ubuntu as hdb/hd1). There is also an install of Ubuntu Studio on sda which did get recognized and is in the list at boot up time and will boot normally. I thought the 30_probe script should find the Windows partition and add it to the menu but that didn't happen.
This is a Thinkpad T60.

I've been reading the Grub2 documentation and have determined that the Windows partition is (hd1,1) but I'm not clear on how to add it and all the parameters in order to have Windows show up as a choice in the menu... or even if this is all that needs to be done.

Where do I go next?

---

### Post by meanmrmustard on 2010-06-07
I came up with the right search terms and found this:

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

The script seems to have added Windows but when I choose to boot it I get :

A disk read error occurred
Press Ctrl+Alt+Del to restart

Just guessing but would that be the Windows partition that didn't get read properly or have I borked Grub2 itself?
I don't have much familiarity with Windows these days but I'm wondering if using the (Win) install disk to fix the MBR would be the way to get things back on track.

---

### Post by john newbuntu on 2010-06-07
It appears that the os-prober was not able to determine the windows boot sector files, which is probably why it never identified that OS.  Were you able to boot into win7 properly prior to the install?  
I would suggest repairing the boot sector using the win7 installation CD: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)  (You need to only run /Fixboot).

After repairing, log back into Ubuntu and run "sudo update-grub" and see if grub is able to detect win7.

---

### Post by meanmrmustard on 2010-06-07
> **john newbuntu said:**
> It appears that the os-prober was not able to determine the windows boot sector files, which is probably why it never identified that OS.  Were you able to boot into win7 properly prior to the install?

I didn't try it just continued installing Ubuntu Studio then Lucid on the first hd
>   
I would suggest repairing the boot sector using the win7 installation CD: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)  (You need to only run /Fixboot).

I'll give that a try and see what happens.
> 
After repairing, log back into Ubuntu and run "sudo update-grub" and see if grub is able to detect win7.

---

### Post by meanmrmustard on 2010-06-07
> 
I would suggest repairing the boot sector using the win7 installation CD: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) (You need to only run /Fixboot). 

> I'll give that a try and see what happens.

Windows RE didn't see the installation, when I ran the command it said no file system found.

Tried a new installation of Lucid.
Same issue.

---

### Post by john newbuntu on 2010-06-07
In order to get more system information, download and run the boot info script courtesy of our forum member meierfra: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instructions on this page to download and run the boot_info_script and post the output using code tags.

---

### Post by meanmrmustard on 2010-06-08
Here's the output.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=2c2b6f8f-532d-4586-91fe-d881a9a6e1df)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    48,908,287    48,906,240  83 Linux
/dev/sda2          48,910,334   312,580,095   263,669,762   5 Extended
/dev/sda5          48,910,336    57,698,303     8,787,968  82 Linux swap / Solaris
/dev/sda6          57,700,352   312,580,095   254,879,744  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   308,801,429   308,801,367   7 HPFS/NTFS
/dev/sdb2    *    308,801,430   359,566,829    50,765,400  83 Linux
/dev/sdb3         359,566,830   368,884,529     9,317,700  82 Linux swap / Solaris
/dev/sdb4         368,884,530   976,768,064   607,883,535  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c171cb77-9bbd-4a18-a52b-035a96bc211b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9840bea5-4b17-4ef4-9573-2a2d32a316c5   swap                                     
/dev/sda6        c4094752-9320-4802-ad93-e41b04ec7c8d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5A4FF1885ED789E6                       ntfs                                     
/dev/sdb2        01c6668a-dc72-4042-a512-836e4655f3d6   ext4       root                          
/dev/sdb3        72d7596d-7aa9-4e0e-b2e8-a39c2716619a   swap                                     
/dev/sdb4        5e69d5c7-363c-4c26-94ba-58488eb814c1   ext4       home                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
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
search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c171cb77-9bbd-4a18-a52b-035a96bc211b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c171cb77-9bbd-4a18-a52b-035a96bc211b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hdb,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c171cb77-9bbd-4a18-a52b-035a96bc211b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=01c6668a-dc72-4042-a512-836e4655f3d6 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=01c6668a-dc72-4042-a512-836e4655f3d6 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
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
# / was on /dev/sda1 during installation
UUID=c171cb77-9bbd-4a18-a52b-035a96bc211b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c4094752-9320-4802-ad93-e41b04ec7c8d /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9840bea5-4b17-4ef4-9573-2a2d32a316c5 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=72d7596d-7aa9-4e0e-b2e8-a39c2716619a none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: initrd.img
  17.3GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=01c6668a-dc72-4042-a512-836e4655f3d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=01c6668a-dc72-4042-a512-836e4655f3d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 01c6668a-dc72-4042-a512-836e4655f3d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=01c6668a-dc72-4042-a512-836e4655f3d6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=5e69d5c7-363c-4c26-94ba-58488eb814c1 /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=72d7596d-7aa9-4e0e-b2e8-a39c2716619a none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 177.5GB: boot/grub/core.img
 171.6GB: boot/grub/grub.cfg
 177.5GB: boot/initrd.img-2.6.32-21-generic
 177.5GB: boot/vmlinuz-2.6.32-21-generic
 177.5GB: initrd.img
 177.5GB: vmlinuz
    
```

---

### Post by yetiman64 on 2010-06-08
It seems grub2 bootloader is in the MBR of both drives. 
In the second drive grub2 on sdb is looking to a drive with uuid of 2c2b6f8f-532d-4586-91fe-d881a9a6e1df for grub boot files. 
However no partition with that uuid exists according to the blkid section of the script output.
This may have a large bearing on your situation. Can't see any other abnormalities though.

My suggestion to fix is to remove the grub2 entry on /dev/sbd MBR with dd then run update-grub. The commands:

Edit2: do this from Ubuntu Studio 10.04 install

```
*dd* if=/dev/zero of=/dev/sdb bs=446 count=1
```this removes grub2 bootcode from this drive, but won't remove the drive partition tables, bs of 512 would do that.
Then run
```
sudo update-grub
``` this should now allow grub2 on sda to pick up all the OS's installed.

Edit: Be aware the Ubuntu Studio install will be the grub2 "base" for picking up all the OSes and booting in the future if you follow the above.

---

### Post by john newbuntu on 2010-06-08
/dev/sdb1 is the partition that has your NTFS and hopefully the win7 files but does not have all the boot loader files to get it up and running.  Also, /dev/sdb2 has the boot flag set, which makes me feel that at some point, it would have played the role of the boot sector for win7.

Note that re-installing ubuntu or playing with grub will not help get  back the windows install.  What you could try and do is to change the boot flag to /dev/sdb1 (say, using gparted or otherwise) and then try fixing the win7 boot sector file. 

If this does not work, there is one more option you could try is testdisk as given here in this post by meierfra:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If neither of these help, I am out of ideas on how to resurrect win7 at  this point.  Hopefully someone else can help.

---

### Post by yetiman64 on 2010-06-08
> **john newbuntu said:**
> /dev/sdb1 is the partition that has your NTFS and hopefully the win7 files but does not have all the boot loader files to get it up and running.  Also, /dev/sdb2 has the boot flag set, which makes me feel that at some point, it would have played the role of the boot sector for win7...

@john newbuntu, just noted the missing bootfiles :oops:.
@meanmrmustard, try john newbuntu's link 1st and repair Windows bootfiles, I suspect now that will be your fix and the uuid in MBR of sdb2 will be of little consequence. Sorry didn't mean to confuse the issue.

---

### Post by meanmrmustard on 2010-06-08
> **john newbuntu said:**
>   What you could try and do is to change the boot flag to /dev/sdb1 (say, using gparted or otherwise) and then try fixing the win7 boot sector file. 

:-(
> 
If this does not work, there is one more option you could try is testdisk as given here in this post by meierfra:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If neither of these help, I am out of ideas on how to resurrect win7 at  this point.  Hopefully someone else can help.

OK... first I made /dev/sdb1 bootable and unchecked the flag for /sdb2


Back to "repair your computer"..
When I click "repair your computer" the resulting box shows no OS listed.
Sill I chose the "use recovery tools..." option and continued to the command line to run /Fixboot.
It tells me "The volume does not contain a recognized file system. Please make sure that all file system drivers are loaded and that the volume is not corrupted." Which I suppose is suspect since Windows didn't see the OS in the first place.

Testdisk reported: 
Boot sector: OK 
Backup boot sector Status: OK 
Sectors are identical

Trying once again, to boot Windows 7 in Grub I get:
"error: no such disk" :confused:


It would seem to me that Windows may be corrupted beyond repair and the answer might be to re-install Windows then re-install Grub?

---

### Post by john newbuntu on 2010-06-08
Not sure if it matters to windows, but change your BIOS boot order to boot from the second disk first.  Then, here's one other thing you could try (run 'bootsect' from command line):
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Once you finish this, reboot and see if you are able to boot win7.

---

### Post by meanmrmustard on 2010-06-09
> **john newbuntu said:**
> Not sure if it matters to windows, but change your BIOS boot order to boot from the second disk first.  Then, here's one other thing you could try (run 'bootsect' from command line):
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Once you finish this, reboot and see if you are able to boot win7.

Bootsect didn't work.
Booting from the second drive just leaves me with a flashing cursor.
Trying disk 1 it says "missing operating system."

The problem with "recovery tools" is that when I choose it there is no operating system listed.

I think I'll just bite the bullet and install Windows again.
I'm wondering if it's being pissy just because it's not on the first disk.

---

### Post by john newbuntu on 2010-06-09
Well, once you reverse the boot order in BIOS, it would be on the first disk anyway.  So, sorry I have run out of ideas on resurrecting the win partition.

---

### Post by meanmrmustard on 2010-06-09
> **john newbuntu said:**
> Well, once you reverse the boot order in BIOS, it would be on the first disk anyway.  So, sorry I have run out of ideas on resurrecting the win partition.

No problem!
Thanks for the input - it was fun trying anyway.

---

