---
title: "Cannot Access extended partition"
date: 2010-12-28
forum: General Help
---

### Post by aldee96 on 2010-12-28
I'm very-very new user to ubuntu
I've installed ubuntu a weeks ago

Two days ago I want to expand the free room for my C:\ partition on my laptop, i thought that just shrink the D:\ partition and expand the C:\ and the problem solved, but it's not solved, the C:\ remains and can't be expanded. so i merge the D:\ again,but the D:\ status become an extended partition

After all, next morning I boot into Ubuntu and my D:\ are not available in "Places" menu in Ubuntu just the C:\ partition, so I boot from Win7 and run CHKDSK /f to my D:\ partition, but it's gave me no effects

Is there any way to solve this problem? I've run

```
sudo fdisk -l
```

in terminal and my D:\ listed as "Extended" in System type.
In my Win7, everything is alright

---

### Post by mikewhatever on 2010-12-28
What filesystem is on D:\? An extended partition is just a container for logical partitions which can be created inside it.
From Ubuntu, can you post the output of **sudo fdisk -l** to let us see the partition table.

---

### Post by aldee96 on 2010-12-29
> **mikewhatever said:**
> What filesystem is on D:\? An extended partition is just a container for logical partitions which can be created inside it.
From Ubuntu, can you post the output of **sudo fdisk -l** to let us see the partition table.

here it is 
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6425ab5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         852     6835200   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         852         864      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             864        4023    25376123+   7  HPFS/NTFS
/dev/sda4            4023        9729    45834849+   5  Extended
/dev/sda5            5162        9729    36691404+   7  HPFS/NTFS
/dev/sda6            4023        5107     8701952   83  Linux
/dev/sda7            5107        5161      439296   82  Linux swap / Solaris

Partition table entries are not in disk order

```

there's something weird in the start and end i think

---

### Post by vanadium on 2010-12-29
You have three ntfs ("Windows") partitions. Two of these are primary partitions, sda5 is a logical partition. The logical partition sda6 is your Ubuntu system partition, and sd7 your swap partition, a partition used for swap memory.

Seeing three ntfs partitions, it appears that under Windows, you would have three drives? You only refer to C: and D:. Perhaps, the sda2 is a "recovery" partition, hidden from Windows.

To see whether your sda5 can mount, perform the following experiment in a terminal window and post the output here. Eventual error messages can give a clue as to what is wrong. Open a terminal and paste following commands:

```

mkdir ntfstest
sudo mount /dev/sda5 ntfstest

```

If there is no output, and you can see the contents of sda5 in the directory (folder) ntfstest, then at least we know already that the problem is not with the partition itself.

---

### Post by Quackers on 2010-12-29
It appears that sda5 should be a primary partition. It is now, however a logical partition within sda4 (the extended partition). I'm not sure how you managed to do that!
Could you please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by aldee96 on 2010-12-29
> **vanadium said:**
> You have three ntfs ("Windows") partitions. Two of these are primary partitions, sda5 is a logical partition. The logical partition sda6 is your Ubuntu system partition, and sd7 your swap partition, a partition used for swap memory.

Seeing three ntfs partitions, it appears that under Windows, you would have three drives? You only refer to C: and D:. Perhaps, the sda2 is a "recovery" partition, hidden from Windows.

To see whether your sda5 can mount, perform the following experiment in a terminal window and post the output here. Eventual error messages can give a clue as to what is wrong. Open a terminal and paste following commands:

```

mkdir ntfstest
sudo mount /dev/sda5 ntfstest

