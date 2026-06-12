---
title: "Boot Loader issues: Grub Rescue"
date: 2011-01-16
forum: General Help
---

### Post by whubbard on 2011-01-16
So I've done something foolish and I'm in need of some help.

I installed Ubuntu 10.10 on my external hard drive which is connected to my laptop by USB. However I didn't want to have to hit F8 whenever booting to start Linux so I just installed the boot loader on my internal hard drive that also contains my windows 7 boot loader.

So now when I turn on my laptop with the hard drive connected I am prompted by the loader and get to choose between Ubuntu or Windows 7. If I disconnect my hard drive the boot loader doesn't actually let me choose anything it just opens Grub Rescue.

So now I'm looking for one of two solutions. First is there anything I can put into grub rescue to make it load windows 7? Or is there a way to make it so that Windows 7 is back in the MBR or wherever it needs to be to load with the external disconnected.

-West

---

### Post by wilee-nilee on 2011-01-16
> **whubbard said:**
> So I've done something foolish and I'm in need of some help.

I installed Ubuntu 10.10 on my external hard drive which is connected to my laptop by USB. However I didn't want to have to hit F8 whenever booting to start Linux so I just installed the boot loader on my internal hard drive that also contains my windows 7 boot loader.

So now when I turn on my laptop with the hard drive connected I am prompted by the loader and get to choose between Ubuntu or Windows 7. If I disconnect my hard drive the boot loader doesn't actually let me choose anything it just opens Grub Rescue.

So now I'm looking for one of two solutions. First is there anything I can put into grub rescue to make it load windows 7? Or is there a way to make it so that Windows 7 is back in the MBR or wherever it needs to be to load with the external disconnected.

-West

Lets have a look do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by whubbard on 2011-01-16
Here it is. Many Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,438,655   234,438,593   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,048,578,047 1,048,576,000   7 HPFS/NTFS
/dev/sdb2       1,048,578,048 1,351,682,047   303,104,000  83 Linux
/dev/sdb3       1,351,682,048 1,771,112,447   419,430,400   7 HPFS/NTFS
/dev/sdb4       1,771,114,494 1,953,521,663   182,407,170   f W95 Ext d (LBA)
/dev/sdb5       1,771,114,496 1,953,521,663   182,407,168   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,701,863,423 1,701,861,376   7 HPFS/NTFS
/dev/sdc2       1,701,863,424 1,953,519,615   251,656,192   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50ACDC02ACDBE090                       ntfs       Operating System              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1200B48700B472F9                       ntfs       Storage 2                     
/dev/sdb2        3eaec030-a25e-43b0-a525-80551575f807   ext4                                     
/dev/sdb3        6ED0FBD5D0FBA18F                       ntfs       Spare Operating System        
/dev/sdb4: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        12881D5E881D41A1                       ntfs       Storage 1                     
/dev/sdc2        A884EAD084EAA054                       ntfs       System Backup                 
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc2        /media/System Backup     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/Storage 2         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/Spare Operating System fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Storage 1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
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
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3eaec030-a25e-43b0-a525-80551575f807 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3eaec030-a25e-43b0-a525-80551575f807 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3eaec030-a25e-43b0-a525-80551575f807 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3eaec030-a25e-43b0-a525-80551575f807 ro single 
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
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3eaec030-a25e-43b0-a525-80551575f807
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 50acdc02acdbe090
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1

=================== sdb2: Location of files loaded by Grub: ===================


 635.7GB: boot/grub/core.img
 539.2GB: boot/grub/grub.cfg
 537.6GB: boot/initrd.img-2.6.35-22-generic
 537.7GB: boot/initrd.img-2.6.35-24-generic
 635.7GB: boot/vmlinuz-2.6.35-22-generic
 635.7GB: boot/vmlinuz-2.6.35-24-generic
 537.7GB: initrd.img
 537.6GB: initrd.img.old
 635.7GB: vmlinuz
 635.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb5

00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 00 b0 02 00 00 00 00  00 50 55 41 00 00 00 00  |.........PUA....|
000000c0  00 a0 fa 7f 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde 
```

---

### Post by wilee-nilee on 2011-01-16
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

So to reload the MS bootlaoder use a W7 recovery or install disc, with the external unplugged, run the startup repair 3 times. Here is a recovery link if you don't have the media already to boot up.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Check then that it boots to W7; if so boot the 10.10 cd to the live desktop. Run these two commands with the usb drive plugged in.

sudo mount /dev/sdb2 /mnt
then
sudo grub-install --root-directory=/mnt/ /dev/sdb

Reboot to Ubuntu through the grub menu by just putting the sdb first in the bios, and run 
sudo update grub 
this will add the W7 to the grub menu. You now can just have the usb plugged in when you want and choose W7 from grub menu to boot W7 no keys pressed to boot the usb hd. Windows will boot like normal when the usb is removed.

---

### Post by garvinrick4 on 2011-01-16
#Do you have the Windows disks. If so use this:
 Looks like you have Windows 7 and Windows XP installed boot managers in sda?
Need to reinstall Windows boot manager into sda (very simple to do here is link)
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

#If do not have Windows disks use this in Ubuntu live Cd (install Cd using Try ubuntu)
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```

