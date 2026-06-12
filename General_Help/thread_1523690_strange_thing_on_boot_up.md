---
title: "strange thing on boot up"
date: 2010-07-04
forum: General Help
---

### Post by kduffy101 on 2010-07-04
hi, just switched my pc on + it wood not boot uo passed the bios page,
after about 15 tries i put live cd in+was trying to boot from cd,eventually i got it to boot up,it was like it was doing a fresh install.
i only got to the partioning dard drive bit,then it was as if it rebooted then its started up but ive no favourites,bookmarks,history or anything i had saved to desktop.ive got 2 folders on desktop,1 says examples+other says install ubuntu 10.04 lts.
can anyone help me please?

---

### Post by kduffy101 on 2010-07-04
ok im going to do a fresh install

---

### Post by Rubi1200 on 2010-07-04
> **kduffy101 said:**
> hi, just switched my pc on + it wood not boot uo passed the bios page,
after about 15 tries i put live cd in+was trying to boot from cd,eventually i got it to boot up,it was like it was doing a fresh install.
i only got to the partioning dard drive bit,then it was as if it rebooted then its started up but ive no favourites,bookmarks,history or anything i had saved to desktop.ive got 2 folders on desktop,1 says examples+other says install ubuntu 10.04 lts.
can anyone help me please?

It sounds as if you are currently looking at the live desktop in Ubuntu.

As a precaution, click on the link at the bottom of my post. Follow the instructions and post the results back here.

By the way, regarding your original problem; have you checked all your cables are properly plugged in? What is the boot sequence in BIOS?

Also, a bit more information about your setup would be helpful. The more we know, the better we can help you.

I just saw your post above: please consider backing things up before a fresh install and/or post the results of the script I linked to.

---

### Post by kduffy101 on 2010-07-04
when it ask about opening file it wont let me.

---

### Post by kduffy101 on 2010-07-04
i think i done it,but when i copy+paste the results im getting this message...
You have included 22 images in your message.  You are limited to using 8  images so please go back and correct the problem and then continue  again. 

Images include use of smilies, the BB code [img] tag and HTML  <img> tags. The use of these is all subject to them being enabled  by the administrator.
im not even sure if this is what i was meant to do.

---

### Post by Rubi1200 on 2010-07-04
The results should be a simple text format. Open it on Ubuntu with gedit (available in Accessories) then Ctrl A Ctrl C and then post it back here. Please wrap the text with the code tag # you see at the top of the message box.

---

### Post by kduffy101 on 2010-07-04
ok ive got the boot script,when i press ctrl+a it highlights all,then when i press ctrl+c the page goes white with c showing.
im new to ubunta+im not much of a techie,im not sure about the tag thingy...

---

### Post by Rubi1200 on 2010-07-04
> **kduffy101 said:**
> ok ive got the boot script,when i press ctrl+a it highlights all,then when i press ctrl+c the page goes white with c showing.
im new to ubunta+im not much of a techie,im not sure about the tag thingy...

You need to put the script on the Desktop in Ubuntu and then go to Applications > Accessories > Terminal and run the following code:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

When it is finished you should see a file called RESULTS.txt on the Desktop.

Open it and copy and paste the content back here.

---

### Post by kduffy101 on 2010-07-04
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   231,454,719   231,452,672  83 Linux
/dev/sda2         231,456,766   240,119,807     8,663,042   5 Extended
/dev/sda5         231,456,768   240,119,807     8,663,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        061cd768-821d-446f-8174-5d17d933fcaf   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0938a1cc-4cb0-4c73-b7dc-00b7b10a7d35   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=061cd768-821d-446f-8174-5d17d933fcaf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=061cd768-821d-446f-8174-5d17d933fcaf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 061cd768-821d-446f-8174-5d17d933fcaf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=061cd768-821d-446f-8174-5d17d933fcaf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0938a1cc-4cb0-4c73-b7dc-00b7b10a7d35 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
 116.2GB: boot/initrd.img-2.6.32-21-generic
 116.1GB: boot/vmlinuz-2.6.32-21-generic
 116.2GB: initrd.img
 116.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  39 00 00 00 12 00 0a 00  ee f0 00 00 b0 0c 08 00  |9...............|