```If there is no output, and you can see the contents of sda5 in the directory (folder) ntfstest, then at least we know already that the problem is not with the partition itself.

thanks the D:\ partition is mounted again, but will it be mounted averytime i started the Ubuntu? and before it was located in ```
/media/0B8662EE5459F605
``` now it's mounted under the places menu and named "ntfstest"can i rename it and place it in the location before as seen above?

---

### Post by audiomick on 2010-12-29
> **Quackers said:**
> It appears that sda5 should be a primary partition. It is now, however a logical partition within sda4 (the extended partition). I'm not sure how you managed to do that!
If a partition is called sda5, it must be a logical. It is only possible to have 4 primaries on any drive. After that, you have to have extended with logicals inside.

Even if there are only one primary, one extended and lots of logicals inside it, the first logical will always be sda5. The numbering system works that way.

There doesn't seem to be anything principally wrong with the partition table as such, although that is no help in getting your access back. I'd be curious to know what the space at the start of the drive that comes up as sda1 is. No recognised file system on it...

The boot info script is probably a good idea.

---

### Post by Quackers on 2010-12-29
Yes, I'm aware of that :-)
However, if sda5 is drive D:, it seems it existed before Ubuntu was installed and the extended partiton was made. It would be very unusual for D: to have been a logical partition at that stage.
It is much more likely to have been a 4th primary partition, imho. So, unless D: has been deleted and replaced with a logical partition the present partition layout looks odd. However the OP doesn't say that this was done.
The OP states 
"so i merge the D:\ again,but the D:\ status become an extended partition"
which is curious to me.

---

### Post by vanadium on 2010-12-29
> **aldee96 said:**
> thanks the D:\ partition is mounted again, but will it be mounted averytime i started the Ubuntu? and before it was located in ```
/media/0B8662EE5459F605
``` now it's mounted under the places menu and named "ntfstest"can i rename it and place it in the location before as seen above?
This would suggest that at least, there is nothing wrong with this partition as such. Question remains then why you cannot see it in your Places menu anymore.

Since this is an internal drive anyway, you could include the partition in your /etc/fstab file. That way, it will be automounted during startup of the system.

---

### Post by audiomick on 2010-12-29
> **Quackers said:**
>  [COLOR=Red]It would be very unusual for D: to have been a logical partition at that stage.[/COLOR]
It is much more likely to have been a 4th primary partition, imho. So, unless D: has been deleted and replaced with a logical partition the present partition layout looks odd. However the OP doesn't say that this was done.
The OP states 
"so i merge the D:\ again,but the D:\ status become an extended partition"
which is curious to me.

True, but it must have been. As long as the "D:" partition is the same one all the time, anyway. As far as I know, it is just not possible to change a primary into a logical, but I could be wrong.

I think that the D: partition, if it was there before the Linux install, unusual though it is, must have been a logical all the time. Or it was created at the time of the Linux install.

D: being a logical would also explain why C: couldn't be expanded. Shrinking a partition inside an extended does not make any space outside the extended available.

Anyway, that is all speculation. Let's wait and see what the OP says next... ;)

edit: Ah, forgot to mention: OP says everything is OK in Win7, so I suspect the UUID has been changed by the partition manipulation. That would mean, I think, that fstab would need to be modified to get Ubuntu to mount the partition at boot every time. Unfortunately, I don't know how to do that... :(

---

### Post by aldee96 on 2010-12-29
> **Quackers said:**
> Yes, I'm aware of that :-)
However, if sda5 is drive D:, it seems it existed before Ubuntu was installed and the extended partiton was made. It would be very unusual for D: to have been a logical partition at that stage.
It is much more likely to have been a 4th primary partition, imho. So, unless D: has been deleted and replaced with a logical partition the present partition layout looks odd. However the OP doesn't say that this was done.
The OP states 
"so i merge the D:\ again,but the D:\ status become an extended partition"
which is curious to me.

here's the RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       50748768 sectors, but according to the info from 
                       fdisk, it has 50752246 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1               2,048    13,672,447    13,670,400  27 Hidden HPFS/NTFS
/dev/sda2    *     13,672,448    13,877,247       204,800   7 HPFS/NTFS
/dev/sda3          13,877,248    64,629,494    50,752,247   7 HPFS/NTFS
/dev/sda4          64,626,686   156,296,384    91,669,699   5 Extended
/dev/sda5          82,911,528   156,294,336    73,382,809   7 HPFS/NTFS
/dev/sda6          64,626,688    82,030,591    17,403,904  83 Linux
/dev/sda7          82,032,640    82,911,231       878,592  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4
/dev/sda3 overlaps with /dev/sda6

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        66E01C48E01C20BB                       ntfs       Recovery                      
/dev/sda2        52C0E118C0E102D9                       ntfs       System Reserved               
/dev/sda3        1C12E6DF12E6BD40                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0B8662EE5459F605                       ntfs                                     
/dev/sda6        585e205c-4317-4322-8651-b3fea0d198f7   ext4                                     
/dev/sda7        cc659d0a-af92-451d-9998-c695532ae27b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/1C12E6DF12E6BD40  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /home/aldhika/ntfstest   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 66e01c48e01c20bb
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 52c0e118c0e102d9
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=585e205c-4317-4322-8651-b3fea0d198f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cc659d0a-af92-451d-9998-c695532ae27b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  40.1GB: boot/grub/core.img
  35.7GB: boot/grub/grub.cfg
  34.7GB: boot/initrd.img-2.6.35-22-generic
  35.7GB: boot/initrd.img-2.6.35-24-generic
  40.1GB: boot/vmlinuz-2.6.35-22-generic
  39.7GB: boot/vmlinuz-2.6.35-24-generic
  35.7GB: initrd.img
  34.7GB: initrd.img.old
  39.7GB: vmlinuz
  40.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ac 8e e5 37 6e 67 c9 36  7d 33 15 b1 00 78 9e 4d  |...7ng.6}3...x.M|
00000010  cc e9 e6 78 3e db af f4  61 0b 62 c0 68 6f 24 bf  |...x>...a.b.ho$.|
00000020  07 85 48 6a 18 49 ba 6c  62 12 3b 7f 64 99 ba 95  |..Hj.I.lb.;.d...|
00000030  96 e5 9c c2 99 71 6e a4  64 77 f5 95 e7 4d aa 56  |.....qn.dw...M.V|
00000040  35 9a 0d ed fd 1c 90 45  4e 78 68 58 87 49 7c 67  |5......ENxhX.I|g|
00000050  8b 7a b0 31 e7 dd 47 1e  23 e8 34 c5 e2 8c f8 4b  |.z.1..G.#.4....K|
00000060  05 fe 6d 90 53 95 9b 95  da 55 00 8b 9c d6 ae 14  |..m.S....U......|
00000070  7d e7 8a ca 38 bd be 29  cf e5 58 c0 6c bf d6 66  |}...8..)..X.l..f|
00000080  00 1d e6 a9 e8 b4 d4 bb  bc 74 d5 63 df 86 f4 56  |.........t.c...V|
00000090  a3 4c 58 21 94 b0 c8 b3  d4 02 f2 1d 77 1e b9 2f  |.LX!........w../|
000000a0  37 1e 6c 09 97 cf 57 54  23 a8 73 8b a3 96 7a 2f  |7.l...WT#.s...z/|
000000b0  1c ea 8c ae 68 2f b0 18  ac 4e aa 5b db 89 6d 04  |....h/...N.[..m.|
000000c0  b2 d8 27 b6 1a e6 43 38  f8 b8 09 b6 44 ea c4 66  |..'...C8....D..f|
000000d0  19 ad 3d c2 3d 1a 66 ba  0d 8e 1a 0a a8 2a 1a 6d  |..=.=.f......*.m|
000000e0  2c 7d 0a c1 52 04 0f 05  af 2e bb d6 3e c5 b0 9d  |,}..R.......>...|
000000f0  c9 a2 85 ab 70 c9 19 52  67 0b ea 58 c8 87 51 e2  |....p..Rg..X..Q.|
00000100  b3 1c ca ec 86 44 d1 f0  13 82 02 d6 bb 09 75 a4  |.....D........u.|
00000110  55 35 35 28 48 c8 49 c7  64 6a 8e 85 11 6f 0b c7  |U55(H.I.dj...o..|
00000120  6d 17 f8 75 2c 7e ef 75  ca 28 4c 64 33 87 29 55  |m..u,~.u.(Ld3.)U|
00000130  9f 1e 60 f1 4e 4f 22 d9  d6 55 31 a4 61 56 51 71  |..`.NO"..U1.aVQq|
00000140  9e c4 38 9b 22 85 d9 d0  b5 d4 71 d2 59 c2 22 9f  |..8.".....q.Y.".|
00000150  f4 f4 7b 1b e6 43 51 67  cc 38 84 d8 20 62 bc fb  |..{..CQg.8.. b..|
00000160  aa 01 4e 9d ef e7 84 1a  42 c5 a0 4e 73 24 11 32  |..N.....B..Ns$.2|
00000170  d1 5c 85 4f 52 0a 23 a9  ce 36 cb 2e eb bb 4d fd  |.\.OR.#..6....M.|
00000180  6a 7b 65 c4 9d 87 aa 14  0d 1b 4b 62 84 d2 d4 16  |j{e.......Kb....|
00000190  e8 b0 c7 e1 90 70 de 0f  40 68 02 c5 87 4a ca e8  |.....p..@h...J..|
000001a0  8a 97 00 af b9 d4 3b d8  2b 0a ea cd 61 73 7d 37  |......;.+...as}7|
000001b0  87 0e ae ac 35 e9 c3 8d  4c bb 25 2e 07 bc 00 fe  |....5...L.%.....|
000001c0  ff ff 07 fe ff ff 2a 01  17 01 99 bb 5f 04 00 fe  |......*....._...|
000001d0  ff ff 05 2a f8 ff 01 00  00 00 01 90 09 01 00 00  |...*............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by vanadium on 2010-12-29
This provides any information you could supply, but does not hint to any error. Please reboot your system such that everything is back to the default. Can you see the partition in Places - Computer? If so, can you see its contents by double clicking the icon?

---

### Post by Quackers on 2010-12-29
The bit in red could be a problem
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    13,672,447    13,670,400  27 Hidden HPFS/NTFS
/dev/sda2    *     13,672,448    13,877,247       204,800   7 HPFS/NTFS
/dev/sda3          13,877,248    64,629,494    50,752,247   7 HPFS/NTFS
/dev/sda4          64,626,686   156,296,384    91,669,699   5 Extended
/dev/sda5          82,911,528   156,294,336    73,382,809   7 HPFS/NTFS
/dev/sda6          64,626,688    82,030,591    17,403,904  83 Linux
/dev/sda7          82,032,640    82,911,231       878,592  82 Linux swap / Solaris

[COLOR="Red"]/dev/sda3 overlaps with /dev/sda4
/dev/sda3 overlaps with /dev/sda6[/COLOR]

```
[COLOR="Black"]But I'm not sure on how you would go about fixing it.[/COLOR]

---

### Post by aldee96 on 2010-12-29
> **vanadium said:**
> This provides any information you could supply, but does not hint to any error. Please reboot your system such that everything is back to the default. Can you see the partition in Places - Computer? If so, can you see its contents by double clicking the icon?

No ican't see it again, it's disappear

---

### Post by aldee96 on 2010-12-29
> **vanadium said:**
> This would suggest that at least, there is nothing wrong with this partition as such. Question remains then why you cannot see it in your Places menu anymore.

Since this is an internal drive anyway, you could include the partition in your /etc/fstab file. That way, it will be automounted during startup of the system.

how to edit the /etc/fstab file to mount it during the startup and mounted at
```
media/0B8662EE5459F605
``` ?

---

### Post by vanadium on 2010-12-29
Create mount point "/media/0B8662EE5459F605"

Add a line for the drive to the file /etc/fstab:

```

UUID=0B8662EE5459F605  /media/0B8662EE5459F605 ntfs defaults,locale=en_US.UTF-8 0 0

```

---

### Post by coffeecat on 2010-12-29
@aldee96, I suggest you delay on this:

> **vanadium said:**
> Create mount point "/media/0B8662EE5459F605"

Add a line for the drive to the file /etc/fstab:

```

UUID=0B8662EE5459F605  /media/0B8662EE5459F605 ntfs defaults,locale=en_US.UTF-8 0 0

```

... and take **serious** note of what Quackers has pointed out:

> **Quackers said:**
> The bit in red could be a problem
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    13,672,447    13,670,400  27 Hidden HPFS/NTFS
/dev/sda2    *     13,672,448    13,877,247       204,800   7 HPFS/NTFS
/dev/sda3          13,877,248    64,629,494    50,752,247   7 HPFS/NTFS
/dev/sda4          64,626,686   156,296,384    91,669,699   5 Extended
/dev/sda5          82,911,528   156,294,336    73,382,809   7 HPFS/NTFS
/dev/sda6          64,626,688    82,030,591    17,403,904  83 Linux
/dev/sda7          82,032,640    82,911,231       878,592  82 Linux swap / Solaris

[COLOR=Red]/dev/sda3 overlaps with /dev/sda4
/dev/sda3 overlaps with /dev/sda6[/COLOR]

```

Not only does sda3 (your Windows C: partition) overlap with the extended sda4, it overlaps with your sda6 Ubuntu root partition. Your inability to mount sda5 may be secondary to this. This overlapping problem may lead to filesystem corruption unless something is done. I need to read the thread more closely before suggesting anything and will post back if I can.

---

### Post by vanadium on 2010-12-29
sda5 can be mounted using the terminal without a problem. Only does it not show up in nautilus.

To fix the overlapping partitions will involve changing the partitioning. Indeed, the overlap might cause corruption of the extended partition and the Ubuntu system partition one day, when data is written to sda3 on a place where the Ubuntu system partition is supposed to be.

Repartitioning is in theory possible without having to remove the data. However, do not start such an attempt unless you have an up-to-date backup copy of your user data (which you should always have).

---

### Post by Quackers on 2010-12-29
After much consultation with my learned coleague :-) it seems that the best we can come up with for the moment is to try shrinking the C: partition by a few MB's. Even 50MB would be more than enough. For this job I would first try the Windows disk management console. Right-click the C: partition and select shrink, then just enter 50MB as the shrink amount - if Windows will allow that.
BUT, you should first defrag the C: drive at least once, preferrably twice.

