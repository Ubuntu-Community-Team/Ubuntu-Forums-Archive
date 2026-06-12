---
title: "No grub loader on startup"
date: 2010-10-18
forum: General Help
---

### Post by pwnmonkey on 2010-10-18
Hey guys,
I just recently installed Ubuntu 10.10 and upon restart there was no grub loader.
On occasion I will catch a glimpse of what seems to be the boon menu but even then it only display Windows 7. 
How can I get to it?
I'm certain this is a dumb question with a ridiculously simple answer but i'm stumped..

thanks in advance!
-Devan

---

### Post by Quackers on 2010-10-18
Try holding down the shift key during boot.

---

### Post by pwnmonkey on 2010-10-18
> Try holding down the shift key during boot.
I tried that, nothing happened it just booted to Win7

---

### Post by Quackers on 2010-10-18
How did you install Ubuntu? CD or USB?

---

### Post by sikander3786 on 2010-10-18
If you've got a single HDD, you can try reinstalling Grub as per instructions here.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have Windows and Ubuntu on separate HDDs, you can try changing the boot device from Bios to the one containing Ubuntu (in case you installed Grub to the MBR of same drive).

If you are unsure, please post the output of bootinfoscript so we have a better idea of your situation.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Don't forget to wrap your output with proper code tags #.

---

### Post by Legeril on 2010-10-18
I have a similar issue, I am only running Ubuntu 10.04 no Windoze at all. And it just boots straight in, not that this is a massive issue to me but should I see the GRUB screen? I did when I had dual-boot. But since removing Windoze re-partitioning and installing I get nothing =/

---

### Post by Quackers on 2010-10-18
If Ubuntu is the only installed OS the default behaviour is to not show a grub menu. If you want to see it you can hold the shift key during boot.

---

### Post by sikander3786 on 2010-10-18
As **Quackers** mentioned, you need to use the Shift key to see it.

If you want to see it everytime you boot your computer, instead of editing the files and running all those commands, you can use StartUp Manager to set the default time out.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by Legeril on 2010-10-18
OK thanks guys, I don't think I'll be needed to see it as I prefer a faster loading time. I can find the kernels (to delete) by searching "Linux-image" in Synaptic Systems Manager right? And they are ordered Newest at the top and oldest at the bottom?

---

### Post by Quackers on 2010-10-18
Or that can be done in ubuntu-tweak. It is advisable to leave at least one extra kernel in the list as well as the one you currently use for trouble-shooting reasons.

---

### Post by pwnmonkey on 2010-10-18
> **Quackers said:**
> How did you install Ubuntu? CD or USB?

10.10 with the CD

---

### Post by Quackers on 2010-10-18
Ok, boot from your Ubuntu CD and when the GUI comes up, select "try Ubuntu". Once you've got an internet connection go to the link below and download the boot script to your desktop then in a terminal run the command given on that page. This will produce a Results.txt file on your desktop. Copy the contents of that file and paste them into your next post using CODE tags (Click New Reply then click on the # symbol in the tool bar and paste the results between the two code tags).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pwnmonkey on 2010-10-18
I'll give that a try when i get home, thanks!

---

### Post by pwnmonkey on 2010-10-18
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,131,629,791 1,131,422,944   7 HPFS/NTFS
/dev/sda3       1,131,630,590 1,250,263,039   118,632,450   5 Extended
/dev/sda5       1,250,076,672 1,250,263,039       186,368  82 Linux swap / Solaris
/dev/sda6       1,131,630,592 1,250,074,623   118,444,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F45608A4560869A6                       ntfs       System Reserved               
/dev/sda2        EA5409FA5409C9F1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        abfbaba9-ea49-4faf-ac4b-cb6ffc4299ff   swap                                     
/dev/sda6        a64c9844-c645-4b5c-9ac3-7a7a4b223de8   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/a64c9844-c645-4b5c-9ac3-7a7a4b223de8 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a64c9844-c645-4b5c-9ac3-7a7a4b223de8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a64c9844-c645-4b5c-9ac3-7a7a4b223de8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set a64c9844-c645-4b5c-9ac3-7a7a4b223de8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f45608a4560869a6
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a64c9844-c645-4b5c-9ac3-7a7a4b223de8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=abfbaba9-ea49-4faf-ac4b-cb6ffc4299ff none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 603.1GB: boot/grub/core.img
 583.8GB: boot/grub/grub.cfg
 580.2GB: boot/initrd.img-2.6.35-22-generic
 603.1GB: boot/vmlinuz-2.6.35-22-generic
 580.2GB: initrd.img
 603.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```Here you are, that's a really large file though, is that what you needed?

---

### Post by drs305 on 2010-10-18
Grub isn't installed in the MBR so it never gets run.

To put Grub into the MBR and point to your Ubuntu installation on sda6, from the Live CD Desktop, open a terminal (Applications, Accessories, Terminal).

Run these commands:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you use the partition in the first command, but only the drive designation in the second.

When you reboot, it will boot directly into Ubuntu if it didn't see Windows initially, or show both if it didn't. If it boots directly into Ubuntu, run the following command after the boot so it will put Windows into the menu:
```
sudo update-grub
```

---

### Post by pwnmonkey on 2010-10-18
That worked! Thanks so much everyone that helped. Again, sorry if it was a stupid question.

Another thing: is it normal to have so many partitions? I know windows 7 uses 2 for its system reserve but does Ubuntu use 3?

---

### Post by Quackers on 2010-10-18
Nice result :-)
On your system Linux is really using 2 partitions (sda5 & sda6) but they are both within the extended partition (sda3).

---

### Post by pwnmonkey on 2010-10-18
> On your system Linux is really using 2 partitions (sda5 & sda6) but they are both within the extended partition (sda3).
Ah, thanks for clearing that up

---

