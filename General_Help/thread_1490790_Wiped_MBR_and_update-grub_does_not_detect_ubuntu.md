---
title: "Wiped MBR and update-grub does not detect ubuntu"
date: 2010-05-22
forum: General Help
---

### Post by Manbeardo on 2010-05-22
I was having some issues with GRUB2, so I decided (stupidly) to wipe out /boot on my ubuntu drive and run update-grub and grub-install.

After running these and rebooting, I found that my Ubuntu install wasn't listed in GRUB's menu.

I've been playing around with a live CD to attempt to fix the problem, but I don't know the technical details necessary to manually add an entry for my Ubuntu install.

Any ideas?

---

### Post by dcstar on 2010-05-22
> **Manbeardo said:**
> I was having some issues with GRUB2, so I decided (stupidly) to wipe out the MBR on my ubuntu drive and run update-grub and grub-install.

After running these and rebooting, I found that my Ubuntu install wasn't listed in GRUB's menu.

I've been playing around with a live CD to attempt to fix the problem, but I don't know the technical details necessary to manually add an entry for my Ubuntu install.

Any ideas?

The MBR is only on the first 446 bytes of the boot sector, if you "wiped" more than that then you also wiped the partition table.

---

### Post by Manbeardo on 2010-05-22
I guess I didn't "wipe the MBR"; I ran:

```
rm /boot/*
rm -r /boot/grub
```

---

### Post by Manbeardo on 2010-05-22
Shameless bump.  I've been able to mount and navigate my Ubuntu install from the live CD, but GRUB doesn't automatically detect the Ubuntu install when I run update-grub.

---

### Post by wilee-nilee on 2010-05-23
Post this script in code tags. To post in code tags highlight the script readout in the reply and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please be sure to post in the code tags as it is very hard to read otherwise.

---

### Post by dcstar on 2010-05-23
> **Manbeardo said:**
> I guess I didn't "wipe the MBR"; I ran:

```
rm /boot/*
rm -r /boot/grub
```

Then copy those folders from the Live CD back into the place you deleted them from.

---

### Post by Manbeardo on 2010-05-24
Copied /boot from the live CD and ran update-grub; still does not find my ubuntu install.

Ran the boot script within my live CD environment and got this:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   156,299,263   156,092,416   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   468,519,659   468,519,597  83 Linux
/dev/sdb2         468,519,660   488,392,064    19,872,405   5 Extended
/dev/sdb5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        922E061E2E05FBCB                       ntfs       System Reserved               
/dev/sda2        981608851608669A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c93683d5-0d51-4538-9207-5e5d18ef4825   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        997656fc-ca1c-40cf-8b8b-4623e3d779f5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/c93683d5-0d51-4538-9207-5e5d18ef4825 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)


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
search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
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
search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 922e061e2e05fbcb
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
UUID=c93683d5-0d51-4538-9207-5e5d18ef4825 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=997656fc-ca1c-40cf-8b8b-4623e3d779f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/core.img
  28.0GB: boot/grub/grub.cfg
