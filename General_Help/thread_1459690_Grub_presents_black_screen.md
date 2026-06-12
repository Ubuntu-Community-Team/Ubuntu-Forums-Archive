---
title: "Grub presents black screen"
date: 2010-04-21
forum: General Help
---

### Post by Facetious Falcon on 2010-04-21
Ubuntus been working fine for months now, this morning however, I switch on the computer to find a black screen with nothing on it in place of the Grub menu. If I leave it for about 5 minutes it restarts so I don't think it's a video card issue. 

I can't really be more specific and I'm not entirely sure what it is that's caused it as I haven't been messing around with anything major. My only guess is that it's either an update (I remember installing an update yesterday) or a hard disk that's failed.

I've tried holding down shift but to no avail, I've also tried reinstalling Grub 2 using the guide on the ubuntu docs but it still just boots into blackness. I also tried removing all the hard disks apart from the Ubuntu HD and then reinstalling Grub 2 but to no avail.

Any help would be greatly appreciated. Thanks!

---

### Post by 666f6f on 2010-04-21
I don't see any updates in the GRUB package but you may try to [downgrade to GRUB1]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202").

---

### Post by Facetious Falcon on 2010-04-22
Could this be a failed hard disk then? The reason I don't think it is is because all the hard disks are accessible from my the live CD without problem.

I suppose if I can't get grub to work then I'll have to reinstall but I'll need to backup some stuff. However I cannot grab some files because of permissions and the fact I'm not logged on my user account for that HD. How would I login to a user account on a specific hard disk from the live CD?

---

### Post by john newbuntu on 2010-04-22
From the liveCD, download the bootinfo script by Meierfra and post the output file RESULTS.TXT.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Facetious Falcon on 2010-04-22
Thanks John here's the results from the script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005d600

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a898a89

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de11de1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   160,055,594   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA209E55209E27F9                       ntfs       BIG ONE                       
/dev/sdb1        e59eb6e4-e3b7-4883-9766-aab24b7b7d62   ext4                                     
/dev/sdb5        eb761597-a447-48e7-a298-7b8534cc59fe   swap                                     
/dev/sdc1        2630A68430A65B17                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e59eb6e4-e3b7-4883-9766-aab24b7b7d62
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aa209e55209e27f9
	drivemap -s (hd0) ${root}
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
UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=eb761597-a447-48e7-a298-7b8534cc59fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
   6.3GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.31-14-generic
   1.6GB: boot/initrd.img-2.6.31-15-generic
   6.0GB: boot/initrd.img-2.6.31-16-generic
   1.4GB: boot/initrd.img-2.6.31-17-generic
  10.3GB: boot/initrd.img-2.6.31-19-generic
  10.8GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.4GB: boot/vmlinuz-2.6.31-15-generic
   1.8GB: boot/vmlinuz-2.6.31-16-generic
   1.3GB: boot/vmlinuz-2.6.31-17-generic
   8.1GB: boot/vmlinuz-2.6.31-19-generic
   8.6GB: boot/vmlinuz-2.6.31-20-generic
  10.8GB: initrd.img
  10.3GB: initrd.img.old
   8.6GB: vmlinuz
   8.1GB: vmlinuz.old
```

One thing I have noticed from this is that sda is essentially a storage device, it doesn't have windows on it, just files yet it is reporting boot locations however sdc is my Win XP HD and that is not reporting any boot locations. I still don't really know why this would be a problem though because, like I said, it's been working until yesterday for months.

---

### Post by klemes on 2010-04-22
```
Grub 2 is installed in the MBR of /dev/sd**b** and looks on the same drive in 
    partition #1 for /boot/grub
