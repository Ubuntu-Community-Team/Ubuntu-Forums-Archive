---
title: "ubuntu partition unreadable, system reboots even before grub appears. Help!"
date: 2011-01-09
forum: General Help
---

### Post by inso_741 on 2011-01-09
Here's the story..
Last night I rebooted my desktop and it failed as in it just kept resetting after the bios post...so I changed my boot drive which gave me a "no bootable drive found" error(this confirms hdd fault)
then I booted a live cd and checked my partitions
they are as follows
sda1 - boot(ntfs)100MB
sda2 - windows(ntfs)
sda3 - swap
sda4 - ubuntu(ext4)

I tried to mount sda4 to reinstall grub
but it failed...says the partition is corrupt
sda2 has no problems and I made a backup for it
now the problem is how do I perform a disk check on sda4
and how do I get my system up and running again???
please help!!! I dont want to reinstall!!!:(

---

### Post by JDorfler on 2011-01-09
To be honest, don't know how to help you.  Did you have a power surge while your PC was plugged in.  I recommend a UPS to help negate any future surges.

---

### Post by alarme on 2011-01-09
Can you paste the ouput of:

$ sfdisk -l

---

### Post by wilee-nilee on 2011-01-09
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Lets see the what and where stuff is.

---

### Post by inso_741 on 2011-01-10
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Lets see the what and where stuff is.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   268,642,303   268,435,456   7 HPFS/NTFS
/dev/sda3         268,642,304   270,739,455     2,097,152  82 Linux swap / Solaris
/dev/sda4         270,739,456   312,580,095    41,840,640  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               ntfs                                     
/dev/sda2                                               ntfs                                     
/dev/sda3        276f1dd6-22e2-429b-bb70-db5ff9f2b345   swap                                     
/dev/sda4        9d39e350-d864-43f2-b0a3-03198570e8ba   ext3                                     
                 
============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /mnt/sda1                fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)



=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

```

---

### Post by Rubi1200 on 2011-01-10
Hi,
wilee-nilee asked me to jump in and offer some help.

From a LiveCD, run the following commands in the terminal:

```
 sudo e2fsck -C0 -p -f -v /dev/sda4
```

If this reports errors (quite likely), then run this command:

```
sudo e2fsck -f -y -v /dev/sda4
```

Reboot and see if you are back in to Ubuntu.

If not, boot the LiveCD again and re-run and post the boot script wilee-nilee asked for previously.

---

### Post by inso_741 on 2011-01-10
> **Rubi1200 said:**
> Hi,
wilee-nilee asked me to jump in and offer some help.

From a LiveCD, run the following commands in the terminal:

```
 sudo e2fsck -C0 -p -f -v /dev/sda4
```

If this reports errors (quite likely), then run this command:

```
sudo e2fsck -f -y -v /dev/sda4
```

Reboot and see if you are back in to Ubuntu.

If not, boot the LiveCD again and re-run and post the boot script wilee-nilee asked for previously.


```
bt ~ # sudo e2fsck -C0 -p -f -v /dev/sda4
e2fsck: Filesystem has unsupported feature(s) while trying to open /dev/sda4
/dev/sda4:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

bt ~ # sudo e2fsck -f -y -v /dev/sda4
e2fsck 1.39 (29-May-2006)
e2fsck: Filesystem has unsupported feature(s) while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