# Now for Ubuntu grub2 to install to sdb mbr: Using live CD.
```
sudo mount /dev/sdb2 /mnt
```
```
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```
```
sudo umount /mnt
```
Now reboot into HD of Ubuntu and
```
sudo update-grub
```

##Now should be able to boot into both Ubuntu and windows when booting off of
USB drive (sdb) first:
##Will only be able to boot Windows when booting off of internal drive (sda) first.

---

### Post by garvinrick4 on 2011-01-16
Looks like I was typing same time as Wilee-Nilee, same post as his basically.
Enjoy your Ubuntu.

---

### Post by whubbard on 2011-01-17
I owe you both a huge thank you. I couldn't get the first part Wilee-Nilee solution to work until I read in garvinrick4's that I needed to have window 7 unselected why running the 'Repair Startup' utility.

It now runs like a charm. Without the external it boots right to windows 7, with it, I'm prompted.

Thanks!

---

### Post by wilee-nilee on 2011-01-17
> **whubbard said:**
> I owe you both a huge thank you. I couldn't get the first part Wilee-Nilee solution to work until I read in garvinrick4's that I needed to have window 7 unselected why running the 'Repair Startup' utility.

It now runs like a charm. Without the external it boots right to windows 7, with it, I'm prompted.

Thanks!

Glad it worked, my posts can be confusing, thank goodness we all work together, thanks garvinrick4.:)

---

### Post by whubbard on 2011-05-20
So I've done it again!

I let Ubuntu update itself and told it too keep the same boot configuration. It decided not to listen and now I'm stuck having to plug the hard drive in if I want a choice of OS.

Without the external plugged in I go right back into Grub Rescue>. If it try to tell it to boot to windows 7 it says unknown file system.

My main issue now thought is that the Windows 7 repair disc isn't fixing it. Somehow when I run the repair start up 3 times it just continues thinking my machine would boot fine and doesn't fix the MBR.

I've tried searching around, but do any of you know how to repair the windows 7 boot from inside windows, I've got to assume it simple, just can't figure out how.

-West

---

### Post by linuxinstalledfromhdd on 2011-05-20
Maybe this might help:

[http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/](http://cinderbox.net/2011/02/01/how-to-recovery-grub2-after-borking/)

---

### Post by brasini on 2011-05-20
I've got a different question but it's still related to GRUB menu issue. I'm dual booting (windows/Ubuntu 10.10) but have locked myself out of Ubuntu. The laptop battery died and the machine switched off with a liveCD of the ubuntu 10.10 Netbook still on the desktop (was going to use on another machine). Since then every time I choose ubuntu from the GRUB menu it takes me to BusyBox instead of to the main OS that's installed on that partition.  I followed the advice of no. 5 on thread [http://ubuntuforums.org/showthread.php?t=681130](http://ubuntuforums.org/showthread.php?t=681130) and can get a list of 'possible files' (I typed c [enter], root hd0, 2 [enter], kernel / [tab]). That gives a list of possible files including: initrd.img vmlinuz cdrom / .local/initrd.img.old and vmlinuz.old. I'm guessing that the first two are what I left on the desktop when the laptop shut down and that the last two are what I need to get back into the main ubuntu OS on the partition. Even if that's right, I don't know which of the last two files I want or what commands to use to get back in. How do I get back in? Thanks

---

### Post by linuxinstalledfromhdd on 2011-05-20
If you can boot into recovery mode. If not you have you use a live USB stick or disc.

---

### Post by whubbard on 2011-05-20
I'm not sure you understand. I'm not trying to fix grub. I can boot into Linux just fine when I have my drive (with linux install) plugged in.

This issue is that when I don't have it plugged it, my computer is meant to boot into windows, but instead goes to grub rescue.

---

### Post by brasini on 2011-05-20
Thanks no.12. 

whubbard, apologies, I maybe should've started a new thread as mine is about a different boot loader question.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Something up with your master boot record for windows. It sounds like it might have been overwritten, but who knows.  If you have your original windows installation disc you should be able to boot into it to rewrite to your MBR and do a repair.  You would want to research that on google at this point, and see if that might help.

---

### Post by whubbard on 2011-05-20
I've used the Window 7 disc; but it refuses to repair the MBR. Tried using bootsect too, no help.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You would need to contact MS tech support and have them walk you through a trouble ticket to get that MBR restored.  Or you can research it on google for a while. I think I have seen it before, but it was a long time ago.

---

### Post by brasini on 2011-05-20
linuxinstalledfromHDD if you're still there, about no.11 on this thread, I can't boot in recovery mode. What kind of live usb do I need to use to bypass the automatic boot to the liveCD that's on my 10.10 desktop?

---

