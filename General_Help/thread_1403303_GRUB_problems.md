---
title: "GRUB problems"
date: 2010-02-10
forum: General Help
---

### Post by kyeh on 2010-02-10
I have installed a fresh copy of ubuntu 9.10 on one of my machines. The installation was successful without any problems, but when I tried to boot it would always go through the normal BIOS stuff then it would stop after giving the following message "GRUB _".

After that nothing happens, it would not print the menu either (not sure if it does by default, since i'm always dual booting and this one isn't dual boot).

I really have no idea what is causing this, could it be a faulty hard disk?

---

### Post by audiomick on 2010-02-10
It might be that the drive is faulty, or just that it is not spinning up in  time for grub.
You could try looking in BIOS for any "fast boot" options and turning them off. Also, if you have been inside the case, have a look and make sure that all the cables are connected properly. SATA plugs are a bit liable to not being plugged in all the way.

You could try running smartmontools from the live CD to check the drive.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

You could run meierfra's boot info script to see what the state of your install is as far as the boot setup goes
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and post the results.txt here for people to analyse.

---

### Post by darolu on 2010-02-10
When you have Ubuntu only, the default is not to show GRUB menu.
To make it show the menu open a terminal and do:
```
$ sudo nano /etc/default/grub
```
Then comment this line by adding "#" in front of it:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
Save the file with Ctrl+O and then exit with Ctrl+X
Now update your grub with:
```
$ sudo update-grub
```
And that's it, you should see the menu when you restart.

---

### Post by kyeh on 2010-02-10
> **audiomick said:**
> It might be that the drive is faulty, or just that it is not spinning up in  time for grub.
You could try looking in BIOS for any "fast boot" options and turning them off. Also, if you have been inside the case, have a look and make sure that all the cables are connected properly. SATA plugs are a bit liable to not being plugged in all the way.

You could try running smartmontools from the live CD to check the drive.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

You could run meierfra's boot info script to see what the state of your install is as far as the boot setup goes
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and post the results.txt here for people to analyse.

I ran the short test for smartmontools and it detected no problems. I will be running the longer one soon.

Here is the results.txt file

Note: I have two hard drives,
/dev/sda contains data and this data is important.
/dev/sdb OS drive

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 6569479 of 
    the same hard drive for core.img, core.img is at this location on /dev/sdb 
    and looks for (UUID=c3e91d28-6656-4184-abba-ce5b68218f55)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b594

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1 2,930,272,064 2,930,272,064  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9edd9ed

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        612331b3-4657-420a-a8cf-4bbe75737670   ext3                                     
/dev/sdb1        c3e91d28-6656-4184-abba-ce5b68218f55   ext4                                     
/dev/sdb5        892fb926-8ebe-4922-b512-30a761188bee   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/c3e91d28-6656-4184-abba-ce5b68218f55 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c3e91d28-6656-4184-abba-ce5b68218f55
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c3e91d28-6656-4184-abba-ce5b68218f55
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c3e91d28-6656-4184-abba-ce5b68218f55 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c3e91d28-6656-4184-abba-ce5b68218f55
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c3e91d28-6656-4184-abba-ce5b68218f55 ro single 
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=c3e91d28-6656-4184-abba-ce5b68218f55 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=892fb926-8ebe-4922-b512-30a761188bee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