If the change is allowed you should reboot into Windows a couple of times to make sure it is happy with the change.
At that point you could try Ubuntu and see if the missing partition now mounts in Places.

Whenever making partition changes you should make backups of any important data first!

---

### Post by srs5694 on 2010-12-29
First, it's imperative that partitions be clearly identified. In the first post of this thread, aldee96 referred to two partitions by their Windows identifiers, C: and D:. Linux, however, doesn't use disk identifiers of this form, and as vanadium pointed out, there are three NTFS partitions on the disk (plus one hidden NTFS partition), so it's unclear which partition is C:, which is D:, and how the other partitions are identified in Windows. With the exception of /dev/sda1 (the hidden partition) and /dev/sda2, these partitions all have unique sizes, so I suggest that aldee96 go back and figure out how the Windows and Linux partition identifiers map to each other and post that information. The question of partition identification intersects with what aldee96 was attempting to do originally. I'm afraid that description is a bit confusing to me. It sounds like aldee96 wanted to re-allocate disk space from D: to C: but somehow ended up with three partitions instead. Aldee96 must clearly identify which partitions have data that must be preserved, which (if any) can be safely deleted, and what further changes are desirable, beyond those identified below (and by others).

Second, Quackers' identification of the overlapping partitions is very very very very serious! I do not advise attempting to shrink /dev/sda3 until after backing up both /dev/sda5 and /dev/sda6, or at least backing up /dev/sda5 and then saving the output of "sudo sfdisk -d /dev/sda" on a printout or to a removable disk. The reason is that logical partitions are defined in what's known as a "linked list" data structure, in which one partition's definition points to the location where the next one is defined. Because /dev/sda3 overlaps the beginning of the extended partition and also the beginning of the first logical partition, that means that it overlaps the start of the linked list data structure. Resizing /dev/sda3 (or indeed doing anything with /dev/sda3, except deleting it with fdisk) could damage that critical start point, thus trashing access to the rest of the disk. I don't mean to overstate the risk; such a disastrous outcome is far from certain, and in fact may be a bit unlikely unless you were to start writing new data to /dev/sda3. It could happen, though, so back up now!

