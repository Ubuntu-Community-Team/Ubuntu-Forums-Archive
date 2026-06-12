---
title: "issues with Grub2, extra enties, false entries"
date: 2010-06-09
forum: General Help
---

### Post by leopards on 2010-06-09
I am running 10.04 Lucid. I'm showing entries for 2.6.32.22, 2.6.32.21 and 2.6.32.20 I have double entries for 2.6.32.21 and when a tried to apt-get remove 2.6.32.20 It wasn't found! It also isn't present in synaptic to be removed! I tried a rebuild of grub, but it just put it right back the same way it was before commenting out the .20 version! I just tried to boot into the 2.6.32.20 kernel and I got a blinking cursor at the end of being warned I was going into low res! So right now Things are working, but this is weird and annoying!:confused:

---

### Post by wilee-nilee on 2010-06-09
Each one is a kernel and each one has a recovery. And just a little clue her your messing with stopping your whole system in it's tracks by not doing it correctly, that is trying to remove any.

If you run ```
sudo apt-get autoremove
``` it will take out the extras kernels. Just look at the terminal and choose y or n.

It is a good idea to keep two kernels and the recovery with them so you would have a total of 4 lines and the memory check option.

---

### Post by leopards on 2010-06-09
I do know that, what I have is four entries for the 2.6.32.21 two each of the kernel and two of the recovery! That is what is weird and the two for 2.6.32.20 are totally bogus I did a aptitude search for linux-header and the .20 one doesn't even show up!

---

### Post by leopards on 2010-06-09
Bump

---

### Post by Mark Phelps on 2010-06-09
If you don't like the answers you got, then go into Synaptic and remove the old kernels.  That will automatically run update-grub and remove the entries for the same kernels from your GRUB2 menu.

And, don't keep bumping -- it's rude!

---

### Post by leopards on 2010-06-09
> **leopards said:**
> I am running 10.04 Lucid. I'm showing entries for 2.6.32.22, 2.6.32.21 and 2.6.32.20 I have double entries for 2.6.32.21 and when a tried to apt-get remove 2.6.32.20 It wasn't found! It also isn't present in synaptic to be removed! I tried a rebuild of grub, but it just put it right back the same way it was before commenting out the .20 version! I just tried to boot into the 2.6.32.20 kernel and I got a blinking cursor at the end of being warned I was going into low res! So right now Things are working, but this is weird and annoying!:confused:
If you will look at the original post I do mention that that is not an option as 2.6.32.20 is not present in synaptic, so that I can remove it, or I would already have done it!

---

### Post by leopards on 2010-06-09
tom@tom-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
That didn't work!

---

### Post by oldfred on 2010-06-10
Post this so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by leopards on 2010-06-10
As you can see the partitioning is a bit of a mess! The Data partition was up to a couple of days ago an XP Pro dual boot which somehow got messed up and kept rebooting once it reached a usable desktop, after several futile efforts to repair it, I realized I hadn't used it in  year or so, so formatted it to EXT4 and moved all the saved pictures and stuff over there!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   143,364,059   143,363,997  83 Linux
/dev/sda2         143,364,060   192,169,529    48,805,470  83 Linux
/dev/sda3         482,319,556   488,392,064     6,072,509   5 Extended
/dev/sda5         482,319,558   488,392,064     6,072,507  82 Linux swap / Solaris
/dev/sda4         192,169,530   414,319,034   222,149,505  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e0f86265-9ffa-424f-9c68-fab9ab31bda8   ext4       Data                          
/dev/sda2        330b3e36-6a43-425d-8898-4484d7b83ef4   ext4       /                             
/dev/sda3: PTTYPE="dos" 
/dev/sda4        b62d4c87-414e-423d-b5eb-6cf08720aff9   ext4       /home                         
/dev/sda5        601a0849-ec3b-4b21-8e31-59469272fdcc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)
/dev/sda1        /media/Data              ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=b62d4c87-414e-423d-b5eb-6cf08720aff9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=601a0849-ec3b-4b21-8e31-59469272fdcc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  73.5GB: boot/grub/core.img
  84.7GB: boot/grub/grub.cfg
  79.4GB: boot/initrd.img-2.6.31-20-generic
  79.8GB: boot/initrd.img-2.6.31-21-generic
  74.6GB: boot/initrd.img-2.6.32-21-generic
  74.6GB: boot/initrd.img-2.6.32-22-generic
  77.7GB: boot/vmlinuz-2.6.31-20-generic
  78.9GB: boot/vmlinuz-2.6.31-21-generic
  74.4GB: boot/vmlinuz-2.6.32-21-generic
  74.6GB: boot/vmlinuz-2.6.32-22-generic
  74.6GB: initrd.img
  74.6GB: initrd.img.old
  74.6GB: vmlinuz
  74.4GB: vmlinuz.old
