---
title: "Grub issues on new Natty installation"
date: 2011-06-22
forum: General Help
---

### Post by Sotanaht on 2011-06-22
Today I recieved my Asus T101MT netvertible in the mail, and after spending a few minutes playing with the touchscreen in Windows, it was time to purify the HDD (reformat to ext4 :P) and install Ubuntu 11.04.  Everything worked out great, I spent the whole day making it fully functional and customizing it to my heart's content, and then I decided it was time to install Android-x86 on it.  2.3 wouldn't boot, so I tried 2.2 and it installed right away, although it barely functioned.  When it was done installing, it redid the bootloader, and left grub with nothing but Android in its menu.lst file.  I tried multiple guides on restoring the bootloader to its original location, sda1's /boot/grub, but they all failed.  I eventually gave up, and tried adding Ubuntu to sda2's /grub/menu.lst, which failed to boot
> title Ubuntu 11.04
root (hd0,0)
kernel /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.38-8-genericI even erased android from menu.lst to see if it was some syntax error, but no.
I tried going into the grub command line and entering
> >root (hd0,0)
>kernel /boot/vmlinuz-2.6.38-8-generic
>bootBut I got "Error 15: File not found" after entering the kernel

I've probably spent the past 2 or 3 hours trying to fix this, and I'm pretty confident that I have no chance of fixing it on my own, unless of course I reinstall Ubuntu, but that's the last solution I want to use because of how much time I spent setting this thing up today.
I'm exhausted from all of this, so I'm just going to pass out now.  Any help is much appreciated.

---

### Post by wildmanne39 on 2011-06-22
> **Sotanaht said:**
> Today I recieved my Asus T101MT netvertible in the mail, and after spending a few minutes playing with the touchscreen in Windows, it was time to purify the HDD (reformat to ext4 :P) and install Ubuntu 11.04.  Everything worked out great, I spent the whole day making it fully functional and customizing it to my heart's content, and then I decided it was time to install Android-x86 on it.  2.3 wouldn't boot, so I tried 2.2 and it installed right away, although it barely functioned.  When it was done installing, it redid the bootloader, and left grub with nothing but Android in its menu.lst file.  I tried multiple guides on restoring the bootloader to its original location, sda1's /boot/grub, but they all failed.  I eventually gave up, and tried adding Ubuntu to sda2's /grub/menu.lst, which failed to boot
I even erased android from menu.lst to see if it was some syntax error, but no.
I tried going into the grub command line and entering
But I got "Error 15: File not found" after entering the kernel

I've probably spent the past 2 or 3 hours trying to fix this, and I'm pretty confident that I have no chance of fixing it on my own, unless of course I reinstall Ubuntu, but that's the last solution I want to use because of how much time I spent setting this thing up today.
I'm exhausted from all of this, so I'm just going to pass out now.  Any help is much appreciated.
Hi, I am going to give you a script to run so you can get help with this problem.
post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by garvinrick4 on 2011-06-22
Download this boot info script from this website to your Desktop and then
run these commands in a terminal (ctrl/alt/t) one at a time will put a RESULTS file on your desktop
post here so we can see where you are at and give you the fix.


