---
title: "Ubuntu on USB HDD and Windows 7"
date: 2011-05-09
forum: General Help
---

### Post by Dovelea on 2011-05-09
I am using an external bootable USB HDD with Ubuntu vers 10, this installed OK, on boot up I get the grub menu and can boot to Ubuntu or windows 7. I also used to be able to unplug USB drive and still use my laptop Acer  Aspire 5734Z as a standalone.

About a week ago did some software updates to Ubuntu, then installed Ubuntu 11, since then because 11 did not work properly on laptop I re-installed vers 10.

If I now try and use my laptop without the ubuntu drive connected, I get this error on bootup

Error: No Such Device 5d3abe9e-1f80-4afb-a7d2-3b09a8f321a2 Grub Rescue.

How can I restore my windows to boot without usb drive connected.

Many thanks for any suggestions (I am fairly good with windows BUT new to Ubuntu)

---

### Post by sanderd17 on 2011-05-09
Let me first explain the problem:

The computer starts at the MBR of the first HDD. That is a fixed point of your HDD. In you case, the MBR contains a command to start GRUB, the bootloader. When GRUB starts, it looks for it's configuration files (which are too big to fit in the MBR). By default, the configuration files are stored in /boot/grub on your linux installation.

Since you don't plug your HDD in while you boot, GRUB can't find the files he need and drops to resque prompt. 

What you need to do is reinstall grub, [s]but put the configuration files on the windows system[/s]. I'll have to search on how to do that exactly.

To know your exact configuration, it would be good to run the boot info script and post the output here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

EDIT: as the other ubuntuers said: you need to repair the mbr to point to windows and put GRUB completely on the USB disk. I was wrong.

---

### Post by wilee-nilee on 2011-05-09
> **sanderd17 said:**
> Let me first explain the problem:

The computer starts at the MBR of the first HDD. That is a fixed point of your HDD. In you case, the MBR contains a command to start GRUB, the bootloader. When GRUB starts, it looks for it's configuration files (which are too big to fit in the MBR). By default, the configuration files are stored in /boot/grub on your linux installation.

Since you don't plug your HDD in while you boot, GRUB can't find the files he need and drops to resque prompt. 

What you need to do is reinstall grub, [s]but put the configuration files on the windows system[/s]. I'll have to search on how to do that exactly.

To know your exact configuration, it would be good to run the boot info script and post the output here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

EDIT: as the other ubuntuers said: you need to repair the mbr to point to windows and put GRUB completely on the USB disk. I was wrong.

See next post, and thanks to sanderd17 for being so quick to edit.;)

---

### Post by ajgreeny on 2011-05-09
It will be easier and safer to restore the windows MBR to the internal hard disk using your windows 7 CD/DVD or whatever install medium you have.  Then using the live ubuntu CD put grub onto the external USB disk.  Make sure grub goes into **/dev/sdb**, or whatever the USB is called, and **NOT** onto a partition such as /dev/sdb1.

See section 13 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for details of restoring grub.

---

### Post by Dovelea on 2011-05-09
> **sanderd17 said:**
> Let me first explain the problem:

The computer starts at the MBR of the first HDD. That is a fixed point of your HDD. In you case, the MBR contains a command to start GRUB, the bootloader. When GRUB starts, it looks for it's configuration files (which are too big to fit in the MBR). By default, the configuration files are stored in /boot/grub on your linux installation.

Since you don't plug your HDD in while you boot, GRUB can't find the files he need and drops to resque prompt. 

What you need to do is reinstall grub, [s]but put the configuration files on the windows system[/s]. I'll have to search on how to do that exactly.

To know your exact configuration, it would be good to run the boot info script and post the output here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

EDIT: as the other ubuntuers said: you need to repair the mbr to point to windows and put GRUB completely on the USB disk. I was wrong.

Have attached results txt as requested. Thanks so far to all, will check mbr first.

---