In fact, the safest course of action is probably to back up /dev/sda3 from Linux using whatever tools are convenient (I'd use tar, but other tools are available). You can then delete /dev/sda3 using fdisk, create a new and slightly smaller /dev/sda3, reboot, and restore the backup. This will only be practical if /dev/sda3 is not a boot partition, though.

If /dev/sda3 is currently empty and you want to give its space to /dev/sda2, then the solution is relatively easy: Delete /dev/sda3 using fdisk, reboot, and use the Windows partition resizer to resize /dev/sda2 to cover the newly-freed space.

---

### Post by aldee96 on 2010-12-30
in the attachment 1, the D:\ is available on Win7
If i'm not wrong:

[LIST]
[*]***[COLOR=Red]dev/sda1[/COLOR]*** is a recovery partition from Win Vista before,because my laptop pre-installed with it(VAIO VGN-CR11GH/L). But it was attacked by virus so i installed win 7
[*]***[COLOR=Red]dev/sda2[/COLOR]*** is the Win7 partition
[/LIST]

---

### Post by Quackers on 2010-12-30
Hi aldee96, I'm afraid from your screenshots it isn't easy to see what is what.
If the partitions are in disc order 
sda1 is almost certainly your recovery partition as it was pre-installed
sda2 is a 100MB system reserved partition for Windows 7 boot files
sda3 is your Windows installation (C: )
your next partition (possibly sda6) appears to be a 8.3GB primary partition which is listed in the boot script as your Ubuntu /root partition
your next partition (possibly sda7) appears to be a 429MB primary partition listed in the boot script as swap space
Your last partition is a logical partition (D: or probably sda5) which appears to be the only partition within the extended partition (sda4)

So, the upshot is that as far as Windows disk management is concerned, you have 5 primary partitions and a D: partition which is within an extended partition (which actually is a primary partition as well).
I have no idea how you have managed this. With Windows 7 on there it shouldn't be possible to do this! They should all be "dynamic disks" now.

It may be possible to delete sda3 (as per srs5694's suggestion) and sda2 and sda1 with fdisk then re-install Win 7 into that unallocated space - but I don't know whether that will work either.

I really don't know what to suggest, other than to re-install everything - which is drastic - but it would appear you are likely to have some problems in the future if you don't. Windows doesn't seem to have a problem with things. It doesn't even agree that sda6 and sda7 are within the extended partition - which Linux does! It's very messy!

As a minimum requirement I would recommend that you backup as much as you can from both Windows and Ubuntu - but I would not recommend you use disk images to do this, as they could just want to re-install the same disk layout that you now have.
Obviously re-installing everything would over-write everything on your hard drive ( including the recovery partition, so if you want that recovery data you should make recovery dvd's from within Windows, if you still can).
If you do decide to go down this route, please stop after re-installing Win 7 and take a look at how many primary partitions it has used!

If you then want advice regarding installing Ubuntu please come back here for it.


It would be interesting to see if anybody else has a less drastic solution.

---

### Post by aldee96 on 2010-12-30
Just like what i thought, delete all the partition and re-install everything
but could you tell me the steps to delete partition using fdisk command?
Is there any software that could help me backed up everything(recovery,and applications maybe)?

---

### Post by aldee96 on 2010-12-30
and could you understand why, after i changed the D:\ GPArted looks like this

---

### Post by Quackers on 2010-12-30
Have a look at srs5694's post (post #20) for details, or on his website perhaps.
I would imagine that gparted looks like that because it knows there is a problem with the partition table (the overlapping partitions).
Before you do anything else, could you please run the boot script again and post the new results in code tags please. This will give us an idea of whether the change you have made has impacted on the partition discrepancy. Thanks.

---

### Post by vanadium on 2010-12-30
Somewhat less drastic would be to reinstall only the contents of the extended partition. You would then delete logical partitions sda5, sda6 and sda7, and then the extended partition.

Then, you could reinstall Ubuntu, telling it to use all free space. If you still need extra ntfs space, then options are
1) to enlarge sda3, then after that install Ubuntu automatically in the remaining space
2) manually re-create (1) an extended partition (2) a logical ntfs partition (3) a logical root partition and (4) a logical swap. Then run Ubuntu install and tell it what partitions to use as root (probably that will be sda6) and swap (sda7).

Even less drastic, but no guarantee of success is try a manual resize of the partitions. I guess the idea posted before to reduce the size of sda3 is worth trying: it is not said that that would render sda4 inaccessible (though I do not know for sure).

Whatever route you take, you need to safeguard your data first. Even if there is no data loss expected, things can go wrong when you attempt repartitioning.

What is the software to backup everything? Since you are using a computer, you should already have a backup routine in place. You only need to care about your user data. These are irreplaceable. An operating system, in contrast, can be downloaded at will or can be bought in the worst case. Your customisations, you can do these again.

---

### Post by Quackers on 2010-12-30
That too is a possibility.
My only concern is the encroachment of the extended partition on the C: partition, according to the boot script output.
It's a puzzle, that's for sure.
Of paramount importance, after any deleting has been done, is that only 3 primary partitions are left, before installing any other OS.

---

### Post by coffeecat on 2010-12-30
> **aldee96 said:**
> and could you understand why, after i changed the D:\ GPArted looks like this

> **Quackers said:**
> Have a look at srs5694's post (post #20) for details, or on his website perhaps.

See here (written by srs5694):

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Although that link describes a different partition table problem, I think Quackers is right. It's probably because of your overlapping partitions. Gparted seems to bow out in such cases and show everything as unallocated. I've seen this myself. I don't think it's as a result (necessarily) of your changing D:.

@aldee96, whatever you do, may I suggest you look at the size of your Windows C: partition? At 24GB it's far too small for Windows 7. I know you've only got an 80GB drive, but W7 needs more space than 24GB.

---

### Post by aldee96 on 2010-12-31
> **Quackers said:**
> Have a look at srs5694's post (post #20) for details, or on his website perhaps.
I would imagine that gparted looks like that because it knows there is a problem with the partition table (the overlapping partitions).
Before you do anything else, could you please run the boot script again and post the new results in code tags please. This will give us an idea of whether the change you have made has impacted on the partition discrepancy. Thanks.


here's the RESULT1.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       50748768 sectors, but according to the info from 
                       fdisk, it has 50752246 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1               2,048    13,672,447    13,670,400  27 Hidden HPFS/NTFS
/dev/sda2    *     13,672,448    13,877,247       204,800   7 HPFS/NTFS
/dev/sda3          13,877,248    64,629,494    50,752,247   7 HPFS/NTFS
/dev/sda4          64,626,686   156,296,384    91,669,699   5 Extended
/dev/sda5          82,911,528   156,294,336    73,382,809   7 HPFS/NTFS
/dev/sda6          64,626,688    82,030,591    17,403,904  83 Linux
/dev/sda7          82,032,640    82,911,231       878,592  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4
/dev/sda3 overlaps with /dev/sda6

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        66E01C48E01C20BB                       ntfs       Recovery                      
/dev/sda2        52C0E118C0E102D9                       ntfs       System Reserved               
/dev/sda3        1C12E6DF12E6BD40                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0B8662EE5459F605                       ntfs                                     
/dev/sda6        585e205c-4317-4322-8651-b3fea0d198f7   ext4                                     
/dev/sda7        cc659d0a-af92-451d-9998-c695532ae27b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,commit=0)
/dev/sda3        /media/1C12E6DF12E6BD40  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /home/aldhika/ntfstest   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro  vga=775 splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro single  vga=775 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro  vga=775 splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=585e205c-4317-4322-8651-b3fea0d198f7 ro single  vga=775 splash
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 585e205c-4317-4322-8651-b3fea0d198f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 66e01c48e01c20bb
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 52c0e118c0e102d9
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

