---
title: "Can't access Windows 7"
date: 2011-07-09
forum: General Help
---

### Post by Porl91 on 2011-07-09
I've got quite a big problem with my computer. I'll try and explain in as much detail as I can. I have a HP netbook with Windows 7 on it and I wanted to dual boot it with Ubuntu, so I downloaded Ubuntu 11.04 to a disk, booted up using it, then once I was on I installed it. I think I'm using this menu called grub when my computer turns on, which I use to select which operating system to run. I can select Ubuntu and it works with no problems, but when I select Windows 7 it goes to the loading screen and then gives out an error, stating that there's either been a hardware or software change.

I'm quite distressed by this at the moment, because I'm really in the wilderness about it as I'm completely new to dual booting and Ubuntu and would greatly appreciate any help anyone can give me.

Thanks in advance,
Paul

---

### Post by Porl91 on 2011-07-09
Just to add a bit more information, which I think might be a source or a product of the problem, whenever I (in Ubuntu) attempt to shut down there's a loud internal beep, the page glitches and then a black screen with quite a long error message appears. Then the computer turns off before I'm able to read it.

---

### Post by Wim Sturkenboom on 2011-07-09
Boot into 11.04 and open up a terminal (I don't know where to find it in 11.04)

In the terminal, run the command (you can copy the below)
```

sudo fdisk -l

```
It will ask you for your password and spit out some information. Using the mouse you can select the output, use 'copy' in one of the terminal menus and paste the output here (preferably between [noparse]```
 and 
```[/noparse]).

It will show us which partitions are on your system.

How did you install? Did you shrink a partition and allow Ubuntu to use the free space? Or ...

HP laptops seems to use 4 primary partitions (at least nowadays) and you might have wiped something.

---

### Post by Porl91 on 2011-07-09
Thanks for the quick response. I just created a partition through Windows by shrinking my C drive. I'll run that command, one min.

---

### Post by Porl91 on 2011-07-09
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf26b837d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       51368   412402688   42  SFS
/dev/sda4           51368       60802    75777025    5  Extended
/dev/sda5           51368       52364     7999488   82  Linux swap / Solaris
/dev/sda6           52364       60802    67776512   83  Linux

```

---

### Post by wildmanne39 on 2011-07-09
> **Porl91 said:**
> Thanks for the quick response. I just created a partition through Windows by shrinking my C drive. I'll run that command, one min.
Hi, for people to help you we need this information. Post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Porl91 on 2011-07-09
Thanks, here it is:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   825,214,975   824,805,376  42 SFS
/dev/sda4         825,217,022   976,771,071   151,554,050   5 Extended
/dev/sda5         825,217,024   841,215,999    15,998,976  82 Linux swap / Solaris
/dev/sda6         841,218,048   976,771,071   135,553,024  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        0A3C76A33C768989                       ntfs       SYSTEM
/dev/sda3        9A128DC1128DA2BD                       ntfs       
/dev/sda5        bbc84565-b641-4ab3-9ac5-6f06d7aa1984   swap       
/dev/sda6        be6a6762-c800-47a1-9ac1-29e647722c83   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /mnt/clean/sda2          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /mnt/clean/sda3          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=be6a6762-c800-47a1-9ac1-29e647722c83 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=be6a6762-c800-47a1-9ac1-29e647722c83 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root be6a6762-c800-47a1-9ac1-29e647722c83
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0A3C76A33C768989
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 9A128DC1128DA2BD
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=be6a6762-c800-47a1-9ac1-29e647722c83 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 439.306854248 = 471.702142976  boot/grub/core.img                             1
 433.503311157 = 465.470636032  boot/grub/grub.cfg                             1
 403.162948608 = 432.892919808  boot/initrd.img-2.6.38-8-generic               2
 439.305545807 = 471.700738048  boot/vmlinuz-2.6.38-8-generic                  1
 403.162948608 = 432.892919808  initrd.img                                     2
 439.305545807 = 471.700738048  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by Porl91 on 2011-07-09
I've read in a few places now that using the Windows 7 disc to perform a repair is a possible fix, although I don't have the Windows 7 installation discs as the place I bought my computer from didn't provide any, so I'm a bit stuck on that one. If anyone knows of perhaps of any other methods of fixing this problem I'd really appreciate it if you helped me out.

---

### Post by goldshirt9 on 2011-07-09
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
that will give you a legitimate recovery disc to repair W 7.
as for the rest i have no idea.
Wait for someone to advise you, ref you above posted info.

they may have a easier / better  solution .
Don't do anything until someone of more experience advises you of what to do ,
 as you may only make things worse ;)

---

### Post by Porl91 on 2011-07-09
Ah, I didn't know you could download it. Thanks! I'll give this a go and report back.

---

### Post by wildmanne39 on 2011-07-09
Hi, after you get windows fixed you will most likely not be able to boot ubuntu, you will have to use an ubuntu livecd to reinstall grub, then you should be good to go just do not install grub into the mbr for windows. Here is some link to help.
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Porl91 on 2011-07-09
Thanks for your reply. I've just tried to use the windows 7 recovery start up fix, but it didn't seem to work. I don't really see where the problems are coming from which is the frustrating thing.

---

### Post by Porl91 on 2011-07-09
When I attempt to load the start up recovery it asks me to select an operating system from the list, although there are no options in the list. Then it asks me to click a button to load drivers for my hard disk, although I'm not sure where they are on Windows. It just opens a file prompt at the windows directory on my c:\ drive.

---

### Post by Porl91 on 2011-07-09
The problem I'm having with this Windows 7 startup repair is that when I boot up using it, I get to a screen where it asks me to select my operating system from a list of options, although there are no options in the box. Here's where I get stuck:

[http://help.artaro.eu/index.php/windows-7/troubleshooting-windows-7/repair-your-computer-in-windows-7.html](http://help.artaro.eu/index.php/windows-7/troubleshooting-windows-7/repair-your-computer-in-windows-7.html)

In the window that's headered "System Security Options"
On that guide it tells me to enter my Windows 7 service pack disks, although as I've said I was never given them. :[

Does anyone know a way around this?

---

### Post by wildmanne39 on 2011-07-09
> **Porl91 said:**
> The problem I'm having with this Windows 7 startup repair is that when I boot up using it, I get to a screen where it asks me to select my operating system from a list of options, although there are no options in the box. Here's where I get stuck:

[http://help.artaro.eu/index.php/windows-7/troubleshooting-windows-7/repair-your-computer-in-windows-7.html](http://help.artaro.eu/index.php/windows-7/troubleshooting-windows-7/repair-your-computer-in-windows-7.html)

In the window that's headered "System Security Options"
On that guide it tells me to enter my Windows 7 service pack disks, although as I've said I was never given them. :[

Does anyone know a way around this?
Hi, if you have an hp you are suppose to make your own recovery disk, possibly the same for some other brands as well. I do not know how you can fix it with out them. I have read that you can contact hp and they will send you the recovery disks.

---

