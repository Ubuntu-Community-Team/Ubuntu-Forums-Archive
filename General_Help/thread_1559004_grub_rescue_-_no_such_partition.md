---
title: "grub rescue - no such partition"
date: 2010-08-23
forum: General Help
---

### Post by bt101 on 2010-08-23
Hi - I think I'm the 10 billionth person with this problem.

I installed 10.04.1 desktop onto a Windows XP machine.  Now my brick says:

```
No such partition
Grub rescue
```

I looked through the forums and tried booting the livecd and re-installing grub using 2 methods with no change in results:

```
mount /dev/sda5 /mnt
grub-install --root-directory=/mnt/ /dev/sda
```


```
mount *blah-blah*
grub-setup -d /media/*blah*/boot/grub /dev/sda
```

Both methods returned no errors (probably happily destroying my drive as was done in the first place).

Here is the output of fdisk:
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36732adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       11034    68146772+   7  HPFS/NTFS
/dev/sda3           11034       19453    67618817    5  Extended
/dev/sda5           11034       19176    65395712   83  Linux
/dev/sda6           19176       19453     2222080   82  Linux swap / Solaris

```

Looks normal.

Any thoughts?

Thanks.

---

### Post by wilee-nilee on 2010-08-23
Post the bootscript in my sig in code tags.

---

### Post by john newbuntu on 2010-08-23
Try booting from the grub rescue> prompt as described in:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

Essentially:
```
ls
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
set
ls /boot
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot 
```

If you are able to boot in, enter "sudo update-grub" in the terminal and "sudo grub-install /dev/sda"

---

### Post by bt101 on 2010-08-23
Thanks for the replies.  I tried the grub rescue commands first.

Right away something looks wrong.

```
ls
(hd0) (hd0,2) (hd0,1) (fd0)
```

I assume it is missing hd0,5

As soon as I get to this command, I get this:
```
insmod /boot/grub/linux.mod
error: no such partition
```

I've attached the output of the dump script (nice script).  I'm looking through the output to see if anything jumps out at me.  Of course I'm not sure if I'll spot anything.  If you see anything wrong, please let me know.

Thanks.

---

### Post by wilee-nilee on 2010-08-23
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   177,259,294   136,293,545   7 HPFS/NTFS
/dev/sda3         177,260,542   312,498,175   135,237,634   5 Extended
/dev/sda5         177,260,544   308,051,967   130,791,424  83 Linux
/dev/sda6         308,054,016   312,498,175     4,444,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        367C45E77C45A30B                       ntfs                                     
/dev/sda2        A6281F81281F5023                       ntfs       New Volume                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        662da533-74e9-4304-9e21-73b99a373477   ext4                                     
/dev/sda6        424c9549-010a-4e1a-8db4-fbcd20a2240b   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
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
search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=662da533-74e9-4304-9e21-73b99a373477 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=662da533-74e9-4304-9e21-73b99a373477 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 662da533-74e9-4304-9e21-73b99a373477
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 367c45e77c45a30b
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
UUID=662da533-74e9-4304-9e21-73b99a373477 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=424c9549-010a-4e1a-8db4-fbcd20a2240b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  95.2GB: boot/grub/core.img
 138.1GB: boot/grub/grub.cfg
  95.1GB: boot/initrd.img-2.6.32-24-generic
  95.1GB: boot/vmlinuz-2.6.32-24-generic
  95.1GB: initrd.img
  95.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  dc dc dc dc dc dc dc dc  dc dc db db db db db db  |................|
00000010  db db da d9 d9 d9 d9 d9  d9 d9 d9 d9 d9 d9 d9 d9  |................|
00000020  d9 d9 d9 d9 d9 d9 d9 d9  d9 d9 d9 d9 d9 d9 d9 d9  |................|
00000030  d9 d9 d9 d9 d9 d9 d9 d9  d9 d9 d8 d8 d8 d8 d8 d8  |................|
00000040  d8 d8 d7 d7 d7 d7 d7 d7  d7 d7 d7 d7 d7 d7 d7 d7  |................|
00000050  d7 d6 d6 d6 d6 d6 d6 d6  d6 d6 d7 d7 d7 d7 d7 d7  |................|
00000060  d7 d6 d6 d6 d6 d6 d6 d6  d6 d6 d6 d6 d6 d6 d6 d6  |................|
00000070  d6 d6 d6 d6 d6 d6 d6 d6  d6 d6 d6 d6 d6 d6 d6 d6  |................|
*
00000090  d5 d4 d4 d4 eb eb eb eb  eb eb eb eb eb eb eb eb  |................|
000000a0  eb eb eb eb eb eb eb eb  eb eb eb eb eb eb eb eb  |................|
*
000001a0  eb eb eb eb eb eb ea ea  ea ea ea ea ea ea ea ea  |................|
000001b0  ea ea ea ea ea ea ea ea  ea ea ea ea ea ea 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 cb 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  cb 07 00 d8 43 00 00 00  |............C...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```


From a live cd Karmic or later in a terminal.
```
sudo mount /dev/sda5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
reboot and run 
```
sudo update-grub
```

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I noticed you had been working in root only use sudo most of the time.

---

### Post by bt101 on 2010-08-23
I may be completely wrong (lemme know) but that looks like the same grub-install command that I tried at the top of the post.  I tried it again and same result... it just boots into grub rescue.

I assume you mean that the update-grub command must be run after the machine successfully boots into the OS and not from the grub rescue menu?  For the heck of it, I tried the command in the grub rescue menu and it just generates command-not-found.

Let me throw out something that has been buzzing in my mind... Is there still a limit to the offset from the start of the disk to where your boot partition can exist?  This boot partition is 80Gig from the start of the disk.  Tell me that this limitation was solved back when they launched Sputnik.

---

### Post by john newbuntu on 2010-08-24
Pre-sputnik BIOS :p .  What machine do you have and the BIOS version?  It does appear like the BIOS is having some kind of an LBA barrier or is unable to access the extended partition for some reason.  Yeah, ls should have shown (hd0,5).

A problem of similar nature was discussed in the following (really long) thread:
[http://ubuntuforums.org/showthread.php?t=1527177&page=6](http://ubuntuforums.org/showthread.php?t=1527177&page=6)
No solution was arrived at in the thread but oldfred (in post#53) suggested looking into the BIOS and review the BIOS settings.

---

### Post by bt101 on 2010-08-24
:popcorn:

You hit the nail on the head.
Went into the BIOS.  Wasn't expecting to see anything as this emachine BIOS has nothing for settings.  The mode for the disc was set to AUTO.  Changed it to LBA.  Again I wasn't expecting anything as AUTO has got to be the best setting eh?  Rebooted and then had to pickup my jaw from the floor when I saw the proper grub boot menu displayed.  Boots fine into either OS.

Many thanks.

Now if I could just figure out how to mark this thread as solved.

---