=============================== sda6/etc/fstab: ===============================

UUID=1C12E6DF12E6BD40 /media/1C12E6DF12E6BD40 ntfs-3g defaults 0 0
UUID=0B8662EE5459F605 /mnt ntfs-3g remount 0 0
UUID=585e205c-4317-4322-8651-b3fea0d198f7 / ext4 defaults 0 1
UUID=cc659d0a-af92-451d-9998-c695532ae27b swap swap sw 0 0

=================== sda6: Location of files loaded by Grub: ===================


  40.1GB: boot/grub/core.img
  36.1GB: boot/grub/grub.cfg
  34.7GB: boot/initrd.img-2.6.35-22-generic
  35.7GB: boot/initrd.img-2.6.35-24-generic
  40.1GB: boot/vmlinuz-2.6.35-22-generic
  39.7GB: boot/vmlinuz-2.6.35-24-generic
  35.7GB: initrd.img
  34.7GB: initrd.img.old
  39.7GB: vmlinuz
  40.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ac 8e e5 37 6e 67 c9 36  7d 33 15 b1 00 78 9e 4d  |...7ng.6}3...x.M|
00000010  cc e9 e6 78 3e db af f4  61 0b 62 c0 68 6f 24 bf  |...x>...a.b.ho$.|
00000020  07 85 48 6a 18 49 ba 6c  62 12 3b 7f 64 99 ba 95  |..Hj.I.lb.;.d...|
00000030  96 e5 9c c2 99 71 6e a4  64 77 f5 95 e7 4d aa 56  |.....qn.dw...M.V|
00000040  35 9a 0d ed fd 1c 90 45  4e 78 68 58 87 49 7c 67  |5......ENxhX.I|g|
00000050  8b 7a b0 31 e7 dd 47 1e  23 e8 34 c5 e2 8c f8 4b  |.z.1..G.#.4....K|
00000060  05 fe 6d 90 53 95 9b 95  da 55 00 8b 9c d6 ae 14  |..m.S....U......|
00000070  7d e7 8a ca 38 bd be 29  cf e5 58 c0 6c bf d6 66  |}...8..)..X.l..f|
00000080  00 1d e6 a9 e8 b4 d4 bb  bc 74 d5 63 df 86 f4 56  |.........t.c...V|
00000090  a3 4c 58 21 94 b0 c8 b3  d4 02 f2 1d 77 1e b9 2f  |.LX!........w../|
000000a0  37 1e 6c 09 97 cf 57 54  23 a8 73 8b a3 96 7a 2f  |7.l...WT#.s...z/|
000000b0  1c ea 8c ae 68 2f b0 18  ac 4e aa 5b db 89 6d 04  |....h/...N.[..m.|
000000c0  b2 d8 27 b6 1a e6 43 38  f8 b8 09 b6 44 ea c4 66  |..'...C8....D..f|
000000d0  19 ad 3d c2 3d 1a 66 ba  0d 8e 1a 0a a8 2a 1a 6d  |..=.=.f......*.m|
000000e0  2c 7d 0a c1 52 04 0f 05  af 2e bb d6 3e c5 b0 9d  |,}..R.......>...|
000000f0  c9 a2 85 ab 70 c9 19 52  67 0b ea 58 c8 87 51 e2  |....p..Rg..X..Q.|
00000100  b3 1c ca ec 86 44 d1 f0  13 82 02 d6 bb 09 75 a4  |.....D........u.|
00000110  55 35 35 28 48 c8 49 c7  64 6a 8e 85 11 6f 0b c7  |U55(H.I.dj...o..|
00000120  6d 17 f8 75 2c 7e ef 75  ca 28 4c 64 33 87 29 55  |m..u,~.u.(Ld3.)U|
00000130  9f 1e 60 f1 4e 4f 22 d9  d6 55 31 a4 61 56 51 71  |..`.NO"..U1.aVQq|
00000140  9e c4 38 9b 22 85 d9 d0  b5 d4 71 d2 59 c2 22 9f  |..8.".....q.Y.".|
00000150  f4 f4 7b 1b e6 43 51 67  cc 38 84 d8 20 62 bc fb  |..{..CQg.8.. b..|
00000160  aa 01 4e 9d ef e7 84 1a  42 c5 a0 4e 73 24 11 32  |..N.....B..Ns$.2|
00000170  d1 5c 85 4f 52 0a 23 a9  ce 36 cb 2e eb bb 4d fd  |.\.OR.#..6....M.|
00000180  6a 7b 65 c4 9d 87 aa 14  0d 1b 4b 62 84 d2 d4 16  |j{e.......Kb....|
00000190  e8 b0 c7 e1 90 70 de 0f  40 68 02 c5 87 4a ca e8  |.....p..@h...J..|
000001a0  8a 97 00 af b9 d4 3b d8  2b 0a ea cd 61 73 7d 37  |......;.+...as}7|
000001b0  87 0e ae ac 35 e9 c3 8d  4c bb 25 2e 07 bc 00 fe  |....5...L.%.....|
000001c0  ff ff 07 fe ff ff 2a 01  17 01 99 bb 5f 04 00 fe  |......*....._...|
000001d0  ff ff 05 2a f8 ff 01 00  00 00 01 90 09 01 00 00  |...*............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