```

I think without being absolutely sure there is where lies your problem.
Grub shoould be installed in the MBR your first drive (sda) I think but instead it is installed in the second one (sdb)
so BIOS after POST searches in the MBR of your first drive where apparently there is no information for booting any OS so you get a black screen.
Is there a message like 'No Media Found Press any Key to Reboot' when you are booting from your hard drive?
If this is the case I think there should be such a message depending on your BIOS I think.
Did you upgraded grub recently ?maybe that's what it caused it.
Just guessing here but maybe it's enough to get you on track to somewhere...

---

### Post by john newbuntu on 2010-04-22
According to the script, sda1 contains the boot sector for windows XP, which in turn loads the OS in /dev/sdc1.  Slightly unusual for a typical XP install.  But that's ok.
Grub2, despite your last update is in the right location.  I am assuming that your BIOS is set to look at the second drive (sdb) first.

Since you get a blank screen initially, there appears to be a problem reading MBR of sdb into memory or perhaps some files are missing.  Could you run memtest from liveCD and make sure that your RAM is ok?

If that is ok too, then if you have time on your hands, try installing grub2 on sdc and change BIOS to boot from sdc first and see if that helps.

---

### Post by Facetious Falcon on 2010-04-22
Thanks for the help guys, I think you've helped me get somewhere. I've done what you said John and installed Grub onto sdc instead of sdb and now grub loads up but there's no menu, just the Grub prompt. I've tried using the boot command and it just says 'no kernel loaded'. I've tried holding down shift again but that doesn't seem to work either. Perhaps I need to enter the menu items somehow...

---

### Post by 666f6f on 2010-04-22
Normally you shouldn't have to edit the menus.. but maybe that's because you changed the boot order.

How exactly are you installing grub? (important to answer)

From within a running system, the following command should do it: ```
sudo grub-install /dev/sdXXX #You should replace XXX with a, b or c!
``` 

From the live CD you can fire up a terminal and try: ```
mkdir tmp && sudo mount /dev/sdb1 tmp && sudo grub-install /dev/sdc --root-directory=~/tmp
```

---

### Post by Facetious Falcon on 2010-04-22
To install Grub I did

```
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdc --recheck
```

Where 0d104aff... is sdc. sdc is a Windows XP HD but grub is installed onto it. Just to note there are no kernels in the boot folder thus I think this might be a problem.

---

### Post by oldfred on 2010-04-22
It seems like your drive order is all messed up. 

This from your boot.ini says windows is on drive 1
rdisk(1)partition(1)

On my system windows is in sda and it shows rdisk(0), so your windows is on sdb per boot.ini. If windows is sda you will have to edit boot.ini to rdisk(0) to get it to work.

---

### Post by 666f6f on 2010-04-22
Facetious, I'm sorry if I repeated stuff you already knew. As far as the missing kernels is concerned (cool finding), it seems other people are experiencing similar issues [http://ubuntuforums.org/showthread.php?t=1342293](http://ubuntuforums.org/showthread.php?t=1342293). Weird indeed..

---

### Post by john newbuntu on 2010-04-23
I am assuming that while re-installing grub2 from the liveCD you mounted /dev/sdb1 which is where your ubuntu partition is.  At this time, run "sudo update-grub2" and see if that helps.

If not , there might be some file is missing in your ubuntu boot partition, follow the "METHOD-3 chroot" given in:
[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)
Be very careful about the X's and Y's.

Now this whole exercise is just to make sure Ubuntu boots fine.  Later on, if it complains about windows booting, we can repair boot.ini or even re-install PBR using XP disk in recovery mode.

---

### Post by Facetious Falcon on 2010-04-23
Again thanks people, especially John however I tried the 'METHOD-3 Chroot' and it looked promising it picked up Windows XP but none of the old Ubuntu kernel images. I'm guessing this is because there's no kernel images in the /boot/ folder of sdc (because it's a fresh install of grub). I tried copying these over from the old sdb boot directory and they got picked up with update-grub but when I rebooted and chose them from the menu it said something to the effect 'error: partition not found'. Are the kernels supposed to automatically be copied over with update-grub?

I'm going to try and trawl through the grub docs to get a better understanding of how it all works see if that sheds some light on the situation but I'm fairly sure that the issue started because the mbr of sdb became corrupted/a bad sector.

---

### Post by john newbuntu on 2010-04-23
I thought your boot sector was still /dev/sdb1 and that you have moved only grub2 to the mbr of /dev/sdc.  This is the reason why I asked if you had mounted /dev/sdb1 which has both the boot and root partition of ubuntu. /dev/sdc is not supposed to have a boot folder.  Its sole purpose is for the mbr to be used.

update-grub only updates the file grub.cfg that is located in your boot partition.  It does the OS scan among other things.  

Can you give one more try to restore grub2 to mbr to sdc and correct the grub2 files:
Insert liveCD and reboot computer. Open terminal
```
   
   sudo mkdir /mnt
   sudo mount /dev/sdb1 /mnt
   sudo mount --bind /dev /mnt/dev
  sudo mount --bind /proc /mnt/proc
   sudo mount --bind /sys  /mnt/sys
  sudo mount --bind /usr/ /mnt/usr
   sudo chroot /mnt
   sudo update-grub
   sudo grub-install --root-directory=/mnt /dev/sdc --recheck
   sudo umount /mnt/dev
   sudo umount /mnt/proc
   sudo umount /mnt/sys
   sudo umount /mnt/usr
   sudo umount /mnt

