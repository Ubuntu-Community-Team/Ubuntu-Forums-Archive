---
title: "Please help me: I just killed my /home"
date: 2011-02-18
forum: General Help
---

### Post by jarreboum on 2011-02-18
Dear all,

I made a big, big mistake, in a single sudo command line.
I wanted to do this
[http://forum.eeeuser.com/viewtopic.php?pid=350208#p350208](http://forum.eeeuser.com/viewtopic.php?pid=350208#p350208)
(last message on the page)
I think myself as a computer literate person and I understood fairly well what I was doing. But in an off-guard moment I copy-pasted the commands and forgot to change my hdd number.

To keep it short, i did 
```
$ sudo sfdisk --change-id /dev/sda 2 ef
```
Where sda2 is my /home partition (ext4).

The Bootbooster was activated, so it has written something on it on the following boot. According to some people in this forum, "it looks like there's a 200byte header, then a snapshot of the ram on the system after post)." The bootbooster's partition is no more than 8MB.

I discovered my mistake when Ubuntu would not find /home.

I then booted back on my Ubuntu USB key and changed the id of sda2 to 83 again.
Alas it seems I was too late. Gparted only finds an "unknown" partition for sda2.

I don't know what to do, I really hope my data is still here.



Please help me.

---

### Post by oldfred on 2011-02-18
Post this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

You may have created new UUIDs?

---

### Post by jarreboum on 2011-02-18
> **oldfred said:**
> Post this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

You may have created new UUIDs?

Here you go. I hope we can find some info in it.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 16.0 Go, 16013942784 octets
255 têtes, 63 secteurs/piste, 1946 cylindres, total 31277232 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    12,578,894    12,578,832  83 Linux
/dev/sda2          12,578,895    31,246,424    18,667,530  83 Linux
/dev/sda4          31,246,425    31,262,489        16,065  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 16.1 Go, 16139354112 octets
255 têtes, 63 secteurs/piste, 1962 cylindres, total 31522176 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,519,529    31,519,467  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ecdcada7-6a41-3542-83cd-02f4aa82b927   ext2       casper-rw                     
/dev/sda1        2b2ae464-7d4a-487a-a0f9-4fc4782f9e68   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bd124f98-50fe-41c8-8ac5-d35f1996fef3   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         FC3F-BF29                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/Internet Everywh  iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/bd124f98-50fe-41c8-8ac5-d35f1996fef3 ext3       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
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
search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=2b2ae464-7d4a-487a-a0f9-4fc4782f9e68 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-29-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
	echo	'Chargement de Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=2b2ae464-7d4a-487a-a0f9-4fc4782f9e68 ro single 
	echo	'Chargement du disque mémoire initial ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b2ae464-7d4a-487a-a0f9-4fc4782f9e68
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
UUID=2b2ae464-7d4a-487a-a0f9-4fc4782f9e68 /               ext3    errors=remount-ro 0       1
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)
UUID=2ed08217-1735-4925-8e4c-d9337adf1643   /home    ext4          nodev,nosuid       0       2

=================== sda1: Location of files loaded by Grub: ===================


   1.2GB: boot/grub/core.img
   1.3GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.32-29-generic
   1.5GB: boot/vmlinuz-2.6.32-29-generic
   2.1GB: initrd.img
   1.5GB: vmlinuz
```

---

### Post by jarreboum on 2011-02-18
Because I didn't mention it: I'm using Ubuntu 10.04, and the partition was ext4.

the general helping guide to recover lost partition is to use fsck. Would it be good for my specific case? or would it just aggravate the problem?

I'm not touching anything before someone tells me to.

---

### Post by jarreboum on 2011-02-19
Oh my, I'm already on page 6 after just one night.

I hope the bump is allowed here, because I still need your help.

---

### Post by jarreboum on 2011-02-19
My partition has been restaured with the help of fsck.

As some data have been written at the begining of the partition, i'm expecting some strange behaviour or maybe one ore two corrupted files. But otherwise, everything else is back.

---

### Post by oldfred on 2011-02-19
Glad you got it working.

I was off for the evening, but would have suggested e2fsck as the first thing to try. That is supposed to solve problems, not create more.

If all you did was the partition type changed, all your data should be ok. That change would write into the partition table and should not have changed data unless other restructuring was done. Did you get the correct UUID into fstab? It would not mount if it was changed, but I do not know if it would have changed or not.

---

### Post by jarreboum on 2011-02-19
The UUID wasn't changed, once the partition has been restored it got back its old UUID.

What I was afraid of is that some data writing happened at boot and was unsure wether fsck could retrieve the right information to repair the partition.

It seems silly now I'm relieved but my greatest fear was to make things worse by trying stuff i was unsure of.

Thank you anyway.

---

