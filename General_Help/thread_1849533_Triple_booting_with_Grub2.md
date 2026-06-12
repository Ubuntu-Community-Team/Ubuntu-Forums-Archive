---
title: "Triple booting with Grub2"
date: 2011-09-24
forum: General Help
---

### Post by joesquire on 2011-09-24
Hello
Currently I have 3 operating systems installed on my PC.
Windows 7, Windows XP, Ubuntu 11.04.
I have only just installed XP, and would like all of these to boot from Grub2.
Windows XP wouldnt show up in the Grub menu, so i played with MBR records and I had to restore to the original Windows boot loader, and I can only boot up Windows 7 now.

Windows 7 is on HDD 1 Partition 1
Windows XP is on HDD 1 Partition 2
Ubuntu is on HDD 2 Partition 2

So basically all I want, is grub to be able to boot up all 3 of these together.
I have ubuntu on a usb stick, but i think its just like the Live CD.

Any help appreciated, thanks!

---

### Post by wolfen69 on 2011-09-24
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by Leppie on 2011-09-24
Could you post the output of the following command:
```
sudo fdisk -l
```

---

### Post by garvinrick4 on 2011-09-24
Put in you live USB and boot into it.
open a terminal and like posted before'
```
sudo fdisk -l
```( Lower case L)

Pick out your Ubuntu Linux install:
I will use sda5 for this. [COLOR=Red]Use your own[/COLOR].
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo shutdown -h now
```Take out your USB and start er up.
Should have grub2 in the mbr (master boot record) now instead of Windows bootloader.
When boot into Ubuntu:
```
sudo update-grub 
```so as to put other operating systems in as grub menuentrys.

---

### Post by joesquire on 2011-09-25
hello, thanks for your help, that did get back my grub boot loader, but it didn't include my windows xp installation.

All in the list is
Ubuntu
Ubuntu Recovery
Memtest
Memtest
Windows 7

I am unsure why it doesn't include xp?

---

### Post by raja.genupula on 2011-09-25
Look at this link 

[http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)

all the best

---

### Post by garvinrick4 on 2011-09-25
Run this in script it is a boot_info_script so we can see what it looks like only way we
can tell.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

If you have a problem running just ask.
Download to Desktop and then extract by right clicking and choose archive manager then
run:
```
sudo bash ~/Desktop/boot_info_script.sh
```
Will put a RESULTS file on Desktop copy and paste here after pasted highlight whole
thing and hit the # sign in upper right of message box to put in a nice readable box.

---

### Post by daftlad on 2011-09-25
I use Boot Repair and it works for me,[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html)

---

### Post by oldfred on 2011-09-25
+1 on garvinrick4 suggestion on boot script. We then can give detailed help.

But the issue is Windows. It only knows how to boot from the active partition (one with boot flag). So it moves the boot files from any additional installs to the first install and boots from that. 

Explanation here, Lots of details but pictures pretty much explain it.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you were reinstalling this would work:
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

But you should be able to "repair" the XP partition and directly boot it.

---

### Post by joesquire on 2011-09-25
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   541,245,914   541,245,852   7 NTFS / exFAT / HPFS
/dev/sda2    *    541,245,915   625,137,344    83,891,430   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   204,796,619   204,794,572   7 NTFS / exFAT / HPFS
/dev/sdb2         204,797,950   586,063,871   381,265,922   5 Extended
/dev/sdb5         204,797,952   586,063,871   381,265,920  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3EE42F67E42F211F                       ntfs       Windows 7
/dev/sda2        02380CD3380CC81D                       ntfs       Windows XP
/dev/sdb1        8E628EBB628EA793                       ntfs       Linux & VHD
/dev/sdb5        163bedd3-6ba3-46a6-80f9-67f03d2e81dd   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows 7" /noexecute=optin /fastdetect /usepmtimer 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=163bedd3-6ba3-46a6-80f9-67f03d2e81dd ro splash quiet vga=786  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=163bedd3-6ba3-46a6-80f9-67f03d2e81dd ro single splash quiet vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 163bedd3-6ba3-46a6-80f9-67f03d2e81dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3EE42F67E42F211F
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 155.780570984 = 167.268114432  boot/grub/core.img                             1
 246.462032318 = 264.636592128  boot/grub/grub.cfg                             1
 100.096923828 = 107.478253568  boot/initrd.img-2.6.38-11-generic-pae          1
  99.198673248 = 106.513764352  boot/vmlinuz-2.6.38-11-generic-pae             1
 100.096923828 = 107.478253568  initrd.img                                     1
  99.198673248 = 106.513764352  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-09-25
First lets try just moving the XP boot files to the XP partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 


Run this in Ubuntu and it will find Windows XP and add it to the menu, but if it does not boot then sda2 boot sector may need updating.

sudo update-grub

---

### Post by joesquire on 2011-09-25
hi, im probably just being stupid, but how do move the files and where do i move them to etc, thanks

---

### Post by oldfred on 2011-09-25
From Ubuntu or the liveCD you should be able to mount the Windows 7 partition sda1 and then copy the XP files from that partition to the sda2 or  windows XP c: drive which in Ubuntu will be the top level or root of the XP partition.

---

### Post by joesquire on 2011-09-26
Thank you very muchhh!!! It is all sorted now.
Thanks again

---