### Post by wilee-nilee on 2011-05-09
Here is the actual script. The link in post 4 has the answers if you want specific commands and instructions let us know. Post 4 also describes what the problem is no grub in sdb it is in sda. So put grub2 in sdb and either a MS bootloader in sda, or the Linux Lilo bootloader, it boots windows. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cadc4.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 184909000 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    27,278,369    27,278,307  27 Hidden HPFS/NTFS
/dev/sda2    *     27,278,370    27,487,214       208,845   7 HPFS/NTFS
/dev/sda3          27,487,215   625,140,399   597,653,185   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 243     2,012,159     2,011,917   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56D81A92D81A710B                       ntfs       PQSERVICE                     
/dev/sda2        40341AB4341AACC2                       ntfs       SYSTEM RESERVED               
/dev/sda3        4E0C1BBE0C1B9FCF                       ntfs       Acer                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a9828eef-65cd-4478-8ee5-8fa844cfecf3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a3111928-4dac-4d2f-8be5-bab929eb6f92   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        356D-9969                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/356D-9969         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a9828eef-65cd-4478-8ee5-8fa844cfecf3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a9828eef-65cd-4478-8ee5-8fa844cfecf3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a9828eef-65cd-4478-8ee5-8fa844cfecf3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a9828eef-65cd-4478-8ee5-8fa844cfecf3 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a9828eef-65cd-4478-8ee5-8fa844cfecf3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 56d81a92d81a710b
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 40341ab4341aacc2
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9828eef-65cd-4478-8ee5-8fa844cfecf3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3111928-4dac-4d2f-8be5-bab929eb6f92 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/initrd.img-2.6.35-28-generic
  94.6GB: boot/vmlinuz-2.6.35-22-generic
  94.7GB: boot/vmlinuz-2.6.35-28-generic
    .3GB: initrd.img
    .9GB: initrd.img.old
  94.7GB: vmlinuz
  94.6GB: vmlinuz.old
```

---

### Post by Dovelea on 2011-05-10
Many thanks for identifying error, I am not very good at Ubuntu (commands etc) If I could have a little help in form of a "Quick help guide" it would be appreciated.

---

### Post by Hedgehog1 on 2011-05-10
**[SIZE="3"]Step 1 - make the internal hard drive boot into Windows only.[/SIZE]**

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-10
**[SIZE="3"]Step 2 - Load grub to boot Ubuntu on External Drive Only.[/SIZE]**

Please boot off your **[SIZE="3"]Vers 10[/SIZE]** LiveCD/LiveUSB, select 'TRY'

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**b1** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**b**
```


***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-05-10
Follow the Hedge, it is what I would do.;)

---

### Post by Dovelea on 2011-05-10
Many thanks to all especially [Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016")
Have done as you suggest but when I try commands in Ubuntu I get the following system come up

I am not sure how all the commands should be typed, where do I have to type root command etc.
Sorry, I am more windows based but learning slowly.

---

### Post by wilee-nilee on 2011-05-10
> **Dovelea said:**
> Many thanks to all especially [Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016")
Have done as you suggest but when I try commands in Ubuntu I get the following system come up

I am not sure how all the commands should be typed, where do I have to type root command etc.
Sorry, I am more windows based but learning slowly.

Your commands are run in a terminal while you are booted to the live desktop on a 10.10 live cd. As the screen shot shows you are

You have to get the commands exactly correct; the first one has a extra space no wanted in it between the /sdb1.  Looks like this in your screen shot of the terminal / sdb1.

Run them in that terminal like you were. Then you reboot to the grub menu log in to your install on the external and open a terminal there and run
sudo update-grub

---

### Post by drthompson on 2011-05-10
One other thing you might try, there a Windows freeware program call Boot Control by Neosmart.  When you load it there is a tab to restore the MBR to default.  I had the same problem, did this and it worked.  But I'm having major problems with the current ubuntu distro and this boot issue, this is definitely not ready for prime time.

---

### Post by wilee-nilee on 2011-05-10
> **drthompson said:**
> One other thing you might try, there a Windows freeware program call Boot Control by Neosmart.  When you load it there is a tab to restore the MBR to default.  I had the same problem, did this and it worked.  But I'm having major problems with the current ubuntu distro and this boot issue, this is definitely not ready for prime time.

lol, please do not post to just complain and offer a solution with no links it is bad practice.

---

### Post by Dovelea on 2011-05-12
Again many thanks for help and guidance, have followed instructions, downloaded software, done the mbr bit, bootrec etc and still same issue in Windows 7, it will not boot properly without ext usb hdd connected. I most certainly do not want to format my windows drive.

There must be some additional code that was written by Ubuntu on to bootloader in windows 7 which I have not found yet.

I will keep looking various sites for help, if I find answer I will get back here.

---

### Post by wilee-nilee on 2011-05-12
> **Dovelea said:**
> Again many thanks for help and guidance, have followed instructions, downloaded software, done the mbr bit, bootrec etc and still same issue in Windows 7, it will not boot properly without ext usb hdd connected. I most certainly do not want to format my windows drive.

There must be some additional code that was written by Ubuntu on to bootloader in windows 7 which I have not found yet.

I will keep looking various sites for help, if I find answer I will get back here.

I think there was a mistake somewhere here, run the bootscript if you still want to try.

These are standard commands we use all the time, the only difference I would use this command to reload the laptop.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
```

---

### Post by Dovelea on 2011-05-12
Many thanks for suggestion, says operation successful, rebooted and up came same error of "No such device and same reference number as previously given.

Back to searching Microsoft KB.

---