```
   Now reboot and finally after logging in to linux:
   sudo update-grub2

---

### Post by gawadelnil2002 on 2010-04-23
did anybody notice insmod=ext2 in grub.cfg while his root partition formated ext4.
I started thread about that hoping some one can explane
[http://ubuntuforums.org/showthread.php?t=1460756](http://ubuntuforums.org/showthread.php?t=1460756)

---

### Post by Facetious Falcon on 2010-04-23
I understand a bit better now - grub is now installed on sdc's mbr whilst the root directory is on my sdb I've set sdc to run first from bios when this is done grub just hangs at 'Grub loading' I waited 10 minutes to see if it would generate any error messages but it doesn't. Perhaps it's to do with the kernels that's it's loading...

---

### Post by john newbuntu on 2010-04-23
If you do not find grub loading complete (it should not take that long), check the consistency of your ext* filesystem by running the following from a liveCD without mounting any partitions:
```

 sudo e2fsck -C0 -p -f -v /dev/sdb1
```If this gives any errors, then run:
```
sudo e2fsck -f -y -v /dev/sdb1
```

---

### Post by Facetious Falcon on 2010-04-23
This is what the command gave me, looks ok to me:

```
 296625 inodes used (12.66%)
     348 non-contiguous files (0.1%)
     240 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 268369/104/1
 1899280 blocks used (20.30%)
       0 bad blocks
       1 large file

  222905 regular files
   38625 directories
      68 character device files
      26 block device files
       2 fifos
     394 links
   34950 symbolic links (28005 fast symbolic links)
      40 sockets
--------
  297010 files
