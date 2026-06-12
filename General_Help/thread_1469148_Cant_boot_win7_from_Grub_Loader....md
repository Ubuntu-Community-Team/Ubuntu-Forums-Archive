---
title: "Cant boot win7 from Grub Loader..."
date: 2010-05-01
forum: General Help
---

### Post by di5co on 2010-05-01
Hi Everyone,

I run two separate HDDs one for win7 and the other for dedicated ubuntu.  I've never had a problem booting into the windows HDD from the GRUB loader screen.  However I just upgraded to 10.04 and since then I still get the option to boot which ever OS I want when I start my PC but when I select the win7 loader it goes to the black screen with the flashing cursor.  I rebooted and went into ubuntu and checked the filesystem for win7 and all the files and everything are still there, for sum reason it just wont boot....

Any suggestions on how to fix this?

Thanks!

---

### Post by di5co on 2010-05-02
Hi Everyone,

Pumping this after reading the other posts about this problem and trying a few of the workarounds I'm still having no luck....

Here is my sudo update-grub:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

I also checked synaptic to make sure only grub2 was installed:

screen shot is attached.

I also ran the "sudo fdisk -l" command and got this output:

```

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47169   378880000    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ed10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59321   476495901   83  Linux
/dev/sdb2           59322       60801    11888100    5  Extended
/dev/sdb5           59322       60801    11888068+  82  Linux swap / Solaris


```

Please note that I have two HDDs one for Ubuntu and one for Win7.  

When I was given the option to assign GRUB to the different partitions during the update to 10.04 (done through update manager NOT a disc) I selected all the partitions including the win7 HDD.

I run my business from my win7 partition so I'm concerned about logging into it again, all of the files are still there I can mount the filesystem and view everything on that HDD in Ubuntu.

THanks!

---

### Post by di5co on 2010-05-02
bump

---

### Post by wilee-nilee on 2010-05-02
post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by di5co on 2010-05-02
Sorry for the delay here is the Boot Info Script output below, I have also attached the actual text file!

Thanks!


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 275263 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 275263 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
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

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   757,762,047   757,760,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   952,991,864   952,991,802  83 Linux
/dev/sdb2         952,991,865   976,768,064    23,776,200   5 Extended
/dev/sdb5         952,991,928   976,768,064    23,776,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7EC81291C8124833                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b973ca05-371a-4556-9554-07adbd69ce9d   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cf432cd3-3809-43c5-9232-d963d3d83a84   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/7EC81291C8124833  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b973ca05-371a-4556-9554-07adbd69ce9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b973ca05-371a-4556-9554-07adbd69ce9d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=b973ca05-371a-4556-9554-07adbd69ce9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=b973ca05-371a-4556-9554-07adbd69ce9d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b973ca05-371a-4556-9554-07adbd69ce9d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7ec81291c8124833
    chainloader +1
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
UUID=b973ca05-371a-4556-9554-07adbd69ce9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cf432cd3-3809-43c5-9232-d963d3d83a84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  51.7GB: boot/grub/grub.cfg
   2.8GB: boot/initrd.img-2.6.31-21-generic
   8.7GB: boot/initrd.img-2.6.32-21-generic
   1.5GB: boot/vmlinuz-2.6.31-21-generic
 296.6GB: boot/vmlinuz-2.6.32-21-generic
   8.7GB: initrd.img
   2.8GB: initrd.img.old
 296.6GB: vmlinuz
   1.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by frantid on 2010-05-02
This is your situation, make sure you select the ntfs partition to make the repair:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3)

---

### Post by di5co on 2010-05-02
ok I tried that and it said that my boot sectors are identical... still cant boot win7 attached screen shots showing identical BS and what I get when i select Rebuild BS

---

### Post by oldfred on 2010-05-02
This is the same instructions linked by frantid and is also by meierfra. who did the post.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by frantid on 2010-05-02
> **di5co said:**
> ok I tried that and it said that my boot sectors are identical... still cant boot win7 attached screen shots showing identical BS and what I get when i select Rebuild BS

You'll have to do a fixboot with win7 dvd then.

---

### Post by itiswhatitis on 2010-05-02
Ran into the exact same issue with my friends computer.  I wrote up an article on how we fixed him up.

[http://tinyurl.com/28wvhgm](http://tinyurl.com/28wvhgm)

---

### Post by poo_22 on 2010-05-02
> **frantid said:**
> You'll have to do a fixboot with win7 dvd then.

i have the exact same problem as the opening poster. my win7 partition is intact, and i tried popping in the win7 dvd and clicking to repair system startup which said that i had no errors...

and what happens when you follow the article posted above me is you delete grub2, replace it with window's bootloader, only to have to install grub2 again. i'd rather not do that and find the cause of this problem...

---

### Post by wilee-nilee on 2010-05-02
> **poo_22 said:**
> i have the exact same problem as the opening poster. my win7 partition is intact, and i tried popping in the win7 dvd and clicking to repair system startup which said that i had no errors...

and what happens when you follow the article posted above me is you delete grub2, replace it with window's bootloader, only to have to install grub2 again. i'd rather not do that and find the cause of this problem...

In order to find the cause you need to start a thread and post the bootscript, in code tags if possible.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by itiswhatitis on 2010-05-02
When you upgraded, did you check all of the boxes on the Grub configuration.  As closely as I can understand, doing this breaks the Windows boot.

There are lots of topics here that have the same issue.  I've read many of them, as well as the Grub2 documentation.  Re-installing Grub seemed like the easiest fix.

---

### Post by oldfred on 2010-05-02
The single biggest problem is everyone is installing grub all over the place including the windows boot sector or (partition boot record) PBR which is not the drive's MBR (master boot record). Windows has essential boot files in its PBR.

itiswhatitis link does not solve the problem. I think he had to run additional repairs while in the windows repair disk. fixboot is the command in windows repair to restore the windows boot loader to the boot sector or PBR.

Testdisk works for most, I have seen many use it and the creator of the link believes the testdisk versions works better than the windows repair in many cases.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If that does not work then you have to use the windows tools.
They are different for XP or Vista/7.

---

### Post by itiswhatitis on 2010-05-02
> **oldfred said:**
> 
itiswhatitis link does not solve the problem. I think he had to run additional repairs while in the windows repair disk. fixboot is the command in windows repair to restore the windows boot loader to the boot sector or PBR.


I've followed my own instructions twice now, and got both systems up and running. 

Fix Windows so the computer boots into windows
Use the LiveCD to re-install grub to the right places
Then reboot into Ubuntu and update-grub to get the windows option back

I don't mean to sound high and mighty here, but my solution solves the problem.

Edit:  Fixboot is the XP option.  Vista and Win 7 have a different set of options.

---

