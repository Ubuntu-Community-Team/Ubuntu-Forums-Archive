---
title: "Ubuntu fails to boot"
date: 2010-10-24
forum: General Help
---

### Post by slpixe on 2010-10-24
Hey all,
This morning I have been unable to boot into my ubuntu drive.

To point out, I have been using standby and "sudo shutdown -h now" and sometimes I would get an error when shutting down, or starting up from standby

Anyway after selecting my ubuntu partition on the grub menu, I get the ubuntu loading bar.

Then I get the following errors in a shell

```
udev-work[75] inotify_add_watch (6, /dev/dm-2, 10) failed no such file or directory

Gave up waiting for root device
Alert /dev/disk/by__uuid/(loads of random characters)
Does not exist dropping to a shell

Busy Box v1.15.3
Initramfs
```

If this will be too hard to fix.
Do you know of a way I can at least pull my data off the drive?

Thanks all

---

### Post by argedion on 2010-10-24
I have no clue as to the error your having but I did find a program that may be able to help its called:
ubuntu-rescue-remix-10-04 I believe it can be found here:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)
Good luck

---

### Post by slpixe on 2010-10-24
Ok

I shall have a go with that

btw, on windows, when I go to disk manager, It asks me to initilize my ubuntu drive.
with either MBR(mast boot rec), or another grid type or something.

Should I initilize? Or will that destroy some section of ubuntu
or will it fix it?

---

### Post by Rubi1200 on 2010-10-24
Before trying the suggestion mentioned by the previous poster, use a LiveCD and post the results of the following commands (run them separately):

```
cat /etc/fstab
```

```
sudo blkid
```

Thanks.

---

### Post by slpixe on 2010-10-24
Ok I will do that instead, was having hard time finding way of making bootable usb for the recover program.

---

### Post by slpixe on 2010-10-24
Any problems seeing images let me know

fstab
[IMG]http://***************/_2_W6yrV2S9Q/TMQ_2p1tOaI/AAAAAAAAIPA/we-JaJQoVlE/s640/cat%20etc%20fstab.png[/IMG]

blkid
[IMG]http://lh6.ggpht.com/_2_W6yrV2S9Q/TMQ_2omHLSI/AAAAAAAAIPE/wqnINBALXEA/s640/blkid.png[/IMG]

---

### Post by Rubi1200 on 2010-10-24
Hi slpixe,
do me a favor please and copy/paste the results from the terminal back here; the images are not clear enough.

Thanks.

---

### Post by slpixe on 2010-10-24
fstab
```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```blkid
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e617c4d2-49ea-413d-a0ee-f8da789ae459" TYPE="ext4" 
/dev/sda5: UUID="740211c5-2e2e-4f47-8929-8e83460d6017" TYPE="swap" 
/dev/sdb: TYPE="silicon_medley_raid_member" 
/dev/sdc: TYPE="silicon_medley_raid_member" 
/dev/sdd1: LABEL="MYLINUXLIVE" UUID="7E43-2267" TYPE="vfat" 
/dev/sde1: LABEL="WD 250" UUID="240428100427E390" TYPE="ntfs" 
/dev/sdf1: LABEL="Tera" UUID="A08014578014366E" TYPE="ntfs" 
/dev/mapper/sil_agagcededfff1: LABEL="20k raptor 70" UUID="ACE05A9BE05A6B98" TYPE="ntfs" 
ubuntu@ubuntu:~$ 
```(sda = ubuntu I think
sdb/c = windows on a raid (+ sil 20k rapter = the drive for windows)
mylinuxlive = live usb im on now
wd250/tera = storage drives
theres a 200gig maxtor which ubuntu is on..

hope this helps)
[IMG]http://lh5.ggpht.com/_2_W6yrV2S9Q/TMRJOMJcoiI/AAAAAAAAIPU/AEFQI4VJcmg/s800/hard%20disk.png[/IMG]

---

### Post by Rubi1200 on 2010-10-24
Well, the fstab file is certainly missing the required entries. In other words, at the very least the Ubuntu and swap partitions should be in there along with their respective UUIDs. Since I do not use, nor have experience with, RAID arrays, I cannot advise you on that account.

Here is what my fstab file looks like for comparison:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7e07a924-8356-48d2-a8ec-65bc85589b04 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=607d5597-2115-44dd-a807-215fc0c14711 none            swap    sw   
```

