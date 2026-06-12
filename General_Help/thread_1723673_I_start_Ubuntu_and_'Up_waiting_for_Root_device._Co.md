---
title: "I start Ubuntu and 'Up waiting for Root device. Common problens'"
date: 2011-04-07
forum: General Help
---

### Post by joept on 2011-04-07
Hello,

Sometimes Ubuntu doesn't work on my pc.
I start my pc and sometimes I get the follow message:
See the image: [www.myblogsite.nl/images/P070411_12.09.jpg]("http://www.myblogsite.nl/images/P070411_12.09.jpg")
See the image: [www.myblogsite.nl/images/P070411_12.10.jpg]("http://www.myblogsite.nl/images/P070411_12.10.jpg")

I have install Ubuntu 10.10 with Wubi.

I am Dutch so I hope you can understand me.
Thanks for your help.


Joep

---

### Post by Rubi1200 on 2011-04-07
Hi and welcome to the forums :-)

Hallo en welkom op het forum :-) (sorry, I couldn't resist the temptation to use Google Translate; is this an accurate translation?)

Anyway, down to business. The error you are seeing might have a number of possible causes.

To help us troubleshoot this, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

If you don't have an image, download it from here (there are also instructions on the page about how to create a LiveCD/USB)
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by tredegar on 2011-04-07
You might want to read [this thread]("http://ubuntuforums.org/showthread.php?t=1723381") which is about the same error (also a "wubi" install).

---

### Post by bcbc on 2011-04-07
Yeah /dev/**sde2** seems kind of suspect.

When you see the grub menu, hit 'c' to drop to a grub prompt, and enter: ls   (lower case LS) 

Then post back the results: (hd0) (hd0,...)

It's preferred you do the bootinfoscript that Rubi1200 suggested, but you can do this if you get stuck.


(If this only happens sometimes, then likely it's due to the presence or absence of peripheral devices. I'd say it's more likely to work when they are plugged in based on the drive).

---

### Post by joept on 2011-04-07
@Rubi1200,

It's a correct translation (nice!!)
But where can I find the option: 'Try Ubuntu without any changes'
I start Windows 7 and I put the live CD in my computer.
I get the message (in Dutch):
[www.myblogsite.nl/images/Ubuntu.png]("http://www.myblogsite.nl/images/Ubuntu.png")

In English:
[http://blogs.tech-recipes.com/shamanstears/files/2008/11/ubuntu_windows_dual_1.png](http://blogs.tech-recipes.com/shamanstears/files/2008/11/ubuntu_windows_dual_1.png)

So I have no option: 'Try Ubuntu without any changes'.

Can you help me please.


Joep

---

### Post by bcbc on 2011-04-07
You need to boot from the CD, not open it while running it in Windows. Usually there is a BIOS boot option key you can press (eg. F12) that will allow you to boot from CD/DVD.

---

### Post by Rubi1200 on 2011-04-08
As bcbc already said, you need to run this as a LiveCD.

Here are further instructions on how to do this:
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by joept on 2011-04-08
@Rubi1200,

I have Ubuntu installed with a Dual Boot (new install).
But I by accidence I have Ubuntu installed two times.
She image: [www.myblogsite.nl/images/P080411_16.21.jpg](www.myblogsite.nl/images/P080411_16.21.jpg)

How can I remove one Ubuntu?
Thank you so much for your time and effort.


Joep

---

### Post by Rubi1200 on 2011-04-08
See post #2; you can also use those instructions to run the script from within Ubuntu.

Post the results so we can see what is going on.

Thanks.

---

### Post by joept on 2011-04-08
@Rubi1200,

The results, it is a ZIP file.
You can download it from:
[www.myblogsite.nl/Desktop.zip]("http://www.myblogsite.nl/Desktop.zip")

What is the problem do you think?

EDIT:
I have change the language in English, so now can I find the option.


Joep

---

### Post by Rubi1200 on 2011-04-08
I will take a look at the results and post back a little bit later.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Schijf /dev/sde: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   607,380,399   607,378,352   7 HPFS/NTFS
/dev/sde2         807,553,022 1,250,263,039   442,710,018   5 Extended
/dev/sde5         807,553,024   995,684,351   188,131,328  83 Linux
/dev/sde6         995,686,400 1,003,741,183     8,054,784  82 Linux swap / Solaris
/dev/sde7       1,003,743,232 1,240,160,255   236,417,024  83 Linux
/dev/sde8       1,240,162,304 1,250,263,039    10,100,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sde1        36A6C12CA6C0ED85                       ntfs       Windows 7                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        a30b1fda-ae4f-4cbd-b0e8-b2b42789219d   ext4                                     
/dev/sde6        8de5c48f-1539-4234-932a-185f0d0857de   swap                                     
/dev/sde7        3b8bee77-5067-4e11-853c-838f05dc9a00   ext4                                     
/dev/sde8        3622338c-6974-4ae1-b604-46106de3583d   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 36a6c12ca6c0ed85
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7f9b7ff8-e1d0-4146-aaba-02490593b9f4
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7f9b7ff8-e1d0-4146-aaba-02490593b9f4 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7f9b7ff8-e1d0-4146-aaba-02490593b9f4
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=7f9b7ff8-e1d0-4146-aaba-02490593b9f4 ro single
    initrd /boot/initrd.img-2.6.35-28-generic-pae
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=8de5c48f-1539-4234-932a-185f0d0857de none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


 426.4GB: boot/grub/core.img
 482.4GB: boot/grub/grub.cfg
 414.2GB: boot/initrd.img-2.6.35-28-generic-pae
 426.4GB: boot/vmlinuz-2.6.35-28-generic-pae
 414.2GB: initrd.img
 426.4GB: vmlinuz

=========================== sde7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 36a6c12ca6c0ed85
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro single
    initrd /boot/initrd.img-2.6.35-28-generic-pae
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

=============================== sde7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=3622338c-6974-4ae1-b604-46106de3583d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde7: Location of files loaded by Grub: ===================


 531.2GB: boot/grub/core.img
 569.8GB: boot/grub/grub.cfg
 514.8GB: boot/initrd.img-2.6.35-28-generic-pae
 531.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 514.8GB: initrd.img
 531.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 
```

---

### Post by Rubi1200 on 2011-04-08
> **joept said:**
> @Rubi1200,

I have Ubuntu installed with a Dual Boot (new install).
But I by accidence I have Ubuntu installed two times.
She image: [www.myblogsite.nl/images/P080411_16.21.jpg]("http://www.myblogsite.nl/images/P080411_16.21.jpg")

How can I remove one Ubuntu?
Thank you so much for your time and effort.


Joep
Okay, well it seems that the install on sde7 and sde8 was the last one.

I would use GParted on the LiveCD to delete sde5 and sde6.

Make sure you don't touch the other partitions and double check before clicking the green arrow to apply the changes.

When you start GParted you will probably see a key symbol next to certain partitions. Right-click on the swap partition > Swapoff.

Then, just highlight those partitions and choose delete from the right-click context menu.

After that, there are 2 options.

1. either boot back into Ubuntu and run ```
sudo update-grub
``` to have the Windows and Ubuntu install, leaving the free space for something else (you can decide later about that)

2. once deleted, use the free space for the Ubuntu install on sde7 by moving sde7 into the space and then extending the partition to take up the remaining free space

---

### Post by joept on 2011-04-09
I'm sorry I don't understand you.
I have installed GParted, I see the key symbol.
But where can I find the option: 'Right-click on the swap partition > Swapoff.'

See image:
[www.myblogsite.nl/images/Schermafdruk.png]("http://www.myblogsite.nl/images/Schermafdruk.png")

Joep

---

### Post by joept on 2011-04-09
Okay, I can not delete number 6.
See image: [www.myblogsite.nl/images/Screenshot.png]("http://www.myblogsite.nl/images/Screenshot.png")

It is difficult.


Joep

---

### Post by Rubi1200 on 2011-04-09
On sde8 > right-click > Swapoff. That should unmount the partitions. Are you doing this from the LiveCD as I suggested?

---

### Post by joept on 2011-04-09
> **Rubi1200 said:**
> On sde8 > right-click > Swapoff. That should unmount the partitions. Are you doing this from the LiveCD as I suggested?
No I have installed from the Software Center is that wrong?

I do nothing before I have an answer. thank you :P
How can I install it from the Live CD?

Thank you so much for your effort.

Joep

---

### Post by Rubi1200 on 2011-04-09
GParted is installed by default on the LiveCD.

Go to System > Administration > GParted

If you see any partitions with the key symbol, turn them off. It is always safer to work with partitions when they are unmounted.

---

### Post by joept on 2011-04-09
I can not unmound number 7
See image: [www.myblogsite.nl/images/Screenshot-1.png](www.myblogsite.nl/images/Screenshot-1.png)

What can I do?


Joep

---

### Post by Rubi1200 on 2011-04-09
Joep,
are you working with the LiveCD or inside your Ubuntu installation?

If you restart the computer and use the LiveCD, then that partition should not be mounted.

The only thing you should have to unmount is the swap partition.

Once that is done, then you can delete the partitions you don't want.

---

### Post by joept on 2011-04-09
I have deleted 5 and 6 with the Live CD.
See image: [www.myblogsite.nl/images/Screenshot-GParted.png](www.myblogsite.nl/images/Screenshot-GParted.png)

But the code is doesn't work.
See image:
[www.myblogsite.nl/images/Screenshot-code.png](www.myblogsite.nl/images/Screenshot-code.png)


Joep

---

### Post by Rubi1200 on 2011-04-10
You need to run the update-grub command after rebooting without the CD and once you are back in the Ubuntu install again.

I think it would also be a good idea to run the boot info script again so we can see what has changed.

---

### Post by joept on 2011-04-10
Okay, the results.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   607,380,399   607,378,352   7 HPFS/NTFS
/dev/sde2         807,553,022 1,250,263,039   442,710,018   5 Extended
/dev/sde5       1,003,743,232 1,240,160,255   236,417,024  83 Linux
/dev/sde6       1,240,162,304 1,250,263,039    10,100,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        36A6C12CA6C0ED85                       ntfs       Windows 7                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        3b8bee77-5067-4e11-853c-838f05dc9a00   ext4                                     
/dev/sde6        3622338c-6974-4ae1-b604-46106de3583d   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3b8bee77-5067-4e11-853c-838f05dc9a00
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 36a6c12ca6c0ed85
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a30b1fda-ae4f-4cbd-b0e8-b2b42789219d
    linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=a30b1fda-ae4f-4cbd-b0e8-b2b42789219d ro single
    initrd /boot/initrd.img-2.6.35-28-generic-pae
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde7 during installation
UUID=3b8bee77-5067-4e11-853c-838f05dc9a00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=3622338c-6974-4ae1-b604-46106de3583d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


 531.2GB: boot/grub/core.img
 569.8GB: boot/grub/grub.cfg
 514.8GB: boot/initrd.img-2.6.35-28-generic-pae
 531.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 514.8GB: initrd.img
 531.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 
```I can only start my pc with the Live-CD.


Joep

---

### Post by Rubi1200 on 2011-04-10
Hi,
sorry for the delayed response.

Okay, this is what you need to do to fix this.

Use the LiveCD again and run these 2 commands in the terminal:

```
sudo mount /dev/sde5 /mnt 
sudo grub-install --root-directory=/mnt /dev/sde
```Reboot, taking out the CD.

Hopefully, you should be back in Ubuntu.

Then, run this command:

```
sudo update-grub
```Let us know if this works or if you need any other help.

---

### Post by joept on 2011-04-10
@Rubie1200,

Thank you very much for your help! (In Dutch: Hartelijk dank voor je hulp!)
Is there anything I can do for you?


Joep

---

### Post by Rubi1200 on 2011-04-10
It's fixed now? If yes, that's great news :D

You are more than welcome too.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by joept on 2011-04-11
Yes, it is fixed.
Thank you very much for your help!!


Joep

---

### Post by Rubi1200 on 2011-04-11
No problem, you are more than welcome :)

Enjoy!

---

