---
title: "Dual boot problems, windows 7 bootloader fails me."
date: 2011-01-15
forum: General Help
---

### Post by Patch-c on 2011-01-15
Hiya,

I recently reinstalled windows, and linux on my laptop,

N.B first time using linux (i love it), Just keep that in mind cause im nott to hot on all this. 

The  problem is with the boot, i have it set to use grub, witht he options  linux, safemode, memtest, safemode, and windows 7 bootloader.

I go into windows 7 bootloader and this gives me two choices, linux and some other linux. Not what i needed.
So now i cannot get onto my windows system.

I  googles, and was able to find all this info about repairing the windows  boot loader from windows cd, problem is my win 7 disk goes immediately  to install. And i dont have a recovery disk.

So what i really  need is a way of repairing it from ubuntu in easy terms, without the  need of a disk or the need of a windows 7 system... Directly from  ubuntu. 
ANY contribution would be greatly appreciated.

Thanks in advance.

 Pat

---

### Post by Quackers on 2011-01-15
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Patch-c on 2011-01-15
Here we go...
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

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

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 108052216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    81,919,999    81,713,152   7 HPFS/NTFS
/dev/sda3          81,920,000   112,639,999    30,720,000  83 Linux
/dev/sda4         112,640,000 1,250,263,039 1,137,623,040   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC30B35A30B32A6A                       ntfs       System Reserved               
/dev/sda2        3A42BA4D42BA0E1F                       ntfs                                     
/dev/sda3        421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37   ext4                                     
/dev/sda4        F83AAF743AAF2E96                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true

```

Thanks again for helping

---

### Post by Quackers on 2011-01-15
It seems that some of the boot script is missing. Can you copy the full file and try again please?

---

### Post by Patch-c on 2011-01-15
whoops...

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

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

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 108052216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    81,919,999    81,713,152   7 HPFS/NTFS
/dev/sda3          81,920,000   112,639,999    30,720,000  83 Linux
/dev/sda4         112,640,000 1,250,263,039 1,137,623,040   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC30B35A30B32A6A                       ntfs       System Reserved               
/dev/sda2        3A42BA4D42BA0E1F                       ntfs                                     
/dev/sda3        421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37   ext4                                     
/dev/sda4        F83AAF743AAF2E96                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37 ro  vga=792  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37 ro single  vga=792
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ac30b35a30b32a6a
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=421dd5d6-8e3d-49ef-a0bf-3b3da0da5e37 /               ext4    errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


  55.0GB: boot/grub/core.img
  48.7GB: boot/grub/grub.cfg
  42.7GB: boot/initrd.img-2.6.35-22-generic
  55.3GB: boot/vmlinuz-2.6.35-22-generic
  42.7GB: initrd.img
  55.3GB: vmlinuz

```

---

### Post by Quackers on 2011-01-15
Ok, thanks. The boot script looks good to me.
Let me just recap.
If you boot the machine you get the grub menu, which has Ubuntu, Ubuntu recovery, 2 Memtest enties, and one entry for Windows Loader on sda1. Yes?
If you select the top entry, Ubuntu boots up?
If you select the Windows entry you are getting another menu come up?

---

### Post by Patch-c on 2011-01-15
Yes,
And the windows choice from the grub menu. Goes to the windows bootloader. However the bootloader only has a choice for linux, no windows.

---

### Post by Quackers on 2011-01-15
I'm not sure where that second bootloader screen is coming from. It shouldn't be appearing. What makes you think it's a Windows bootloader?

---

### Post by Patch-c on 2011-01-15
Looking at it now.
Black and white screen, says "windows boot manager" (my bad, I should have checked that one)
It asks to choose an operating system to start.
The choices are neosmart Linux and Linux, one which returns to grub menu, the other boots ubuntu.
And beneath that is a tools section, with windows memory diagnostic.

---

### Post by Quackers on 2011-01-15
Have you have installed EasyBCD at some time?

---

### Post by Patch-c on 2011-01-15
yes.

---

### Post by Quackers on 2011-01-15
It may be worth looking at the Neosmart site for support, or their forum.
All I can think of is repairing the mbr with a Windows 7 repair disc, which you can download from here
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)
or other places, then booting up Windows and deleting EasyBCD.
Then you can re-install grub using the Ubuntu Live cd/usb.
There may be quicker ways to do it that I am unaware of.

---

### Post by Patch-c on 2011-01-15
Ill look at it now and get back to you.

**And thanks heaps. **

---

### Post by Quackers on 2011-01-15
You're welcome. Good luck!

---

### Post by Patch-c on 2011-01-15
Worked a charm.
Thank you very much.

Now to install grub...

---

### Post by Quackers on 2011-01-15
Very nice :-)
From the live cd terminal
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by Pillars of Creation on 2011-01-15
20110115-easy bcd-2

Patch-c,

You can get the Windows 7 repair disks here. This is not a direct download but a torent. We’ll need a program to get the download. I recommend Frost Wire rather than LimeWire and be careful how you configure it. By default Frost Wire acts as a server for everything you download.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)


FrostWire 4.21.3
[http://download.cnet.com/FrostWire/3000-2196_4-10627624.html?tag=mncol;1](http://download.cnet.com/FrostWire/3000-2196_4-10627624.html?tag=mncol;1)

After you repair the MBR you can boot into Windows. Once back in Windows you can start up Easy BCD. From there you can delete any existing Ubuntu entry and add a single new one.

What’s going on is you have two separate boot loaders. One is associated with GRUB-2 from Ubuntu and the other is a modified Windows boot loader from Easy BCD. Normally after the Ubuntu install the GRUB-2 boot loader comes up first with a single working option for Windows seven. I don’t know why yours didn’t work.

In any case, once you get back into Windows 7 you’re going to reverse the order of the two boot loaders. The Easy BCD boot loader will come up first. The option within it for Ubuntu will boot into the BRUB-2 boot loader.

If you wish you can edit the grub menu to set the startup time equal to zero. This way you won’t see the second menu and you will boot directly into Ubuntu

Applications, accessories, terminal. Then type sudo gedit. Click on file system, select ect, default, grub.

Change GRUB_TIMEOUT=10 TO GRUB_TIMEOUT=0

Back in terminal type “sudo update-grub” to update the GRUB-2 boot loader menu.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

