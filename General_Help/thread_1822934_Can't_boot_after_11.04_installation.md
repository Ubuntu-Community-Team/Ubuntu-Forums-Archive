---
title: "Can't boot after 11.04 installation"
date: 2011-08-11
forum: General Help
---

### Post by weyland42 on 2011-08-11
I've been using Vista and SUSE on a desktop for quite a while, but having installed Ubuntu 11.04 on a netbook I thought I'd put it on the desktop as well instead of SUSE.

It installed with no apparent problems, but then the system won't boot anything. Says there's no operating system. I suppose I made a mistake with load points or something. I'm no expert.

So I rebooted from the CD and installed grub2 (AMD64). 

But [COLOR=Purple]sudo grub-install[/COLOR] / says [COLOR=Red]/usr/sbin/grub-probe: error: cannot stat 'aufs'[/COLOR]

Meanwhile the desktop PC is unusable unless booted from the CD. What can I do?

---

### Post by jramshu on 2011-08-11
Run this in terminal and paste the output.

```
sudo fdisk -l
```

---

### Post by weyland42 on 2011-08-11
> **jramshu said:**
> Run this in terminal and paste the output.

```
sudo fdisk -l
```
I can't do that, jramshu, because I've jumped the gun and started to install again. Thanks for your very quick response. (I'm posting this from the netbook.)

I got as far as this, but I don't know what mount points to use, or which device to select from the list at the bottom . . .

[IMG]http://lh4.googleusercontent.com/-q64Jr0R7jxc/TkPgS5IF6NI/AAAAAAAAEK8/Cl-bulnz4Iw/s800/%252521-P1020372.jpg[/IMG]

I'd like to install it in the smaller ext4 partition, unless you'd advise differently.

---

### Post by weyland42 on 2011-08-11
> **jramshu said:**
> Run this in terminal and paste the output.

```
sudo fdisk -l
```

OK. I've now reinstalled. Still get this message when I restart the system:

[COLOR=Red]ERROR No operating system
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER[/COLOR]

This is [COLOR=DarkOrchid][COLOR=Black]the[/COLOR] sudo fdisk -l[/COLOR] output . . .

[FONT=Courier New][COLOR=Sienna][FONT=Courier New]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10498    84317152    7  HPFS/NTFS
/dev/sda2           18863       19457     4777920    7  HPFS/NTFS
/dev/sda3   *       10499       18862    67183799+   f  W95 Ext'd (LBA)
/dev/sda5           10499       10683     1485981   82  Linux swap / Solaris
/dev/sda6           10684       13294    20972826   83  Linux
/dev/sda7           13295       18862    44724928+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

[COLOR=Black]And [/COLOR][COLOR=DarkOrchid][COLOR=Black]from[/COLOR] df[/COLOR] [COLOR=Black]. . .[/COLOR]

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    964984     74168    890816   8% /
none                    958096       668    957428   1% /dev
/dev/sr0                701742    701742         0 100% /cdrom
/dev/loop0              673664    673664         0 100% /rofs
none                    964984       100    964884   1% /dev/shm
tmpfs                   964984        12    964972   1% /tmp
none                    964984        92    964892   1% /var/run
none                    964984         4    964980   1% /var/lock
ubuntu@ubuntu:~$ 

[COLOR=Black](I tried to use a fixed-pitch font, but that got ignored.)[/COLOR]
[/FONT] [/COLOR][/FONT]

---

### Post by weyland42 on 2011-08-12
Is there no hope?

(I would dump Vista altogether if I wasn't very attached to Corel PaintShopPro, but for the moment I need it. Yes, I've tried the Gimp, but find the UI awkward.)

---

### Post by weyland42 on 2011-08-12
I tried [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Both First and Second Repairs resulted in a bootable Ubuntu, but no Vista (just a blinking cursor if Vista selected).

"[COLOR=DarkOrchid]Then try "First repair. When repair is finished, reboot and check if you  recovered access to your OSs. If not, run Boot-Repair again and try the  "Second repair" option. If both repairs did not succeed, copy-paste the URL that appeared in order to get help on Ubuntu forums.[/COLOR]"

No URL appeared, so I can't copy-paste it.

I'm beginning to despair.

---

### Post by weyland42 on 2011-08-13
Can anyone suggest another strategy to get Vista booted on this machine? I'm dead in the water without PaintShop.

---

### Post by Quackers on 2011-08-13
Grub is normally installed to the mbr of a drive - not to a partition on that drive.

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by weyland42 on 2011-08-14
> **Quackers said:**
> This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thank you, Quackers. Here it is, with the console log at the top (something about a problem with *awk*).

```
ubuntu@ubuntu:~$ cd Downloads/boot_info_script060
ubuntu@ubuntu:~/Downloads/boot_info_script060$ sudo bash boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb3 for information... 
Searching sdb4 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Downloads/boot_info_script060/".

ubuntu@ubuntu:~/Downloads/boot_info_script060$ 

_______________________________________________________________________________

                  Boot Info Script 0.60    from 17 May 2011

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

   [COLOR=Red] File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 209794018 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda1 has 164681928 sectors, but according to the info 
                       from fdisk, it has 168634303 sectors.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
[/COLOR] 
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

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

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   168,634,366   168,634,304   7 NTFS / exFAT / HPFS
/dev/sda2         303,019,920   312,575,759     9,555,840   7 NTFS / exFAT / HPFS
/dev/sda3    *    168,650,431   303,018,029   134,367,599   f W95 Extended (LBA)
/dev/sda5         168,650,433   171,622,394     2,971,962  82 Linux swap / Solaris
/dev/sda6         171,622,458   213,568,109    41,945,652  83 Linux
/dev/sda7         213,568,173   303,018,029    89,449,857  83 Linux

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   184,322,047   184,320,000   7 NTFS / exFAT / HPFS
/dev/sdb2         184,322,048   368,642,047   184,320,000   7 NTFS / exFAT / HPFS
/dev/sdb3         368,642,048   552,962,047   184,320,000   7 NTFS / exFAT / HPFS
/dev/sdb4         552,962,048   976,771,071   423,809,024   f W95 Extended (LBA)
/dev/sdb5         552,964,096   976,695,295   423,731,200   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA52BBE252BBA1B5                       ntfs       HP
/dev/sda2        2C88743C8874071C                       ntfs       Recovery
/dev/sda5        5e3338ea-2e48-453b-8744-821b5b30be08   swap       
/dev/sda6        028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b   ext4       
/dev/sda7        fa99054d-15e7-45be-99d8-23774bd599a7   ext4       
/dev/sdb1        C8DACCA3DACC8F5E                       ntfs       SEAGATE_500_1
/dev/sdb2        78F636AFF6366E0E                       ntfs       SEAGATE_500_2
/dev/sdb3        04B6BBFEB6BBEDF4                       ntfs       SEAGATE_500_3
/dev/sdb5        EE96EFB596EF7C89                       ntfs       SEAGATE_500_4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

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
search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root FA52BBE252BBA1B5
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2C88743C8874071C
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
UUID=028dcd80-a29c-4b6f-8e85-4b9cc8a95d4b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=fa99054d-15e7-45be-99d8-23774bd599a7 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5e3338ea-2e48-453b-8744-821b5b30be08 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  84.006302834 = 90.201080832   boot/grub/core.img                             1
  94.186417580 = 101.131895808  boot/grub/grub.cfg                             1
  84.445340157 = 90.672493568   boot/initrd.img-2.6.38-10-generic              2
  83.242215157 = 89.380647936   boot/initrd.img-2.6.38-8-generic               2
  83.387055397 = 89.536168960   boot/vmlinuz-2.6.38-10-generic                 1
 100.035927773 = 107.412759552  boot/vmlinuz-2.6.38-8-generic                  1
  84.445340157 = 90.672493568   initrd.img                                     2
  83.242215157 = 89.380647936   initrd.img.old                                 2
  83.387055397 = 89.536168960   vmlinuz                                        1
 100.035927773 = 107.412759552  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
I've highlighted in red something that looks bad, but I don't know how to fix it.

---

### Post by weyland42 on 2011-08-19
Anyone know how to fix the problem indicated in my previous post?

---