bt ~ #e2fsck -b 8193 /dev/sda4
e2fsck 1.39 (29-May-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```


I've rebooted but still the same problem
here's the o/p for the boot script now(its same as before)
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   268,642,303   268,435,456   7 HPFS/NTFS
/dev/sda3         268,642,304   270,739,455     2,097,152  82 Linux swap / Solaris
/dev/sda4         270,739,456   312,580,095    41,840,640  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               ntfs                                     
/dev/sda2                                               ntfs                                     
/dev/sda3        276f1dd6-22e2-429b-bb70-db5ff9f2b345   swap                                     
/dev/sda4        9d39e350-d864-43f2-b0a3-03198570e8ba   ext3                                     
                 
============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /mnt/sda1                fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)



=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file
```

Edit: Thanx for the quick response and just to let you know I'm using the live version of backtrack3(its the only one available to me now)

---

### Post by inso_741 on 2011-01-10
Alright I had to do something so I ran bootrec /fixmbr from a win install dvd which has removed grub from the 100mb sda1 partition and I can boot in to windows now...
the rest of the partitions are as before(including sda4)

---

### Post by QLee on 2011-01-10
That is a pretty old version of fsck you're using from BT3, could you try running a newer live Ubuntu CD version, maybe the CD you were intending to reinstall from if reinstalling becomes necessary. See if you get different results from running the commands Rubi1200 gave you on sda4 but using a newer version of fsck.

---

### Post by matt_symes on 2011-01-10
Hi

You could try running fsck with a different superblock as the output of fsck suggests. From a terminal type

```
sudo dumpe2fs /dev/sda4 | grep -i backup
```

to get a list of superblocks and then

fsck -b <block number> 

Here are some of mine

```
Backup superblock at 32768, Group descriptors at 32769-32771
Backup superblock at 98304, Group descriptors at 98305-98307
Backup superblock at 163840, Group descriptors at 163841-163843
Backup superblock at 229376, Group descriptors at 229377-229379
```

so i would run

```
sudo fsck -b 32768
```

Kind regards

---

### Post by QLee on 2011-01-10
We will probably find that the version of e2fsprogs in BT3 is not ext4 aware and that would be the reason that the boot info script run from it shows the sda4 as ext3 even though inso_741 in post 1 told us it was ext4.

---

### Post by inso_741 on 2011-01-10
> **QLee said:**
> That is a pretty old version of fsck you're using from BT3, could you try running a newer live Ubuntu CD version, maybe the CD you were intending to reinstall from if reinstalling becomes necessary. See if you get different results from running the commands Rubi1200 gave you on sda4 but using a newer version of fsck.
well actually I stopped using CDs since Ubuntu 7.10...USBs are less messy:P
and the latest ISOs are on the corrupt partition
this backtrack cd is all that I have, I'll have to download the ISO again to reinstall and thats what I'm trying avoid!
> **matt_symes said:**
> Hi

You could try running fsck with a different superblock as the output of fsck suggests. From a terminal type

```
sudo dumpe2fs /dev/sda4 | grep -i backup
```

to get a list of superblocks and then

fsck -b <block number> 

Here are some of mine

```
Backup superblock at 32768, Group descriptors at 32769-32771
Backup superblock at 98304, Group descriptors at 98305-98307
Backup superblock at 163840, Group descriptors at 163841-163843
Backup superblock at 229376, Group descriptors at 229377-229379
```

so i would run

```
sudo fsck -b 32768
```

Kind regards

I'll try that asap and keep you posted. Also should I d/l the ISO again or will bt3 do??

---

### Post by matt_symes on 2011-01-10
Hi

> Also should I d/l the ISO again or will bt3 do??

Download the Ubuntu ISO.

Kind regards

---

### Post by inso_741 on 2011-01-11
I got the Ubuntu 10.04 finally and ran those commands again only this time there were no errors, I could even mount the partition
so I reinstalled grub2 and rebooted but now it keeps getting stuck on a cursor after the bios post...
I booted the live usb again and made backup of everything I could...
some files gave a "you dont have permissions to access" error
but I got most of my data, the only thing left that I really care about are bookmarks that I made in firefox If get those I wont mind a reinstall. Here's the o/p as of now...
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda4
                                                                               
  206073 inodes used (15.75%)
     162 non-contiguous files (0.1%)
     296 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 161824/59
 1153003 blocks used (22.05%)
       0 bad blocks
       1 large file

  134598 regular files
   21282 directories
      59 character device files
      26 block device files
       0 fifos
     387 links
   50096 symbolic links (44092 fast symbolic links)
       3 sockets
--------
  206451 files
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9443

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       16723   134217728    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           16723       16853     1048576   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4           16853       19458    20920320   83  Linux
Partition 4 does not end on cylinder boundary.

```

---

### Post by inso_741 on 2011-01-11
And here's the o/p of the boot script
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   268,642,303   268,435,456   7 HPFS/NTFS
/dev/sda3         268,642,304   270,739,455     2,097,152  82 Linux swap / Solaris
/dev/sda4         270,739,456   312,580,095    41,840,640  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6468621A6861EAEE                       ntfs       System Reserved               
/dev/sda2        E4967C85967C5A4E                       ntfs                                     
/dev/sda3        276f1dd6-22e2-429b-bb70-db5ff9f2b345   swap                                     
/dev/sda4        9d39e350-d864-43f2-b0a3-03198570e8ba   ext4                                     


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
insmod png
if background_image /home/phcoder/Pictures/Calm.png ; then
  set color_normal=black/black
  set color_highlight=brown/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9d39e350-d864-43f2-b0a3-03198570e8ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9d39e350-d864-43f2-b0a3-03198570e8ba ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9d39e350-d864-43f2-b0a3-03198570e8ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9d39e350-d864-43f2-b0a3-03198570e8ba ro single 
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 9d39e350-d864-43f2-b0a3-03198570e8ba
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6468621a6861eaee
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=9d39e350-d864-43f2-b0a3-03198570e8ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=276f1dd6-22e2-429b-bb70-db5ff9f2b345 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 143.0GB: boot/grub/core.img
 145.5GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.35-22-generic
 141.9GB: boot/initrd.img-2.6.35-24-generic
 143.0GB: boot/vmlinuz-2.6.35-22-generic
 143.1GB: boot/vmlinuz-2.6.35-24-generic
 141.9GB: initrd.img
 143.1GB: vmlinuz


```

---

### Post by matt_symes on 2011-01-11
Hi

Your Firefox bookmarks are stored in the hidden folder in your home directory called .mozilla

That is <dot>mozilla

You can view them in nautilus by using View->Show hidden files from the nautilus menu.

I would make a backup of that before anything.

To copy files you don't have permission to access open nautilus as root.

Press ALT F2 and type 

```
gksudo nautilus
```

Kind regards

---

### Post by matt_symes on 2011-01-11
Hi

Then try to reinstall grub and update grub.

[http://www.robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd](http://www.robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd)

Kind regards

---

### Post by inso_741 on 2011-01-11
> **matt_symes said:**
> Hi

Your Firefox bookmarks are stored in the hidden folder in your home directory called .mozilla

That is <dot>mozilla

You can view them in nautilus by using View->Show hidden files from the nautilus menu.

I would make a backup of that before anything.

To copy files you don't have permission to access open nautilus as root.

Press ALT F2 and type 

```
gksudo nautilus
```

Kind regards

Well it seems you cant copy protected file/folders of a installed distro from a live session try it....
those file/folders have an X on them and can only be accessed from within the distro that to as a root user only....or am I wrong???

and I've reinstalled grub thats how I knew Its still not working 
please refer to the latest boot info script o/p  :(




EDIT: or maybe I'm wrong and those folders are corrupt....

---

### Post by inso_741 on 2011-01-11
alright If anyones interested, here's how I recovered my bookmarks:
I went deep into .mozilla (which in the /home/username) directory
and opened the latest .json file in gedit, copied all the text content(ctrl+a) and made a new file with an extension .json with the copied content
then went into firefox and imported the file through bookmark manager and guess what it worked!!! Now I dont mind a fresh install(although it'll take some time to customize everything again) but I'll wait a few more days to see if you guyz can come up with something that solves the problem...all you guyz have been very patient with me and I thank you for that...keep it up!!!

---

