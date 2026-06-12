---
title: "System Recovery"
date: 2010-07-22
forum: General Help
---

### Post by Fir3chi3f on 2010-07-22
So I was playing around and tried installing puppy linux 5.0.1, made a new partition for it and everything /dev/sda7. But accidentally installed it onto /dev/sda6 :oops: That contained my main Ubuntu install 10.04. 

Luckily the /home directory was encrypted, so I likely didn't loose anything there, but unfortunately will not boot. The boot screen just continues to cycle and same for the recovery boot.

Is there an easy way to salvage this? Or am I left to un-encrypt the drive with a live cd, move all my stuff and reinstall Ubuntu? thanks in advance

---

### Post by Nerflander on 2010-07-22
Use your ubuntu cd to restore the grub loader.

Hope it helps!

---

### Post by varunendra on 2010-07-22
> **Nerflander said:**
> Use your ubuntu cd to restore the grub loader.

+1

And if it doesn't, please run & post the output of [Boot Info Script]("http://bootinfoscript.sourceforge.net/") (courtesy of forum member meierfra). You can use a live cd to boot into a live session & run the script there.

---

### Post by Fir3chi3f on 2010-07-22
Just gave it a go, rebooting right now.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

```

From:
[http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

---

### Post by Fir3chi3f on 2010-07-22
Grub restore is a no go, strange part is that the grub menu doesn't show the new installation of puppy on the sda7. (after the mistaken install I did install it on the correct partition that seemed to go well. Puppy files are on the partition.)

Script vomited this out: (Kidding;) )
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Puppy Linux Linux 2.4.22 [i486 
                       arch]
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   128,471,804   128,471,742   7 HPFS/NTFS
/dev/sda2         128,471,805   301,909,544   173,437,740   b W95 FAT32
/dev/sda3         301,910,014   390,716,864    88,806,851   5 Extended
/dev/sda5         386,556,093   390,716,864     4,160,772  82 Linux swap / Solaris
/dev/sda6         301,910,016   376,065,584    74,155,569  83 Linux
/dev/sda7         376,065,648   386,556,029    10,490,382  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        08A6025BA6024A20                       ntfs       SQ004409V05                   
/dev/sda2        475D-D5C9                              vfat                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b19ee307-6070-482a-830f-ea914add34b5   swap                                     
/dev/sda6        def3d026-4b33-4776-85bf-3ae3d7b5e1b5   ext4                                     
/dev/sda7        f5712bf5-2652-49ce-a4b8-94740f4f0a5c   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
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
search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=def3d026-4b33-4776-85bf-3ae3d7b5e1b5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set def3d026-4b33-4776-85bf-3ae3d7b5e1b5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 08a6025ba6024a20
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

/dev/sda6     /            ext4     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0

=================== sda6: Location of files loaded by Grub: ===================


 156.9GB: boot/grub/core.img
 157.0GB: boot/grub/grub.cfg
 157.2GB: boot/initrd.img-2.6.32-21-generic
 158.2GB: boot/initrd.img-2.6.32-22-generic
 158.4GB: boot/initrd.img-2.6.32-23-generic
 157.3GB: boot/vmlinuz
 156.9GB: boot/vmlinuz-2.6.32-21-generic
 155.5GB: boot/vmlinuz-2.6.32-22-generic
 156.3GB: boot/vmlinuz-2.6.32-23-generic
 158.4GB: initrd.img
 158.2GB: initrd.img.old
 156.3GB: vmlinuz
 155.5GB: vmlinuz.old

=============================== sda7/etc/fstab: ===============================

/dev/sda7     /            ext4     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0

=================== sda7: Location of files loaded by Grub: ===================


 195.3GB: boot/vmlinuz
```

Thanks guys, I'll keep this script around. I like it. xD

---

### Post by philinux on 2010-07-22
> **Fir3chi3f said:**
> So I was playing around and tried installing puppy linux 5.0.1, made a new partition for it and everything /dev/sda7. But accidentally installed it onto /dev/sda :oops: That contained my main Ubuntu install 10.04. 

Luckily the /home directory was encrypted, so I likely didn't loose anything there, but unfortunately will not boot. The boot screen just continues to cycle and same for the recovery boot.

Is there an easy way to salvage this? Or am I left to un-encrypt the drive with a live cd, move all my stuff and reinstall Ubuntu? thanks in advance

