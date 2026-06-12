---
title: "Cannot get into XP after installing 10.10"
date: 2010-10-25
forum: General Help
---

### Post by dalzell99 on 2010-10-25
I installed Ubuntu 10.10 alongside Windows XP today. When I restart the computer it doesn't let me choose what to load so I can't access XP anymore. It just loads Ubuntu 10.10. Please help.

---

### Post by sikander3786 on 2010-10-25
Are you sure the Windows partition is still there? Please post the output of,

```
sudo fdisk -l
```

And if it lists your Windows XP drive, also this one,

```
sudo update-grub
```

---

### Post by dalzell99 on 2010-10-25
the terminal won't let me type in my password. Is there something I have to do to enter it.

---

### Post by sikander3786 on 2010-10-25
It won't show up on the screen in form of any asterisks, just type and hit Enter.

---

### Post by dalzell99 on 2010-10-25
I just wasn't typing fast enough.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000a5bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 749.5 GB, 749452918784 bytes
255 heads, 63 sectors/track, 91115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006add4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91116   731886592    7  HPFS/NTFS




Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by sikander3786 on 2010-10-25
Is this where Windows was installed?

```
/dev/sdb1 1 91116 731886592 7 HPFS/NTFS
```

Grub is not seeing the Windows at all. Please post the output of bootinfoscript as per instructions here. Wrap the text with proper code tags #.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by jroa on 2010-10-25
If you have access to another computer, you might want to try a GAG boot disk.  When you boot with a GAG CD, do not select save and it will let you boot into Windows without affecting you boot partition.

---

### Post by dalzell99 on 2010-10-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 749.5 GB, 749452918784 bytes
255 heads, 63 sectors/track, 91115 cylinders, total 1463775232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,463,775,231 1,463,773,184   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ed873a37-fa56-47e5-acdc-625825612831   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        efb2a689-c386-4f88-a4d8-ad986a2f7675   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        92DC5A9CDC5A7A85                       ntfs       My Book                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/WD SmartWare      udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ed873a37-fa56-47e5-acdc-625825612831 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ed873a37-fa56-47e5-acdc-625825612831 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ed873a37-fa56-47e5-acdc-625825612831
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=efb2a689-c386-4f88-a4d8-ad986a2f7675 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  81.7GB: boot/grub/core.img
  64.6GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  81.7GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  81.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e8 4d 01 00 17 83 c4 10  85 c0 75 0f 3b 00 07 02  |.M........u.;...|