[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 


rick@rick-HP:~$ cd Desktop  
 

 rick@rick-HP:~/Desktop$ ls  
 boot_info_script060.zip        
 

 rick@rick-HP:~/Desktop$ unzip boot_info_script060.zip  
 Archive:  boot_info_script060.zip  
 replace CHANGELOG? [y]es, [n]o, [A]ll, [N]one, [r]ename: n  
 replace boot_info_script.sh? [y]es, [n]o, [A]ll, [N]one, [r]ename: n  
 

 rick@rick-HP:~/Desktop$ ls  
 boot_info_script060.zip  CHANGELOG     
 boot_info_script.sh       
 

 rick@rick-HP:~/Desktop$ sudo ./boot_info_script.sh  
 [sudo] password for rick:

---

### Post by Sotanaht on 2011-06-22
Here are the results from the script
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 32784 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /menu.lst /syslinux.cfg /grub.exe /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2968640 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the E:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 2048.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   474,060,799   474,058,752  83 Linux
/dev/sda2         474,060,800   482,252,799     8,192,000  83 Linux
/dev/sda3         482,252,800   484,300,799     2,048,000  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
256 heads, 25 sectors/track, 4894 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,224    31,326,207    31,323,984   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000 MB, 2000682496 bytes
28 heads, 40 sectors/track, 3488 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048     3,905,535     3,903,488   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 10.10 i386
/dev/loop1                                              squashfs   
/dev/loop2       666d23b4-78f9-9047-84fb-bf376935e0f8   ext2       
/dev/sda1        040239e8-3095-450d-9194-0e50182fd0db   ext4       Ubuntu
/dev/sda2        a4e12d57-5212-4a7e-80ff-5b4ac740dab2   ext3       Android-x86
/dev/sda3        1a3f8f4c-69da-437e-ad22-1cda608e65d7   swap       
/dev/sdb1        9ED9-FD0A                              vfat       MULTIBOOT
/dev/sdd1        B4C3-C22B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/loop2       /media/666d23b4-78f9-9047-84fb-bf376935e0f8 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /media/B4C3-C22B         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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

### BEGIN /etc/grub.d/09_eeepc_acpi1 ###
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=040239e8-3095-450d-9194-0e50182fd0db ro   quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=040239e8-3095-450d-9194-0e50182fd0db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/09_eeepc_acpi1 ###

### BEGIN /etc/grub.d/11_eeepc_acpi2 ###
### END /etc/grub.d/11_eeepc_acpi2 ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 040239e8-3095-450d-9194-0e50182fd0db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=040239e8-3095-450d-9194-0e50182fd0db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=1a3f8f4c-69da-437e-ad22-1cda608e65d7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  80.135513306 = 86.044852224   boot/grub/core.img                             1
 104.158977509 = 111.839850496  boot/grub/grub.cfg                             1
   1.505405426 = 1.616416768    boot/initrd.img-2.6.38-8-generic               2
  80.133792877 = 86.043004928   boot/vmlinuz-2.6.38-8-generic                  1
   1.505405426 = 1.616416768    initrd.img                                     2
  80.133792877 = 86.043004928   vmlinuz                                        1

============================= sda2/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
default=0
timeout=6

title Ubuntu 11.04 Natty Narwhal
root (hd0,0)
kernel /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.38-8-generic
boot
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 226.393558502 = 243.088232448  grub/menu.lst                                  1
 226.370326996 = 243.063287808  grub/stage2                                    2

================================ sdb1/menu.lst: ================================

--------------------------------------------------------------------------------
default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
splashimage=/splash.xpm.gz
foreground=FFFFFF
background=000000

# Suggested by Erhan Sohail
title Boot First Hard Drive (HDD)
map (hd0) (hd1)
map (hd1) (hd0)
map --hook
chainloader (hd0)+1
rootnoverify (hd0)

title Restart
reboot

title Shutdown
halt

title --- Custom MultiBoot Entries ---
root

title Ubuntu 10.10 (GNOME Desktop x86)
find --set-root /ubuntu-10.10-desktop-i386.iso
map /ubuntu-10.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.10-desktop-i386.iso splash
initrd /casper/initrd.lz

title Balder DOS image (FreeDOS)
find --set-root /balder10.img
map --unsafe-boot /balder10.img (fd0)
map --hook
chainloader --force (fd0)+1
rootnoverify (fd0)

title DSL 4.4.10
find --set-root /dsl-4.4.10-initrd.iso
map /dsl-4.4.10-initrd.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

# Suggested by Ambriel
title Lubuntu 10.10 (LXDE Lightweight Desktop x86)
find --set-root /lubuntu-10.10.iso
map /lubuntu-10.10.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/lubuntu.seed boot=casper persistent iso-scan/filename=/lubuntu-10.10.iso floppy.allowed_drive_mask=0 splash
initrd /casper/initrd.lz

# Start Suggested by Erhan Sohail
title TinyCore
find --set-root /tinycore-current.iso
map /tinycore-current.iso (0xff) || map --mem /tinycore-current.iso (0xff)
map --hook
chainloader (0xff)

title SliTaz 3.0
find --set-root /slitaz-3.0.iso
map --heads=0 --sectors-per-track=0 /slitaz-3.0.iso (hd32)
map --hook
chainloader (hd32)

title Linux Mint 10
find --set-root /linuxmint-10-gnome-cd-i386.iso
map /linuxmint-10-gnome-cd-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper persistent iso-scan/filename=/linuxmint-10-gnome-cd-i386.iso floppy.allowed_drive_mask=0 splash
initrd /casper/initrd.lz
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default grub
LABEL grub
KERNEL grub.exe--------------------------------------------------------------------------------

========================= sdb1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

---

### Post by garvinrick4 on 2011-06-22
Put in a live cd and open a terminal and:
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Ubuntu does not use grub-legacy (grub) it uses grub2(grub-pc)
I do not know what is in sda2 but if empty reformat sda2 only and get rid of
all traces of grub-legacy

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Sotanaht on 2011-06-22
sda2 has android-x86 2.2 installed on it, but it's barely functional so I'll happily reformat it

---

### Post by Sotanaht on 2011-06-22
after following your instructions, I got the message
> /usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
Is that something I have to worry about?
I'm going to reboot and see if grub is working now

---

### Post by Sotanaht on 2011-06-22
Just booted into Ubuntu.  Everything appears to be in working order.  Thanks :KS

---

### Post by garvinrick4 on 2011-06-22
Glad you are up and running.
Was the instructions in post 3 easy to follow or did you use other instructions?

---

### Post by Sotanaht on 2011-06-23
> **garvinrick4 said:**
> Glad you are up and running.
Was the instructions in post 3 easy to follow or did you use other instructions?

I followed post 2's instructions, although I've actually used that script before.

---

### Post by gordintoronto on 2011-06-23
> **Sotanaht said:**
> I followed post 2's instructions, although I've actually used that script before.

Post 2 just generates information. How did you fix the problem?

---

### Post by wildmanne39 on 2011-06-23
Hi, glad you got it going, sorry I did not get back in time to help more. Please let us know if you followed the directions from the link on purge and install grub, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Sotanaht on 2011-06-24
I used post 5's commands to fix the problem

---

### Post by gordintoronto on 2011-06-24
Thanks!

---