This link might help you get further:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by slpixe on 2010-10-24
alright im going to want a little more help than that.

Linux must be there and working for the "disk utility" to see linux on the drive. surely?

Any other suggestions for 1) recovering the user data 2) fixing the booting?

---

### Post by slpixe on 2010-10-24
Using linux live.

I can go onto the harddrive and get into the home folder
but I cannot access my user folder (permission etc).

Is there any way to type in my account password to get access to my folder?

---

### Post by Rubi1200 on 2010-10-24
As I said, you do not have the average setup.

But, from the LiveCD, post the results of the boot-script linked at the bottom of my post and I will try and see what we can do to help you resolve this.

Thanks for your patience.

---

### Post by ronparent on 2010-10-24
> udev-work[75] inotify_add_watch (6, /dev/dm-2, 10) failed no such file or directory
Ignore. Not a material error. Will probably disappear when the developers get their act together.

> btw, on windows, when I go to disk manager, It asks me to initilize my ubuntu drive.
with either MBR(mast boot rec), or another grid type or something
It is probably best to stay away from the windows disk manage in regard to Ubuntu drive. Some inconsistencies in hoe win 7 handles extended partitions compared with Ubuntu could cause problems. And yes that include how it views MBR's.

Otherwise than that the problems seen to be some corruption of the Ubuntu setup.

+1 Let see the results from the boot info script.

---

### Post by slpixe on 2010-10-24
boot info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Grub 2 is installed in the MBR of /dev/mapper/sil_agagcededfff and looks 
    on the same drive in partition #1 for (,msdos1)/boot/grub.

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

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sde1 has 
                       488394751 sectors, but according to the info from 
                       fdisk, it has 488397104 sectors.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdf1 has 
                       1953523056 sectors, but according to the info from 
                       fdisk, it has 1953525104 sectors.
    Operating System:  
    Boot files/dirs:   

sil_agagcededfff1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   386,220,031   386,217,984  83 Linux
/dev/sda2         386,222,078   398,295,039    12,072,962   5 Extended
/dev/sda5         386,222,080   398,295,039    12,072,960  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62     4,027,519     4,027,458   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,397,167   488,397,105  42 SFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 1,953,525,167 1,953,525,105  42 SFS


Drive: sil_agagcededfff ___________________ _____________________________________________________