```

I have a sata drive, would that effect anything?

---

### Post by john newbuntu on 2010-04-23
fsck output looks good to me.

Now try booting normally and if it hangs again, hold the shift key at boot and follow the "editing menus during boot section" in this post to see if you are able to diagnose anything:
[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot")

You could also try dropping to a command line (if possible) by typing "c" if you get to the menu.

---

### Post by Facetious Falcon on 2010-04-23
I've noticed that when it says grub loading if I wait a bit it says 'Error: no such disk' or something similar

---

### Post by Facetious Falcon on 2010-04-23
I thought I figured it out when I realised device.map contained an entry for fd0 which I think is the floppy disk, I don't have a floppy drive on my computer. I deleted the fd0 line and ran grub-install without the --recheck parameter but it still didn't work. Still just says 'no such disk' but I don't know what disk it cannot find.

---

### Post by oldfred on 2010-04-23
Review the options here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

meierfra suggests removing the search line.

---

### Post by Facetious Falcon on 2010-04-24
The problem is it won't even get to the menu, only the rescue prompt. Even when I hold shift down whilst it's loading.

I've now reinstalled ubuntu again having backed everything up but the problems still there which means my computer's still unusable.

---

### Post by john newbuntu on 2010-04-24
This time when you re-installed, which partition did you choose for grub?  If I remember, it is an option that is asked somewhere towards the end of the installation.  By default, it writes to the mbr of /dev/sda I think.  I am not a 100% sure.  Can you also post the output of bootinfo script please?

---

### Post by Facetious Falcon on 2010-04-24
I think I left it at the default which was hd0 so sda. Here's the script output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=db317395-fe73-452f-bace-44324e13e07b)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for 
    (UUID=e59eb6e4-e3b7-4883-9766-aab24b7b7d62)/mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005d600

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a898a89

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    74,862,899    74,862,837  83 Linux
/dev/sdb2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sdb5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de11de1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   160,055,594   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA209E55209E27F9                       ntfs       BIG ONE                       
/dev/sdb1        db317395-fe73-452f-bace-44324e13e07b   ext4                                     
/dev/sdb5        eb761597-a447-48e7-a298-7b8534cc59fe   swap                                     
/dev/sdc1        2630A68430A65B17                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set db317395-fe73-452f-bace-44324e13e07b
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
	search --no-floppy --fs-uuid --set db317395-fe73-452f-bace-44324e13e07b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=db317395-fe73-452f-bace-44324e13e07b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set db317395-fe73-452f-bace-44324e13e07b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=db317395-fe73-452f-bace-44324e13e07b ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aa209e55209e27f9
	drivemap -s (hd0) ${root}
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
UUID=db317395-fe73-452f-bace-44324e13e07b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=eb761597-a447-48e7-a298-7b8534cc59fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: initrd.img
    .6GB: vmlinuz

```

---

### Post by john newbuntu on 2010-04-24
Now in the bios, use sda as the first drive to boot from and reboot.

---

### Post by Facetious Falcon on 2010-04-24
Already tried that unfortunately. It still just stops at grub loading then after a while it says 'error: no such disk'. Strangely annoying.

---

### Post by john newbuntu on 2010-04-24
Can you get to mount /dev/sdb from a liveCD and see what is in /boot/grub/device.map?
cat /boot/grub/device.map

Edit: after it says no such disk, is it giving you a rescue prompt?

---

### Post by Facetious Falcon on 2010-04-24
> **john newbuntu said:**
> Can you get to mount /dev/sdb from a liveCD and see what is in /boot/grub/device.map?
cat /boot/grub/device.map

Edit: after it says no such disk, is it giving you a rescue prompt?

From the device.map I've got:

```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

Yep it's giving me a rescue prompt but I have no idea what commands are allowed from the rescue prompt and I don't know what I'm able to do from there.

---

### Post by john newbuntu on 2010-04-24
Ah, we can do these from the rescue prompt: Run steps 1 through 9
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

basically your  (hdX, Y) is (hd1, 1) in steps 2 and 3.
and sdx,y is sdb1 in step 7.
Once you boot in, run "sudo update-grub2" immediately.

---

### Post by Facetious Falcon on 2010-04-24
I think we're getting somewhere now. I did the first 3 commands ok but when I did 'ls /boot/' it says 'no such partition' and then again when I tried to do 'insmod /boot/grub/linux.mod'

---

### Post by john newbuntu on 2010-04-24
At grub rescue prompt, when you run:
ls -l (hd1,1)/
can you see the /boot directory?
if not try ls -l (hd0,1)
although this would be surprising


Then set root below accordingly and run:

```
set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro quiet splash
initrd /initrd.img
boot

```

---

### Post by Facetious Falcon on 2010-04-24
For some reason every time I run the ls command on all the partitions it just says 'no such partition'. Say when I do ls -l (hd1,1) it just says no such partition.

Incidentally when I do ls to list the HDs the list is produced very slowly, maybe this could be a hardware issue?

---

### Post by john newbuntu on 2010-04-24
Hmm.  Never seen that before.  'ls' or 'ls (hd1,1) should get results immediately.  

You could try to boot from sda (first drive) in bios and see if that helps.  Basically repeat all the steps you did in your previous post(#33).
I need to logoff now. I'll check back in another 10 hours or so.

---