00000010  27 98 03 3e 01 e8 81 71  ff 77 08 10 e8 65 80 30  |'..>...q.w...e.0|
00000020  8b f0 85 f6 50 59 59 74  31 85 09 cc 80 09 8b 04  |....PYYt1.......|
00000030  46 04 00 35 59 74 07 50  e8 00 98 e1 ff ff 59 8b  |F..5Yt.P......Y.|
00000040  46 08 0b 40 53 40 03 8a  41 03 56 e8 59 5c 03 00  |F..@S@..A.V.Y\..|
00000050  41 42 2b 53 8b 5d 08 57  83 8a c3 03 2c 16 81 13  |AB+S.].W....,...|
00000060  f8 85 ff 80 13 80 47 ff  75 08 57 e8 52 40 21 45  |......G.u.W.R@!E|
00000070  c2 1e 77 00 15 57 e8 df  02 25 14 21 00 25 09 57  |..w..W...%.!.%.W|
00000080  e8 00 80 73 59 eb 00 1f  6a 01 8d 45 08 50 57 24  |...sY...j..E.PW$|
00000090  e8 cb c0 06 8b 45 c0 12  c0 40 0a 50 01 3f ea c2  |.....E...@.P.?..|
000000a0  79 18 5f 5b 5d 40 c3 53  8b 5c 24 0c 01 a1 0c 31  |y._[]@.S.\$....1|
000000b0  c0 12 10 e8 b0 c0 12 42  27 16 39 00 18 75 12 57  |.......B'.9..u.W|
000000c0  53 8b fe e8 22 2b 00 93  53 e8 6d 40 01 59 59 9d  |S..."+..S.m@.YY.|
000000d0  44 74 04 80 a6 83 ab 80  71 44 24 83 03 25 c1 a7  |Dt......qD$..%..|
000000e0  59 01 59 56 57 c0 27 33  ff 03 82 49 02 40 74 41  |Y.YVW.'3...I.@tA|
000000f0  83 7d 10 00 00 76 08 39  75 10 73 03 8b 00 75 10  |.}...v.9u.s...u.|
00000100  83 7d 0c 00 74 06 00 56  ff 75 0c eb 1a 8d 04 02  |.}..t..V.u......|
00000110  b5 c2 a5 ff 75 14 e8 de  5a 4b 01 ac 82 38 0d 02  |....u...ZK...8..|
00000120  11 e8 12 02 35 0c 20 8b  c7 5f 5e 5d 81 16 53 56  |....5. .._^]..SV|
00000130  26 8b 80 3e 80 7f 33 db  84 cb 75 0c 15 01 34 f9  |&..>..3...u...4.|
00000140  00 34 8b 81 ba 85 ff 74  20 1a 57 e8 e6 de 40 2b  |.4.....t .W...@+|
00000150  75 18 81 c0 14 ff 75 10  57 e8 68 40 03 19 40 ce  |u.....u.W.h@..@.|
00000160  8b d8 c2 8d c2 29 5f 5e  8b 86 c3 40 3f 81 84 57  |.....)_^...@?..W|
00000170  8b 7d 0c 01 4a 1a fc 00  4a a2 80 78 00 ba 75 fc  |.}..J...J..x..u.|
00000180  89 80 45 0c e8 b4 db ff  ff 80 0d 29 41 2b 75 1f  |..E........)A+u.|
00000190  80 68 1b 00 1f 10 8d 00  4d 0c 51 ff 36 50 e8 32  |.h......M.Q.6P.2|
000001a0  06 64 c2 bc 80 05 03 89  7e 04 5e 84 5f c9 81 27  |.d......~.^._..'|
000001b0  51 51 8b 45 00 53 01 84  28 ff 89 45 f8 89 00 fe  |QQ.E.S..(..E....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```The Windows Partition has about 90 Gb and the Ubuntu one has 50Gb.

---

### Post by dalzell99 on 2010-10-25
I've worked out what's wrong. Windows XP is being recognised so the Grub menu didn't show up because it thinks there is only 1 operating system (Ubuntu 10.10). Now i need help getting the system to recognise that XP is present.

---

### Post by SirBlain on 2010-10-25
Wouldn't removing and reinstalling grub let you reconfigure it? That's what I did for every fresh install if it didn't pick up Windows right away!

---

### Post by dalzell99 on 2010-10-25
I reinstalled Grub using this guide ([http://ubuntuforums.org/showthread.php?t=1014708]("http://http://ubuntuforums.org/showthread.php?t=1014708")) but it didn't work. It just won't recognise windows xp.

---

### Post by sikander3786 on 2010-10-25
Seems like boot files for Windows are no more there. First of all you'll need to restore Winodws boot loader and then reinstall Grub. Have you got a Windows disc?

If yes, boot into Windows disc and follow the instructions for Windows XP bootloader here.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once you've successfully fixed Windows bootloader, you'll be able to boot into Windows but not Ubuntu at this stage. For that, you need to reinstall Grub as per instructions here. Use method 1.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Good Luck.

---

### Post by dalzell99 on 2010-10-25
That didn't work. I can't access either OS now. When I restart it comes up with "NTLDR is missing".

---

### Post by sikander3786 on 2010-10-25
> **dalzell99 said:**
> That didn't work. I can't access either OS now. When I restart it comes up with "NTLDR is missing".
Are you sure there is no floppy, CD or USB drive inserted? Are you booting from the correct boot device? See in Bios.

If it still doesn't help, copy the NTLDR and NTDETECT.COM from Windows XP CD to C: drive. e.g,

```
COPY D:\I386\NTLDR C:\
```
```
COPY D:\I386\NTDETECT.COM C:\
```

Where D: is your cd rom device. After copying, remove the CD and reboot to see if it works now.

---

### Post by dalzell99 on 2010-10-25
The first one copied fine but the second could not be copied.

---

### Post by sikander3786 on 2010-10-25
> **dalzell99 said:**
> The first one copied fine but the second could not be copied.
Why? Any errors? Or it couldn't find the file itself?

You sure, the disc it ok and readable?

---

### Post by dalzell99 on 2010-10-25
I'm not sure why. It copied the first file perfectly but the second one came up with a message underneath it saying "This file could not be copied". I'm pretty sure it's readable because it copied the first.

---

### Post by sikander3786 on 2010-10-25
> **dalzell99 said:**
> I'm not sure why. It copied the first file perfectly but the second one came up with a message underneath it saying "This file could not be copied". I'm pretty sure it's readable because it copied the first.
There are some alternate solutions.

[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

---

### Post by dalzell99 on 2010-10-25
That didn't work either. I might just reinstall xp and hope there wasn't anything valuable on there.

---

### Post by sikander3786 on 2010-10-26
> **dalzell99 said:**
> That didn't work either. I might just reinstall xp and hope there wasn't anything valuable on there.
Wait you can install Lilo. From a Live Ubuntu CD, try

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sdb mbr
```

Don't worry if gives any errors. Just get it onto the MBR and reboot to see if it worked.

If yes, then you can continue with re-installation of Grub.

---

### Post by amsterdamharu on 2010-10-26
Was windows always installed on your second harddisk? It looks like you added a harddisk, then installed ubuntu on it and then tried to run windows of the secondary harddisk.

Take out the ubuntu harddisk and see if windows will start (in the boot.ini there are lines saying where to find windows and adding a hd will screw this up). If that works then all you need to do is make ubuntu your secondary harddisk (slave) then install grub on the primary using the live cd.

---

