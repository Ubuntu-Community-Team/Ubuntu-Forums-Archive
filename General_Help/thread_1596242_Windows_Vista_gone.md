---
title: "Windows Vista gone???"
date: 2010-10-14
forum: General Help
---

### Post by mixint27 on 2010-10-14
Guys...i believe i no longer have Vista. Please help me/guide me if possible..

I had installed 10.04 side by side with Vista. Now that we have 10.10 i wanted to do a fresh installation on my laptop. I wanted to do the same thing, install it side by side so what i did is i installed gparted and tried to erase/delete ubuntu 10.04 and leave windows on it. From what i remember, i did just that. I restarted my laptop and windows didnt come up...i got a grub error...i decided then to install ubuntu 10.10. i selected to install ubuntu side by side again with vista. During the installation, i received an error about a partition...i made a few clicks...after it was installing and it went smoothly.

Now when i restart my laptop...it does not give me the option for windows....how do i know if i still have windows on my laptop? According to Gparted i dont have it anymore...

Specs:
Dell E1505
2 gigs
80gb

---

### Post by conradin on 2010-10-14
looks gone to me. Well, maybe not but your certainly in the data recovery phase at this point. My recommendation is get a different hard drive to work from and start trying to recover file systems. As in do not write any thing else to the existing disk. 

Then start reading things like this:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

good luck!

---

### Post by mastablasta on 2010-10-14
> **mixint27 said:**
> ...i made a few clicks...
what kind of clicks?
 
from what it seems you removed Ubuntu but you haven't reinstalled the Vista MRB. hence partition was not recognised. you probably gave instructions that made the whole disk free for install and then installed ubuntu on it.
 
i hope you have some vista recovery CD as it seems you installed Ubuntu over your data and over Vista.
 
what i wonder is why didn't you just upgrade?

---