Disk /dev/mapper/sil_agagcededfff: 74.0 GB, 74037002240 bytes
255 heads, 63 sectors/track, 9001 cylinders, total 144603520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/sil_agagcededfff1   *             63   144,584,999   144,584,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/sil_agagcededfff1 ACE05A9BE05A6B98                       ntfs       20k raptor 70                 
/dev/mapper/sil_agagcededfff: PTTYPE="dos" 
/dev/sda1        e617c4d2-49ea-413d-a0ee-f8da789ae459   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        740211c5-2e2e-4f47-8929-8e83460d6017   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc                                                silicon_medley_raid_member                               
/dev/sdd1        7E43-2267                              vfat       MYLINUXLIVE                   
/dev/sdd: PTTYPE="dos" 
/dev/sde1        240428100427E390                       ntfs       WD 250                        
/dev/sde: PTTYPE="dos" 
/dev/sdf1        A08014578014366E                       ntfs       Tera                          
/dev/sdf: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sil_agagcededfff
sil_agagcededfff1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/e617c4d2-49ea-413d-a0ee-f8da789ae459 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e617c4d2-49ea-413d-a0ee-f8da789ae459 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e617c4d2-49ea-413d-a0ee-f8da789ae459 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e617c4d2-49ea-413d-a0ee-f8da789ae459 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e617c4d2-49ea-413d-a0ee-f8da789ae459 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e617c4d2-49ea-413d-a0ee-f8da789ae459
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/sil_agagcededfff1)" {
    savedefault
    insmod part_msdos
    insmod ntfs
    set root='(/dev/mapper/sil_agagcededfff,msdos1)'
    search --no-floppy --fs-uuid --set ace05a9be05a6b98
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=e617c4d2-49ea-413d-a0ee-f8da789ae459 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=740211c5-2e2e-4f47-8929-8e83460d6017 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
 176.4GB: boot/grub/grub.cfg
 111.8GB: boot/initrd.img-2.6.32-21-generic
 105.7GB: boot/initrd.img-2.6.35-22-generic
 111.8GB: boot/vmlinuz-2.6.32-21-generic
 112.6GB: boot/vmlinuz-2.6.35-22-generic
 105.7GB: initrd.img
 112.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  26 1c 08 46 82 b4 7e 2e  92 1b 30 a1 ad bd fd 7b  |&..F..~...0....{|
00000010  95 e6 8d 74 e6 d1 36 74  a8 f1 73 30 dd 08 67 4d  |...t..6t..s0..gM|
00000020  93 9a 40 6c 9f 1a f3 3d  79 35 96 1d f9 8a d3 c6  |..@l...=y5......|
00000030  fe 9a a4 ee d7 4a 8b 26  b8 ab d5 51 eb 7b 0b 9e  |.....J.&...Q.{..|
00000040  81 bf 5c e2 d5 a9 8f e2  9a 4b 35 ea 40 ca ec 66  |..\......K5.@..f|
00000050  c8 bf ad 46 e5 aa 7b 74  8b ef e9 cf d4 a2 84 dd  |...F..{t........|
00000060  73 4b 98 9b c1 96 a7 4b  87 6a 6d 3b f7 45 85 5b  |sK.....K.jm;.E.[|
00000070  df 40 73 b9 e8 ae ad 04  e5 00 80 8e f1 38 06 88  |.@s..........8..|
00000080  a1 16 91 62 27 48 61 42  72 0a 52 d9 26 13 36 32  |...b'HaBr.R.&.62|
00000090  6a bc 52 a4 11 f5 1d a8  6a 7a 84 84 cb 3e 05 28  |j.R.....jz...>.(|
000000a0  14 82 0a 37 06 69 8c 23  30 e7 50 19 c8 d6 d6 3d  |...7.i.#0.P....=|
000000b0  bf 4f a9 10 c8 8e 6a 76  12 de 6c 5d 8c fb 20 88  |.O....jv..l].. .|
000000c0  a8 10 40 26 03 0a 93 a1  08 cd 22 23 71 3d b5 d7  |..@&......"#q=..|
000000d0  18 26 6a 29 34 a6 c9 66  28 b4 7b 0f 8f 07 53 64  |.&j)4..f(.{...Sd|
000000e0  1f 8b 6b f6 5a a1 b8 e8  b1 2f 0f 07 09 16 d1 56  |..k.Z..../.....V|
000000f0  92 07 61 28 9e 53 5a 78  9a 0e 42 dc 2e 55 35 a2  |..a(.SZx..B..U5.|
00000100  cd fe cd eb a0 41 52 b7  ea a5 27 28 be 54 9f 56  |.....AR...'(.T.V|
00000110  29 25 3e 9f 74 ce 8e c1  57 5c 02 19 44 c8 55 3d  |)%>.t...W\..D.U=|
00000120  44 06 9d 24 10 a8 15 3c  6d a4 37 77 98 69 58 c5  |D..$...<m.7w.iX.|
00000130  52 5e 68 d4 f1 ea 1c b4  28 c8 ca 00 cb 01 8d aa  |R^h.....(.......|
00000140  76 bc a0 cd 29 28 e6 df  09 5b 71 64 8b a1 01 4e  |v...)(...[qd...N|
00000150  ba c1 a1 08 05 b0 8f a6  98 04 50 2f 4c f1 f2 8d  |..........P/L...|
00000160  53 a1 c0 9b 18 00 80 48  87 18 af 12 31 17 24 6d  |S......H....1.$m|
00000170  c5 f8 fd 53 44 5c b0 48  a1 7c 77 29 50 d2 a4 53  |...SD\.H.|w)P..S|
00000180  89 32 38 57 c9 f3 21 86  ca 9e 2e 4b 42 e0 c2 a2  |.28W..!....KB...|
00000190  78 86 61 d0 44 fa cc f5  d4 cb 3c 9c a5 32 a6 4e  |x.a.D.....<..2.N|
000001a0  32 e6 ce a8 d1 ff fb c0  44 35 04 e6 1b 62 d6 8b  |2.......D5...b..|
000001b0  2f 4b 72 c2 ae ea f1 65  23 ea 58 95 9d 5c 00 fe  |/Kr....e#.X..\..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 b8 00 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by ronparent on 2010-10-24
If you want to continue booting from the raid (/dev/mapper/sil_agagcededfff) then you will have to do a grub reinstall per following: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Use this process. First mount the Ubuntu 10.10 install:
> sudo mount /dev/sda1 /mnt
Then reinstall the grub to boot from the raid array:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/sil_agagcededfff

and you should now be set.

---

### Post by slpixe on 2010-10-24
@ronparent

hm, this is wrong,

My pc can access the grub fine, and boot into windows (which is on the raid)

When selecting ubuntu on the raid, is when I get the error.

so maybe do a sudo grub-update? cause maybe the grub lost track of the ubuntu loading scripts or something?


Also no further reply about if I can type in my password to load up my user folder, while i am looking at it in linux live

---

### Post by ronparent on 2010-10-24
Your results indicate that grub 2 is looking for the grub installation on the raid. That is wrong. The grub should be installed to the same partition as the 10.10 install - that is /dev/sda1.

It is wrong primarily because the kernel you are booting to won't be found there and the Ubuntu boot will fail. Solution: simply reinstall grub so that grub is located on /dev/sda1 and the grub boot loader remains on the raid which is apparently set as boot in your system's bios. The reinstall should properly configure the grub menu so that windows is still bootable. Is that what you wanted?

---

### Post by slpixe on 2010-10-24
Ok I think that is right

To confirm I want Grub (loader, so that when my system starts, it asks windows or ubuntu (does this at the moment anyway))

and for the grub to be on the windows drive (as my maxtor/ubuntu drive is less stable, and I broke my windows loader awhile ago)

The commands you gave will reinstall grub on the windows drive, and reconfigure itself to be able to boot into ubuntu fine?


Thanks in advance

---

### Post by ronparent on 2010-10-24
Just to clarify. The grub boot loader will remain on the windows (raid) drive. The grub program will be located with the 10.10 installation. I don't think you have another suitable location without creating a small boot partition somewhere (ie not an ntfs partition).

Even if this isn't ideal, it would serve to make your system available to boot all systems until you could work out alternative solutions.

---

### Post by slpixe on 2010-10-24
Ok that makes sense.

Yes booting all systems is fine

Im just confirming because the command you said 
> sudo grub-install --root-directory=/mnt/ /dev/mapper/sil_agagcededfff
has the "sil" drive, which is the windows drive. I was just making sure this is correct. and is not meant to be one of the ubuntu partitions?

---

### Post by ronparent on 2010-10-24
Yes, the command installs grub 2 into the file system mounted at /mnt (/dev/sda1) and overwrites the boot loader to the MBR of the raid array (where it is now).

---

### Post by slpixe on 2010-10-24
Hey all thanks so much!

It loaded up fine

crazy how 2 commands can fix everything.

---