```

---

### Post by oldfred on 2010-06-10
For whatever reason the boot script also shows two kernels in two locations.

  79.8GB: boot/initrd.img-2.6.31-21-generic
  74.6GB: boot/initrd.img-2.6.32-21-generic
  78.9GB: boot/vmlinuz-2.6.31-21-generic
  74.4GB: boot/vmlinuz-2.6.32-21-generic


You should be able to uninstall from synaptic but here is a link to using command line.
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

You may want to run some updates just to be sure.
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by leopards on 2010-06-10
```
tom@tom-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@tom-desktop:~$ 

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   143,364,059   143,363,997  83 Linux
/dev/sda2         143,364,060   192,169,529    48,805,470  83 Linux
/dev/sda3         482,319,556   488,392,064     6,072,509   5 Extended
/dev/sda5         482,319,558   488,392,064     6,072,507  82 Linux swap / Solaris
/dev/sda4         192,169,530   414,319,034   222,149,505  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e0f86265-9ffa-424f-9c68-fab9ab31bda8   ext4       Data                          
/dev/sda2        330b3e36-6a43-425d-8898-4484d7b83ef4   ext4       /                             
/dev/sda3: PTTYPE="dos" 
/dev/sda4        b62d4c87-414e-423d-b5eb-6cf08720aff9   ext4       /home                         
/dev/sda5        601a0849-ec3b-4b21-8e31-59469272fdcc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 330b3e36-6a43-425d-8898-4484d7b83ef4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=330b3e36-6a43-425d-8898-4484d7b83ef4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=b62d4c87-414e-423d-b5eb-6cf08720aff9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=601a0849-ec3b-4b21-8e31-59469272fdcc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  73.5GB: boot/grub/core.img
  86.5GB: boot/grub/grub.cfg
  79.8GB: boot/initrd.img-2.6.31-21-generic
  74.6GB: boot/initrd.img-2.6.32-22-generic
  78.9GB: boot/vmlinuz-2.6.31-21-generic
  74.6GB: boot/vmlinuz-2.6.32-22-generic
  74.6GB: initrd.img.old
  74.6GB: vmlinuz.old
```

I got rid of the 2.6.31.20 by manually deleting the files from /boot, as suggested , then used synaptic to completely remove 2.6.32.22 header and image, but on reboot it was still in the grub menu and when I chose it I got an error device not found in /dev or something like that! here's the output from the grep of lnux-image
```
tom@tom-desktop:~$ dpkg -l | grep linux-image
ii  linux-image-2.6.32-22-generic         2.6.32-22.36                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                   2.6.32.22.23                                    Generic Linux kernel image
tom@tom-desktop:~$ 

```

As you can see this stuff doesn't agree! Synaptic no longer shows 2.6.31.21 as installed, but as you can see it is still there and shows in the grub menu!

---

### Post by oldfred on 2010-06-10
You do not want to delete  Linux 2.6.32-22-generic as that is the one you use to boot.

At least the results.txt on shows one copy of 31.21. Do you still see it in your /boot.

---

### Post by leopards on 2010-06-10
Yes, 31.21 shows up in the Grub menu and it is still in the /boot directory, but chosing it on bootup from the grub menu fails! I did use synaptic to unistall it completely, but it is still there! what is the down side of going sudo nautilus and manully removing the files from /boot? what other files is this going to leave behind scattered all over the place?

---

### Post by leopards on 2010-06-10
OK, I gave up and did a sudo nautilus and deleted the 31.21 files in the /boot folder and deleted the 31,20 files from root/.local/trash then sudo upadate grub and now I only have the 31.22 it's recovery and the memtest left! Feel kind of uncovered with only one kernel installed though, but we can mark this one closed unless, you know what I did is going to create problems down the road, like files leftoever in strange place I wouldn't know to look for them!

---

### Post by oldfred on 2010-06-10
Yours was the first that I ever saw double entries but I think there is another thread with a similar issue. Very strange.

As long as you can boot you should be ok. 

I still like to have multiple installs on different hard drives and now I have USB flash, a 4GB with multiple Ubuntu & repair ISOs, and I am converting my 16GB from storage to a full install. So I have multiple ways to boot if I ever have to.

---

### Post by leopards on 2010-06-10
If all else fails I have my Live CD and a separate /home partition, which saved my butt when the on-line upgrade from 9.10 to 10.04 failed and I had to do a full install! Really saved a LOT of time!

---