Is /home on it's own partition?

---

### Post by Fir3chi3f on 2010-07-22
> **philinux said:**
> Is /home on it's own partition?

Nope, /home is on /dev/sda6 with the ubuntu installation. (oops! original post had the wrong drive path, fixed it)

---

### Post by Fir3chi3f on 2010-07-22
The error I get while booting up:

```
(process:348): GLib-Warning **: getpwuid_r(): failed du to unknown user id (0)
init: hostname main process (400) terminated with status 1
init: hwclock main process (401) terminated with status 127
init: ureadahead main process (402) terminated with status 127
/bin/sh: error while loading shared libraries: libncurses.so.5: wrong ELF class: ELFCLASS32
init: mountall main process (403) terminated with status 127
/bin/sh: error while loading shared libraries: libncurses.so.5: wrong ELF class: ELFCLASS32
init: mountall post-stop process (404) terminated with status 127
```

^errors repeat as arrow keys are hit

Attempting to decrypt the /home produces one of the errors above: 
```
/bin/sh: error while loading shared libraries: libncurses.so.5: wrong ELF class: ELFCLASS32
```

Guide being followed: [http://www.linux-mag.com/id/7568/3/](http://www.linux-mag.com/id/7568/3/)

Windows Vista boots up fine (as fine as Vista gets) Any more suggestions before I nuke it? 

ps - I like figuring out this stuff <3

---

### Post by varunendra on 2010-07-23
> **Fir3chi3f said:**
> The error I get while booting up:

```
(process:348): GLib-Warning **: getpwuid_r(): failed du to unknown user id (0)
.....
.....
```
looks like an existing bug (see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279"), [here]("https://bugs.launchpad.net/ubuntu/+bug/531027") and an ongoing thread about it [here]("http://ubuntuforums.org/showthread.php?t=1443231"))

I've no idea about it :(


> **Fir3chi3f said:**
> Attempting to decrypt the /home produces one of the errors above: 
```
/bin/sh: error while loading shared libraries: libncurses.so.5: wrong ELF class: ELFCLASS32
```ps - I like figuring out this stuff <3

Seems like a 32bit & 64bit library issue as discussed [here]("http://unix.derkeiler.com/Newsgroups/comp.unix.solaris/2003-09/2225.html") *("Looks like the top binary is trying to run a 64 bit library but is getiing a 32bit library instead. ")*. Is it that your installation was 64bit and you are trying to decrypt via a 32bit live CD?

I'd also like figuring this out (I wish I could.... but... alas!!).

---

### Post by Fir3chi3f on 2010-07-24
> **varunendra said:**
> looks like an existing bug (see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279"), [here]("https://bugs.launchpad.net/ubuntu/+bug/531027") and an ongoing thread about it [here]("http://ubuntuforums.org/showthread.php?t=1443231"))

I doubt its an existing bug :lol: I pretty much just hosed the system by installing a different distro right on top of the old one. Although that thread still could provide information about what is going wrong. 

> **varunendra said:**
> Seems like a 32bit & 64bit library issue as discussed [here]("http://unix.derkeiler.com/Newsgroups/comp.unix.solaris/2003-09/2225.html") *("Looks like the top binary is trying to run a 64 bit library but is getiing a 32bit library instead. ")*. Is it that your installation was 64bit and you are trying to decrypt via a 32bit live CD?

Made my brain skip there for a sec ;) nope, using a 64bit live cd. But did get me thinkin! Puppy install was 32 and ubuntu was 64 so there is the conflict. 

Findings - kernels all looked to be ubuntu's and booting off different ones produced the same outcome. I also tried replacing the libraries mentioned in the error with those from another 64bit install - thinking was that perhaps puppy just replaced those with 32bit versions. Last note- I did end up getting the puppy install working and it was using version 1.5 (I think) of grub not 1.98 like ubuntu.

None of this has been a solution and I finally gave in and reinstalled. School is starting in a couple of weeks and my laptop is not something I need to be worrying about. 

Thanks for your help, didn't lose anything important thanks to dropbox. I'm now rebuilding a new ubuntu install, cheers

---

### Post by varunendra on 2010-07-24
Cheers for nothing being helpful!!!!!!!!
:lolflag:

---