### Post by Quackers on 2010-10-14
Please download and run the boot infor script from the link below. Please copy/paste the contents of the results.txt file between code tags in your next reply (hit New Reply then click  on the # symbol to generate code tags).
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mixint27 on 2010-10-15
> **Quackers said:**
> Please download and run the boot infor script from the link below. Please copy/paste the contents of the results.txt file between code tags in your next reply (hit New Reply then click  on the # symbol to generate code tags).
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks for replying.

Here you go...it does not seem that i have windows..???

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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        63803435-b079-4a55-b12a-7511000ebebd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1bf2aee4-dc25-4cef-bb85-e4829881537b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
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
    search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=63803435-b079-4a55-b12a-7511000ebebd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=63803435-b079-4a55-b12a-7511000ebebd ro single 
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
    search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 63803435-b079-4a55-b12a-7511000ebebd
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
UUID=1bf2aee4-dc25-4cef-bb85-e4829881537b none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  73.1GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  30.5GB: boot/initrd.img-2.6.35-22-generic
  73.1GB: boot/vmlinuz-2.6.35-22-generic
  30.5GB: initrd.img
  73.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  20 f1 ff ff ff a3 c0 03  00 00 68 68 07 00 00 e9  | .........hh....|
00000010  10 f1 ff ff ff a3 c4 03  00 00 68 70 07 00 00 e9  |..........hp....|
00000020  00 f1 ff ff ff a3 c8 03  00 00 68 78 07 00 00 e9  |..........hx....|
00000030  f0 f0 ff ff ff a3 cc 03  00 00 68 80 07 00 00 e9  |..........h.....|
00000040  e0 f0 ff ff ff a3 d0 03  00 00 68 88 07 00 00 e9  |..........h.....|
00000050  d0 f0 ff ff ff a3 d4 03  00 00 68 90 07 00 00 e9  |..........h.....|
00000060  c0 f0 ff ff ff a3 d8 03  00 00 68 98 07 00 00 e9  |..........h.....|
00000070  b0 f0 ff ff ff a3 dc 03  00 00 68 a0 07 00 00 e9  |..........h.....|
00000080  a0 f0 ff ff ff a3 e0 03  00 00 68 a8 07 00 00 e9  |..........h.....|
00000090  90 f0 ff ff ff a3 e4 03  00 00 68 b0 07 00 00 e9  |..........h.....|
000000a0  80 f0 ff ff ff a3 e8 03  00 00 68 b8 07 00 00 e9  |..........h.....|
000000b0  70 f0 ff ff ff a3 ec 03  00 00 68 c0 07 00 00 e9  |p.........h.....|
000000c0  60 f0 ff ff ff a3 f0 03  00 00 68 c8 07 00 00 e9  |`.........h.....|
000000d0  50 f0 ff ff ff a3 f4 03  00 00 68 d0 07 00 00 e9  |P.........h.....|
000000e0  40 f0 ff ff ff a3 f8 03  00 00 68 d8 07 00 00 e9  |@.........h.....|
000000f0  30 f0 ff ff ff a3 fc 03  00 00 68 e0 07 00 00 e9  |0.........h.....|
00000100  20 f0 ff ff ff a3 00 04  00 00 68 e8 07 00 00 e9  | .........h.....|
00000110  10 f0 ff ff ff a3 04 04  00 00 68 f0 07 00 00 e9  |..........h.....|
00000120  00 f0 ff ff ff a3 08 04  00 00 68 f8 07 00 00 e9  |..........h.....|
00000130  f0 ef ff ff ff a3 0c 04  00 00 68 00 08 00 00 e9  |..........h.....|
00000140  e0 ef ff ff ff a3 10 04  00 00 68 08 08 00 00 e9  |..........h.....|
00000150  d0 ef ff ff ff a3 14 04  00 00 68 10 08 00 00 e9  |..........h.....|
00000160  c0 ef ff ff ff a3 18 04  00 00 68 18 08 00 00 e9  |..........h.....|
00000170  b0 ef ff ff ff a3 1c 04  00 00 68 20 08 00 00 e9  |..........h ....|
00000180  a0 ef ff ff ff a3 20 04  00 00 68 28 08 00 00 e9  |...... ...h(....|
00000190  90 ef ff ff ff a3 24 04  00 00 68 30 08 00 00 e9  |......$...h0....|
000001a0  80 ef ff ff ff a3 28 04  00 00 68 38 08 00 00 e9  |......(...h8....|
000001b0  70 ef ff ff ff a3 2c 04  00 00 68 40 08 00 00 fe  |p.....,...h@....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by mixint27 on 2010-10-15
> **mastablasta said:**
> what kind of clicks?
 
from what it seems you removed Ubuntu but you haven't reinstalled the Vista MRB. hence partition was not recognised. you probably gave instructions that made the whole disk free for install and then installed ubuntu on it.
 
i hope you have some vista recovery CD as it seems you installed Ubuntu over your data and over Vista.
 
what i wonder is why didn't you just upgrade?

Masta, i dont really remember what kind of clicks but i did the same thing when i installed 10.04 and it worked just fine.For some reason, it was kinda of different because i received a partition error; I  really dont remember what i did exactly. Im thinking i might have selected the wrong option but im sure i was doing everything right.

The reason i didnt upgrade was because i wanted everything "fresh" again. I honestly did not think this would happen since i did this before with 10.04

---

### Post by mixint27 on 2010-10-15
> **conradin said:**
> looks gone to me. Well, maybe not but your certainly in the data recovery phase at this point. My recommendation is get a different hard drive to work from and start trying to recover file systems. As in do not write any thing else to the existing disk. 

Then start reading things like this:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

good luck!

thanks for the link.

---

### Post by Rasa1111 on 2010-10-15
damn.

second one this week. lol

you could just look at it as a blessing i guess. :P
better than getting bent over it i suppose. 

why would you "install" gparted? 

it's already on the liveCD.

---

### Post by Quackers on 2010-10-15
Yep, no sign of Windows I'm afraid :-( It's been stomped on. Something obviously went wrong in the partitioning choosing phase.
You could maybe try Testdisk and see what it finds, but I fear the worst.
On the brighter side you've got a sweet looking Ubuntu install :-)

---

### Post by mixint27 on 2010-10-16
> **Rasa1111 said:**
> damn.

second one this week. lol

you could just look at it as a blessing i guess. :P
better than getting bent over it i suppose. 

why would you "install" gparted? 

it's already on the liveCD.

yeah i know its in the live cd...

im the second one? geez. oh well...

but i guess i could look at it as a blessing...i was not really using windows vista...i had it as a backup really; whats sad is i dont have office 2007 which was the only thing used in vista. my wife wants it back cuz of office only...



:mad::mad::mad::mad:

---

### Post by mixint27 on 2010-10-16
> **Quackers said:**
> Yep, no sign of Windows I'm afraid :-( It's been stomped on. Something obviously went wrong in the partitioning choosing phase.
You could maybe try Testdisk and see what it finds, but I fear the worst.
On the brighter side you've got a sweet looking Ubuntu install :-)

yes. i have a sweet looking ubuntu...cant complain

---

### Post by Quackers on 2010-10-16
Doesn't openoffice.org work for her?

---

### Post by mixint27 on 2010-10-16
she just does not like it...she prefers office. she just cant get used to it.

---

