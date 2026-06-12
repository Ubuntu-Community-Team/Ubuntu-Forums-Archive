---
title: "Grub out of disk"
date: 2011-04-08
forum: General Help
---

### Post by jarland on 2011-04-08
I installed 10.10 64bit and it was fine. I messed around with some things, went to reinstall (because sometimes, when I'm messing around, it's easier to reinstall than step backward), and now I get:

error: hd0,msdos1 out of disk.
grub rescue>

I don't like the grub command prompt, mostly because I don't know it. Now, no matter how many times I clear my partition table and start from what I assume is square 1, I always end up back here. I've probably reinstalled 7 or 8 times. What annoys me most is that I am absolutely positive that I'm not leaving traces of the previous bootloader when I reinstall. I'm hoping someone has advice, because you can rest assured that I've googled for a day and a half before I ask a question. Plenty of results, all from a slightly different angle (most from USB installations, I'm using DVD), and no working solutions.

---

### Post by Hedgehog1 on 2011-04-08
If you are at a complete (but non-functional) install, please do this:

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-08
In case you are between installs - if you are in a position to wipe the disk clean, please begin your next install by using gparted and do this:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-08
**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-08
**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

**Now when you re-install, select this method:**

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

**And tell the install to use the three partitions this way (You Drive is likely /dev/sda, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]


***The Hedge***

:KS

---

### Post by jarland on 2011-04-09
Thanks for the replies! About to dump the output of that script. I also tried to use GParted, but I get "Error while creating partition table." This happens even when run as root (all done from livecd). I tried manually setting up the partition table from the installer, it did fine, but gave the same result at boot.

This output seems quite interesting.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   488,396,799   488,394,752  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda5        7b56e82b-0e6f-426b-ac3d-f587a2e68f9f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda1: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
```

---

### Post by Hedgehog1 on 2011-04-09
This is very VERY weird.

You have 1 partition on the drive.

It is called /dev/sda1 here:
```
Partition  Boot         Start           End          Size  Id System
/dev/sda1               2,048   488,396,799   488,394,752  83 Linux
```

But the non-existent /dev/sda5 shows here, and no /dev/sda1 is fouond:
```
Device           UUID                                   TYPE       LABEL                         

/dev/sda5        7b56e82b-0e6f-426b-ac3d-f587a2e68f9f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda1: No such file or directory
```

Using gparted, if the /dev/sd5 partiton shows, please right-click on it and select 'swapoff' if available.

Then create a new partition table using gparted.


***The Hedge***

:KS

---

### Post by jarland on 2011-04-09
Alright so I might have messed around in gparted like an hour before I ran that script, and just left the livecd running. It's been one of those days man. Let's get a real output now that I'm actually using my brain again and repartitioned and reinstalled the OS again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4c0286a3-9304-4ce5-aa94-03d4e84f347d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3be9faa3-c583-4dc4-84e3-93ef82282f8f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
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
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d ro single 
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
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
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
# / was on /dev/sda1 during installation
UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3be9faa3-c583-4dc4-84e3-93ef82282f8f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 197.7GB: boot/grub/core.img
 128.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 197.7GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 197.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 99 73 68 c0 05 e6 e3  f3 12 b7 38 23 22 67 7d  |..sh.......8#"g}|
00000010  73 71 46 0d 0a 8a f2 c8  bd df b8 ec a7 f4 f6 be  |sqF.............|
00000020  ea 8b 97 fa 35 bc 8f 3f  d9 2f ac 7c d6 ff 14 d4  |....5..?./.|....|
00000030  c2 03 18 e0 9d b9 f0 02  7c 67 b7 9c f7 58 02 76  |........|g...X.v|
00000040  80 29 b3 76 56 98 27 8f  48 8f d6 01 9f 96 6b 18  |.).vV.'.H.....k.|
00000050  fb 11 20 cf a5 f2 a1 0f  7a 79 ca de 73 cc f1 5d  |.. .....zy..s..]|
00000060  bd b9 c7 de 86 db 8b d4  20 d4 13 3c 5b 11 39 2a  |........ ..<[.9*|
00000070  22 ce 55 95 e2 6e 40 c6  46 91 8b a4 a1 3f b0 0d  |".U..n@.F....?..|
00000080  6c e2 f1 fd 0e 20 f6 7d  e0 41 36 8c b8 b3 ab 9b  |l.... .}.A6.....|
00000090  8d 5d db 32 b5 dc 4d e7  80 41 73 b5 08 4d 5d c8  |.].2..M..As..M].|
000000a0  43 7a c0 0d 0f 64 4c 29  a0 d1 8c 7d f1 15 06 cd  |Cz...dL)...}....|
000000b0  62 c5 d2 4a c8 6e aa b4  70 4e ce b0 68 a6 b8 8c  |b..J.n..pN..h...|
000000c0  83 0a 2b 89 4d 26 34 1e  77 61 90 5b 0f 56 46 50  |..+.M&4.wa.[.VFP|
000000d0  14 ca 4c aa 72 8d 44 46  b8 2b 3a c2 50 dc ab ed  |..L.r.DF.+:.P...|
000000e0  bf 3d a0 c8 61 35 dc 25  d0 50 d8 9f 64 4a 50 45  |.=..a5.%.P..dJPE|
000000f0  2b 8a 2a 9a 19 b2 f4 05  bf b3 55 37 2b 0e e6 51  |+.*.......U7+..Q|
00000100  f9 7f 3b 3f c0 b7 19 7b  e6 f5 83 52 f5 15 77 1d  |..;?...{...R..w.|
00000110  a7 2c b5 9c ed 5f bf dd  8a b2 2a 0c 10 3f 07 14  |.,..._....*..?..|
00000120  22 25 ca 74 39 3a 49 0a  4c 8e 4d 2a 26 76 1f cc  |"%.t9:I.L.M*&v..|
00000130  d1 9f f9 b6 76 4e 57 e5  ef 67 6b b4 ea b9 cc 73  |....vNW..gk....s|
00000140  38 da 35 3b 8e 70 8e d2  ee 17 24 01 6d 2c a1 b3  |8.5;.p....$.m,..|
00000150  f7 cd 5c 74 fb 4b 44 ef  3d 0c 3a 1e 39 38 61 0f  |..\t.KD.=.:.98a.|
00000160  9f bc dc 50 ed 9d ce 46  ce 52 94 4e 19 1a 12 9a  |...P...F.R.N....|
00000170  71 ed 95 ec 44 a7 40 ae  b4 19 86 27 e6 6f ce 8e  |q...D.@....'.o..|
00000180  f7 ef b0 dd 0e 84 82 f7  1c 25 1b 91 d2 e0 c6 57  |.........%.....W|
00000190  8d f1 da 3b bb 89 b0 f6  7d ae 01 34 9e 29 d0 83  |...;....}..4.)..|
000001a0  f8 88 f3 05 58 54 09 2d  51 c6 14 13 d5 32 0d 35  |....XT.-Q....2.5|
000001b0  26 0b 33 d2 d7 87 13 0b  6e 36 b6 8d 10 11 00 fe  |&.3.....n6......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Hedgehog1 on 2011-04-09
Lets start with the easy one.

It appears that you have placed the boot loader in sda2.  For your install, it needs to go in /dev/sda (not a partition like /dev/sda2 or /dev/sda2, but in **/dev/sda**)

Thankfully, you do not have to reinstall to fix this.

Please do these two commands from your LiveCD/LiveUSB:

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```


Then reboot and report back if not solved, or mark the thread 'SOLVED' if you are OK.

***The Hedge***

:KS

---

### Post by jarland on 2011-04-09
I really appreciate the help man. It looks like I'm still getting the same result though.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4c0286a3-9304-4ce5-aa94-03d4e84f347d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3be9faa3-c583-4dc4-84e3-93ef82282f8f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
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
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d ro single 
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
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c0286a3-9304-4ce5-aa94-03d4e84f347d
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
# / was on /dev/sda1 during installation
UUID=4c0286a3-9304-4ce5-aa94-03d4e84f347d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3be9faa3-c583-4dc4-84e3-93ef82282f8f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 197.7GB: boot/grub/core.img
 128.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 197.7GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 197.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 99 73 68 c0 05 e6 e3  f3 12 b7 38 23 22 67 7d  |..sh.......8#"g}|
00000010  73 71 46 0d 0a 8a f2 c8  bd df b8 ec a7 f4 f6 be  |sqF.............|
00000020  ea 8b 97 fa 35 bc 8f 3f  d9 2f ac 7c d6 ff 14 d4  |....5..?./.|....|
00000030  c2 03 18 e0 9d b9 f0 02  7c 67 b7 9c f7 58 02 76  |........|g...X.v|
00000040  80 29 b3 76 56 98 27 8f  48 8f d6 01 9f 96 6b 18  |.).vV.'.H.....k.|
00000050  fb 11 20 cf a5 f2 a1 0f  7a 79 ca de 73 cc f1 5d  |.. .....zy..s..]|
00000060  bd b9 c7 de 86 db 8b d4  20 d4 13 3c 5b 11 39 2a  |........ ..<[.9*|
00000070  22 ce 55 95 e2 6e 40 c6  46 91 8b a4 a1 3f b0 0d  |".U..n@.F....?..|
00000080  6c e2 f1 fd 0e 20 f6 7d  e0 41 36 8c b8 b3 ab 9b  |l.... .}.A6.....|
00000090  8d 5d db 32 b5 dc 4d e7  80 41 73 b5 08 4d 5d c8  |.].2..M..As..M].|
000000a0  43 7a c0 0d 0f 64 4c 29  a0 d1 8c 7d f1 15 06 cd  |Cz...dL)...}....|
000000b0  62 c5 d2 4a c8 6e aa b4  70 4e ce b0 68 a6 b8 8c  |b..J.n..pN..h...|
000000c0  83 0a 2b 89 4d 26 34 1e  77 61 90 5b 0f 56 46 50  |..+.M&4.wa.[.VFP|
000000d0  14 ca 4c aa 72 8d 44 46  b8 2b 3a c2 50 dc ab ed  |..L.r.DF.+:.P...|
000000e0  bf 3d a0 c8 61 35 dc 25  d0 50 d8 9f 64 4a 50 45  |.=..a5.%.P..dJPE|
000000f0  2b 8a 2a 9a 19 b2 f4 05  bf b3 55 37 2b 0e e6 51  |+.*.......U7+..Q|
00000100  f9 7f 3b 3f c0 b7 19 7b  e6 f5 83 52 f5 15 77 1d  |..;?...{...R..w.|
00000110  a7 2c b5 9c ed 5f bf dd  8a b2 2a 0c 10 3f 07 14  |.,..._....*..?..|
00000120  22 25 ca 74 39 3a 49 0a  4c 8e 4d 2a 26 76 1f cc  |"%.t9:I.L.M*&v..|
00000130  d1 9f f9 b6 76 4e 57 e5  ef 67 6b b4 ea b9 cc 73  |....vNW..gk....s|
00000140  38 da 35 3b 8e 70 8e d2  ee 17 24 01 6d 2c a1 b3  |8.5;.p....$.m,..|
00000150  f7 cd 5c 74 fb 4b 44 ef  3d 0c 3a 1e 39 38 61 0f  |..\t.KD.=.:.98a.|
00000160  9f bc dc 50 ed 9d ce 46  ce 52 94 4e 19 1a 12 9a  |...P...F.R.N....|
00000170  71 ed 95 ec 44 a7 40 ae  b4 19 86 27 e6 6f ce 8e  |q...D.@....'.o..|
00000180  f7 ef b0 dd 0e 84 82 f7  1c 25 1b 91 d2 e0 c6 57  |.........%.....W|
00000190  8d f1 da 3b bb 89 b0 f6  7d ae 01 34 9e 29 d0 83  |...;....}..4.)..|
000001a0  f8 88 f3 05 58 54 09 2d  51 c6 14 13 d5 32 0d 35  |....XT.-Q....2.5|
000001b0  26 0b 33 d2 d7 87 13 0b  6e 36 b6 8d 10 11 00 fe  |&.3.....n6......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Hedgehog1 on 2011-04-09
OK - here is the next logical thing to try:

From the LiveCD/LiveUSB:

```
sudo mount /dev/sda1 /mnt
```

```
gksudo gedit /mnt/etc/default/grub
```

[COLOR="Red"]Change[/COLOR]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

[COLOR="red"]to[/COLOR]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=120"

Save the file, then:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot and report back if not solved, or mark the thread 'SOLVED' if you are OK.


***The Hedge***

:KS

---

### Post by jarland on 2011-04-09
Still gave me the same error. If I wasn't so darn sure that this hard drive was fine I'd be looking to blame it.

---