```

---

### Post by audiomick on 2010-02-10
Hi.
Could be that this
 > Grub 2 is installed in the MBR of /dev/[COLOR=Red]sda [/COLOR]and looks at sector 6569479 of 
    the [COLOR=Red]same hard drive for core.img[/COLOR], core.img is at this location on [COLOR=Red]/dev/sdb[/COLOR] 
is your problem (right at the start of the output text).

I am not a great expert on this, so it wont hurt to wait a bit for a second opinion, but I think you may need to re-configure/re-install grub.

In the Grub2 Documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
it says this
> If only the word "Grub" appears at the top of the screen without a prompt (access to the command line) or menu, refer to the Reinstalling from LiveCD section. under "command line & rescue mode"
I _think_ you might need this
[B][B][SIZE=2]> METHOD 2 - Copy GRUB 2 Files from the Installed Partition[/SIZE][SIZE=2] 
[/SIZE][/B][/B]

from the "re-installing" section.

---

### Post by kyeh on 2010-02-10
I followed the grub2 reinstallation and it worked! I installed it on /dev/sdb instead of /dev/sda.

Thanks for the help :popcorn:

---

### Post by audiomick on 2010-02-10
Great. Good on you!

---

### Post by Jzz5 on 2010-02-10
Sorry to interrupt in this thread, but I have a simular problem. I also have a dualboot on 2 HDD's, the first containing WinXP and the 2nd containing Ubuntu 9.10 and 10.04. Both 9.10 and 10.04 boot flawlessly, but since installing 10.04 (only yesterday), I cannot boot XP any more.

It shows the word GRUB and a blinking cursor...

Following this tread, I downloaded and ran the boot-info script, and here's the output:

> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 302288255 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 302285247 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb6 and 
                       looks at sector 302288191 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xbcc1bcc1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   976,751,999   812,905,065   f W95 Ext d (LBA)
/dev/sda5         163,846,998   976,751,999   812,905,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x000b2c74

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   594,340,739   594,340,677  83 Linux
/dev/sdb2         594,340,740   976,768,064   382,427,325   5 Extended
/dev/sdb5         957,120,633   976,768,064    19,647,432  82 Linux swap / Solaris
/dev/sdb6         594,340,866   942,324,704   347,983,839  83 Linux
/dev/sdb7         942,324,768   957,120,569    14,795,802  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EA014DEA014BE69                       ntfs                                     
/dev/sda5        EA78EDD078ED9C17                       ntfs                                     
/dev/sdb1        c1d33d1c-0f47-4ff1-a715-84a30c6296c7   ext4                                     
/dev/sdb5        fc52e245-6210-4feb-ba71-03921ad0558f   swap                                     
/dev/sdb6        e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1   ext4                                     
/dev/sdb7        3a3eeabc-2283-4001-acc6-62b2e56c514a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/windows/D         fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
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
menuentry "Ubuntu, met Linux 2.6.32-12-generic" {
        recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, met Linux 2.6.32-12-generic (herstelmodus)" {
        recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	echo	Loading Linux 2.6.32-12-generic ...
	linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, met Linux 2.6.32-10-generic" {
        recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, met Linux 2.6.32-10-generic (herstelmodus)" {
        recordfail
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	echo	Loading Linux 2.6.32-10-generic ...
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c1d33d1c-0f47-4ff1-a715-84a30c6296c7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1ea014dea014be69
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=c1d33d1c-0f47-4ff1-a715-84a30c6296c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fc52e245-6210-4feb-ba71-03921ad0558f none            swap    sw              0       0
# swap was on /dev/sdb7 during installation
UUID=3a3eeabc-2283-4001-acc6-62b2e56c514a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.32-10-generic
    .0GB: boot/initrd.img-2.6.32-12-generic
    .0GB: boot/vmlinuz-2.6.32-10-generic
    .0GB: boot/vmlinuz-2.6.32-12-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
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
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
insmod png
if background_image /usr/share/images/grub/blauwwit.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single  splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single  splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 ro single  splash
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
#	search --no-floppy --fs-uuid --set 1ea014dea014be69
	drivemap -s (hd0) ${root}
	chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> 				<mount point>   	<type>  	<options>       		   <dump>  <pass>
proc            				/proc           	proc    	defaults        		   0       0
# / was on /dev/sdb6 during installation
UUID=e093a365-cec9-4a8b-9b5b-99c6cdcd6ea1 	/               	ext4    	errors=remount-ro 		   0       1
# swap was on /dev/sdb7 during installation
UUID=3a3eeabc-2283-4001-acc6-62b2e56c514a 	none            	swap    	sw              		   0       0
/dev/sda5    					/media/windows/D   	ntfs-3g 	rw,auto,user,fmask=0111,dmask=0000 0	   0
/dev/scd0       				/media/cdrom0   	udf,iso9660 	user,noauto,exec,utf8 		   0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

I think it's not good that grub is installed on both sda and sdb, but how to solve it?

Thanks in advance for any reply's.
Jzz

edit: I see this tread is marked as Solved... I'll start a new tread then

---