00000010  61 00 00 00 12 00 0a 00  58 b0 00 00 00 00 00 00  |a.......X.......|
00000020  7f 00 00 00 12 00 00 00  fe 68 01 00 40 c0 13 00  |.........h..@...|
00000030  28 00 00 00 21 00 13 00  85 bd 00 00 a0 5d 06 00  |(...!........]..|
00000040  08 00 00 00 12 00 0a 00  0a bc 00 00 00 00 00 00  |................|
00000050  4e 00 00 00 12 00 00 00  f0 71 01 00 30 c7 0d 00  |N........q..0...|
00000060  42 00 00 00 22 00 0a 00  13 2b 01 00 20 c5 0c 00  |B..."....+.. ...|
00000070  1d 00 00 00 12 00 0a 00  21 25 01 00 20 82 0c 00  |........!%.. ...|
00000080  76 00 00 00 12 00 0a 00  97 52 00 00 00 bb 05 00  |v........R......|
00000090  39 00 00 00 22 00 0a 00  6c a5 00 00 00 00 00 00  |9..."...l.......|
000000a0  69 00 00 00 12 00 00 00  53 3a 00 00 50 29 05 00  |i.......S:..P)..|
000000b0  32 00 00 00 22 00 0a 00  b8 73 00 00 90 c5 05 00  |2..."....s......|
000000c0  2d 00 00 00 22 00 0a 00  b7 20 01 00 60 12 0f 00  |-...".... ..`...|
000000d0  08 00 00 00 12 00 0a 00  3f f8 00 00 20 48 08 00  |........?... H..|
000000e0  78 02 00 00 12 00 0a 00  9a fc 00 00 d0 7e 08 00  |x............~..|
000000f0  88 00 00 00 12 00 0a 00  3e fc 00 00 f0 78 08 00  |........>....x..|
00000100  6b 00 00 00 12 00 0a 00  65 74 01 00 00 e1 0d 00  |k.......et......|
00000110  cd 03 00 00 22 00 0a 00  8f 1e 01 00 80 05 0c 00  |...."...........|
00000120  54 00 00 00 12 00 0a 00  ee 3e 00 00 c0 2b 05 00  |T........>...+..|
00000130  40 00 00 00 22 00 0a 00  12 04 01 00 90 10 09 00  |@..."...........|
00000140  2a 00 00 00 12 00 0a 00  ac 47 01 00 70 31 0d 00  |*........G..p1..|
00000150  3c 01 00 00 12 00 0a 00  8e d2 00 00 50 8f 06 00  |<...........P...|
00000160  44 00 00 00 12 00 0a 00  37 47 00 00 00 00 00 00  |D.......7G......|
00000170  0f 00 00 00 12 00 00 00  ec 9b 01 00 00 00 00 00  |................|
00000180  3a 00 00 00 12 00 00 00  8c 05 00 00 00 46 14 00  |:............F..|
00000190  04 00 00 00 11 00 18 00  d7 40 01 00 00 00 00 00  |.........@......|
000001a0  33 00 00 00 12 00 00 00  dd 00 01 00 00 00 00 00  |3...............|
000001b0  3e 00 00 00 12 00 00 00  cc 18 00 00 50 33 00 fe  |>...........P3..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 84 00 00 00  |...........0....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2010-07-04
Initially, there does not seem to be an issue. 

But I wonder about this?

> Unknown BootLoader  on sda2

Also, do you normally have another drive plugged in, an external HDD with Windows maybe?

Additionally, could there be a problem with BIOS?

I suggest you wait until one of the more experienced forums members comes along with advice on how to resolve this.

Hang in there please!

:)

---

### Post by kduffy101 on 2010-07-04
thanks for your help rubi,
no ive no external hd plugged in

---