```

---

### Post by wilee-nilee on 2010-05-24
Have you tried booting from sdb by using the key prompt to chose the booting drive mines f12 or changing the boot order in bios so sdb is read first. Also when you boot are you getting grub or the windows bootloader?

---

### Post by Manbeardo on 2010-05-24
Boot from USB is my system's default. It boots to grub, but the only entry in the grub menu is memtest. (I ran update-grub again after running the script and there is no longer an entry for Windows 7 in grub.cfg)

---

### Post by wilee-nilee on 2010-05-24
> **Manbeardo said:**
> Boot from USB is my system's default. It boots to grub, but the only entry in the grub menu is memtest. (I ran update-grub again after running the script and there is no longer an entry for Windows 7 in grub.cfg)

So a little information will be helpful what is the usb device? Also did you have a working install of windows before you installed into the usb device. And how did you run update grub if you can't get into Ubuntu to start with. Were you able to get to the Ubuntu recovery and a command line and you left out this information.

In other words you need to give a more lowdown on the system the devices and what and what you haven't been able to do, also now that you have done a additional fix after posting the script you will have to post it again. 

Do you see that doing additional repairs after posting the script, and leaving information out that is pertinent will keep anybody from helping you. Take a breath post the script again, do not run any repairs and wait for help.

You should only be running update-grub from the installed system not the live cd.

So also confirm what is installed to the usb device and is it sda or sdb.

---

### Post by amanthethy on 2010-05-24
Just a question for the OP. Did you run "update-grub" after chroot-ing into your Ubuntu installation from teh live cd? If not, give that a try. 

```
sudo mkdir /media/a
sudo mount /dev/*name_of_your_drive* /media/a (ex. sudo mount /dev/sda4 /media/a)
sudo chroot /media/a
sudo update-grub

```

---

### Post by Manbeardo on 2010-05-24
My set-up is a Dell laptop and I use three hard drives:

[LIST=1]
[*]An internal SSD that only has Windows 7 installed on it.
[*]An HDD in a USB enclosure that only has Ubuntu installed on it.
[*]An HDD in a USB enclosure that is used for storage.
[/LIST]
My current boot order defaults to USB so that I can run Ubuntu when my laptop is sitting at a desk and I can run Windows when I'm elsewhere.

When I attempt to boot into Ubuntu, hard drive 2 (Ubuntu) is plugged in and hard drive 3 (storage) is unplugged.

When I boot the machine this way, I get the GRUB2 menu, but the only menu entry is memtest.

If I unplug both external drives or use F12 to boot from the internal drive, Windows boots without any problem.

I have successfully booted an Ubuntu live CD and mounted hard drive 2 and have been able to run update-grub and grub-install (and all files on the drive are fine).

When I run update-grub, it only detects memtest and does not find the Windows 7 and Ubuntu installs that exist.

After running the boot script again (while chroot'd into the Ubuntu install on drive 2), this is what it returned:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   156,299,263   156,092,416   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   468,519,659   468,519,597  83 Linux
/dev/sdb2         468,519,660   488,392,064    19,872,405   5 Extended
/dev/sdb5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        922E061E2E05FBCB                       ntfs       System Reserved               
/dev/sda2        981608851608669A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c93683d5-0d51-4538-9207-5e5d18ef4825   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        997656fc-ca1c-40cf-8b8b-4623e3d779f5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
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
search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c93683d5-0d51-4538-9207-5e5d18ef4825
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=c93683d5-0d51-4538-9207-5e5d18ef4825 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=997656fc-ca1c-40cf-8b8b-4623e3d779f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
  28.0GB: boot/grub/grub.cfg
```

---

### Post by wilee-nilee on 2010-05-24
> **amanthethy said:**
> Just a question for the OP. Did you run "update-grub" after chroot-ing into your Ubuntu installation from teh live cd? If not, give that a try. 

```
sudo mkdir /media/a
sudo mount /dev/*name_of_your_drive* /media/a (ex. sudo mount /dev/sda4 /media/a)
sudo chroot /media/a
sudo update-grub

```

Do you think this is a wise thing to do when we have a user running commands after posting the script? and not getting more information.

---

### Post by Manbeardo on 2010-05-24
> **amanthethy said:**
> Just a question for the OP. Did you run "update-grub" after chroot-ing into your Ubuntu installation from teh live cd? If not, give that a try. 

```
sudo mkdir /media/a
sudo mount /dev/*name_of_your_drive* /media/a (ex. sudo mount /dev/sda4 /media/a)
sudo chroot /media/a
sudo update-grub

```

I've already done this, and you actually left out a few important commands. In order for update-grub to work, you need to bind /dev and /proc; so it would look like:

```
sudo mount /dev/*name_of_your_drive* /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
sudo update-grub

```

---

### Post by perham on 2010-05-24
you obviously have deleted all your kernels along with their stuff. either get them from somewhere (ubuntu repositories should have them), or do a clean install.

[http://packages.ubuntu.com/lucid/linux-image](http://packages.ubuntu.com/lucid/linux-image)
[http://packages.ubuntu.com/lucid/linux-headers-generic](http://packages.ubuntu.com/lucid/linux-headers-generic)

download the packages, boot with livecd, chroot into your system, manually install these packages, boot into your system, then reinstall grub.

---

### Post by wilee-nilee on 2010-05-24
I wonder if the grub in sdb is corrupted and just needs to be reloaded and mounted.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
step 11 without chrooting in, just from the live cd

---

### Post by Manbeardo on 2010-05-24
> **wilee-nilee said:**
> I wonder if the grub in sdb is corrupted and just needs to be reloaded and mounted.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
step 11 without chrooting in, just from the live cd

Step 11? The only step 11 I see in that section is instructions on exiting chroot.

---

### Post by wilee-nilee on 2010-05-24
> **perham said:**
> you obviously have deleted all your kernels along with their stuff. either get them from somewhere (ubuntu repositories should have them), or do a clean install.

[http://packages.ubuntu.com/lucid/linux-image](http://packages.ubuntu.com/lucid/linux-image)
[http://packages.ubuntu.com/lucid/linux-headers-generic](http://packages.ubuntu.com/lucid/linux-headers-generic)

download the packages, boot with livecd, chroot into your system, manually install these packages, boot into your system, then reinstall grub.

I think you are correct there was never a kernel listed even in the 1st script.

---

### Post by dcstar on 2010-05-24
> **amanthethy said:**
> Just a question for the OP. Did you run "update-grub" after chroot-ing into your Ubuntu installation from teh live cd? 
........

Please note that for any chroot from a Live CD boot to work, the Live CD must match the system architecture you are trying to chroot to - for example a 32-bit Live CD cannot chroot to a 64-bit system.

You can waste a lot of time if you have the wrong Live CD just lying around....:confused:

---

### Post by Manbeardo on 2010-05-24
> **perham said:**
> you obviously have deleted all your kernels along with their stuff. either get them from somewhere (ubuntu repositories should have them), or do a clean install.

[http://packages.ubuntu.com/lucid/linux-image](http://packages.ubuntu.com/lucid/linux-image)
[http://packages.ubuntu.com/lucid/linux-headers-generic](http://packages.ubuntu.com/lucid/linux-headers-generic)

download the packages, boot with livecd, chroot into your system, manually install these packages, boot into your system, then reinstall grub.

Okay. I ran synaptic from my chroot'd terminal and I am installing these packages. How do I go about booting into my system if GRUB isn't working? (also, does opening synaptic from the chroot cause the packages to be installed in the mounted drive or do I need to specify the location manually?)

---

### Post by fela on 2010-05-24
Yes, all the kernels are stored in /boot, as well as the grub files. So you need to boot a livecd, chroot into your system, and install a kernel. Then run update-grub and it *should* find it. If it doesn't, I'd just do a reinstall as it might be less hassle (unless you *like* spending ages sorting out avoidable problems...) You've learned your lesson now I guess though :)

EDIT: just thought of something. You must have deleted your whole grub installation when deleting /boot. You need to reinstall that too. Don't know how :(

---

### Post by Manbeardo on 2010-05-24
Hrmmm. Synaptic is giving me an error:
```
Error failed to fork pty
```

---

### Post by fela on 2010-05-24
> **Manbeardo said:**
> Hrmmm. Synaptic is giving me an error:
```
Error failed to fork pty
```

Why don't you use apt-get? Unless that's a deeper issue...what happens when you use apt-get from the command line?

---

### Post by Manbeardo on 2010-05-24
I was using synaptic for the convenience of having a UI. I now installed the packages using apt-get, and the error:
```
Can not write log, openpty() failed (/dev/pts not mounted?)

```
Occurred multiple times during installation.

Before chroot'ing, I ran:
```
sudo mount /dev/sdb /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
```

Also, the live CD I'm using is the same as the installed distro.

---

### Post by Manbeardo on 2010-05-24
I ran update-grub again and it detected the Ubuntu install this time, but still didn't list Windows. I'll report back after I reboot.

---

### Post by fela on 2010-05-24
Hmm...maybe there's something wrong with the windows installation now...

---

### Post by Manbeardo on 2010-05-24
Restarted machine. Ubuntu booted perfectly. Upon logging in, I ran update-grub again and it detected Windows and Ubuntu this time around. Ran grub-install to commit the changes.

Everything is in working order, thanks for the help!

---

### Post by wilee-nilee on 2010-05-24
> **Manbeardo said:**
> Restarted machine. Ubuntu booted perfectly. Upon logging in, I ran update-grub again and it detected Windows and Ubuntu this time around. Ran grub-install to commit the changes.

Everything is in working order, thanks for the help!

Thank goodness for others who notice what we=me have missed, sorry for not noticing the lack of kernels in the script.;) Thanks perham and fela.

---

### Post by perham on 2010-05-24
> **Manbeardo said:**
> Restarted machine. Ubuntu booted perfectly. Upon logging in, I ran update-grub again and it detected Windows and Ubuntu this time around. Ran grub-install to commit the changes.

Everything is in working order, thanks for the help!

glad that your problem is solved. just don't do that again! lol "rm -rf (anything)" is really a bad idea in an up-to-date linux distro like ubuntu. there's always some tool to sort out such problems other than entering commands by hand.

---

### Post by perham on 2010-05-24
> **wilee-nilee said:**
> Thank goodness for others who notice what we=me have missed, sorry for not noticing the lack of kernels in the script.;) Thanks perham and fela.

happens to everyone. the spirit of helping others is the real important thing. ;)

---

### Post by fela on 2010-05-24
> **perham said:**
> glad that your problem is solved. just don't do that again! lol "rm -rf (anything)" is really a bad idea in an up-to-date linux distro like ubuntu. there's always some tool to sort out such problems other than entering commands by hand.

Please let me correct that to up to date **desktop** linux distro.

Anyways glad it got sorted :)

---

