---
title: "error: no such device /external Hd"
date: 2011-02-28
forum: General Help
---

### Post by Jonker on 2011-02-28
Hi there,  I had tried to install Ubuntu 10.10 on an external harddrive, the Laptop was running Vista. It all worked fine, but now, when the external hd isn't connected, I ge the message: error: no such device : ... grub rescue> the I put the ls command grub rescue> ls (hd0)(hdo,msdos3)(hd0,msdos)(hdmsdos1)  Now I just want to get Vista working again, without having to connect the hd.

---

### Post by sikander3786 on 2011-02-28
You installed Grub (Ubuntu bootloader) to the MBR of your Vista HDD whereas it needed to be installed to the external HDD instead.

What you need to do now is to run Startup Repair from Vista repair/install disc. You might need to run it 3 times before you actually start booting Vista successfully.

Then, connect your external HDD and boot an Ubuntu Live CD/USB and follow the instructions here to install Grub to the proper disk.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

If you need a Vista repair disc, grab one here. Its legit.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

If you can't figure out how to re-install Grub, post the output of bootinfoscript as per instructions here so we can give you exact commands to follow. Make sure your external HDD is connected while you run the script.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting the output, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by Jonker on 2011-03-01
Thanks. I have downloaded the ISo and burned it to disc. What should I do after booting Vista from the CD?

---

### Post by sikander3786 on 2011-03-01
Boot from the disc and perform a startup repair.

[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by Jonker on 2011-03-01
Thanks allot. The startup repair didn't work, so I put in the fixMBR command- it did it in a second, and everything is working fine now. I'll have a look with the boot configuration from the external hd and post it here, in case I have troubles. ( Or I'll post the skrypt results, because I'm not that experienced with Ubuntu). Thanks again!!!:D

---

### Post by Jonker on 2011-03-02
For the script; is it necessary to boot from the Ubuntu 10.10 live cd or could it also be an older version before grub 2?

---

### Post by sikander3786 on 2011-03-02
> **Jonker said:**
> For the script; is it necessary to boot from the Ubuntu 10.10 live cd or could it also be an older version before grub 2?
You can boot from _any_ Ubuntu Live CD for running the script. But for re-instal of Grub (if needed), you will need to boot a Live CD with Grub2 i.e, > 9.04 at least.

---

### Post by Jonker on 2011-03-02
ok. I'll try it out right now.

---

### Post by Jonker on 2011-03-02
OK, Here is the result from the script, booted with Ubuntu 10.10:
```
  [FONT=&quot]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

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

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   246,945,791   243,871,744   7 HPFS/NTFS
/dev/sda3         246,945,792   488,395,103   241,449,312   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2017 MB, 2017525248 bytes
64 heads, 63 sectors/track, 977 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   308,533,247   308,531,200  83 Linux
/dev/sdc2         308,535,294   321,671,167    13,135,874   5 Extended
/dev/sdc5         308,535,296   321,671,167    13,135,872  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3206F52706F4ECAB                       ntfs       WinRE                         
/dev/sda2        22A466ECA466C241                       ntfs       Vista                         
/dev/sda3        BEF6251AF624D485                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3895-6F97                              vfat       SANDISC                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        65d64a23-0b3f-4996-ac98-524886f846a0   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        0562dcec-8a1f-4c73-a014-d195b4a79c67   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/SANDISC           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/65d64a23-0b3f-4996-ac98-524886f846a0 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro   quiet splash
      initrd      /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      echo  'Loading Linux 2.6.35-25-generic-pae ...'
      linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro single 
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux16     /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux16     /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set 22a466eca466c241
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 144.0GB: boot/grub/core.img
 129.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-25-generic-pae
 144.0GB: boot/vmlinuz-2.6.35-25-generic-pae
    .5GB: initrd.img
 144.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  5f 12 dd cf ae dc b0 0b  f2 27 19 af 43 ff 00 84  |_........'..C...|
[/FONT][FONT=&quot]00000010  26 ea d2 46 8e 79 22 8c  8e c0 96 fd 71 5d 3c da  |&..F.y".....q]<.|
00000020  68 73 3d 59 e3 93 da c7  1a 90 53 3c 1e 7d 6b b1  |hs=Y......S<.}k.|
00000030  d7 74 88 ad 98 82 58 9e  15 46 38 a7 06 de fb 8e  |.t....X..F8.....|
00000040  c7 87 6b 97 32 2b 8e 78  38 15 df db f8 63 49 b8  |..k.2+.x8....cI.|
00000050  75 fb 54 06 45 04 9c 12  71 5a 5f b8 2d 74 47 80  |u.T.E...qZ_.-tG.|
[/FONT][FONT=&quot]00000060  ea 73 89 77 a9 39 09 de  be 9e 3e 11 f0 b0 04 43  |.s.w.9....>....C|
00000070  14 4b fe c8 ed 47 b5 6b  44 85 ca fa 9f 19 b2 cf  |.K...G.kD.......|
00000080  73 9c f6 ce 31 d4 d7 d1  fa ee 8f a7 21 db 12 02  |s...1.......!...|
00000090  e2 ad 4d b5 62 1c 5b 47  c9 3e 20 d0 75 ab f8 76  |..M.b.[G.> .u..v|
000000a0  24 7c 00 72 4d 7d 15 f6  27 01 95 d7 8a d1 54 70  |$|.rM}..'.....Tp|
000000b0  1a 5a 1f 13 69 ff 00 08  75 9b e9 d4 ca c6 3c 72  |.Z..i...u.....<r|
000000c0  14 77 fc eb ec 8b a8 16  32 85 00 2c 7d 28 95 49  |.w......2..,}(.I|
000000d0  31 72 69 a9 e2 16 3f 01  34 ed 45 55 af 24 77 01  |1ri...?.4.EU.$w.|
000000e0  ba 67 fc 2b e8 cd 3a 5b  99 46 30 3d 78 eb 59 ba  |.g.+..:[.F0=x.Y.|
000000f0  d2 7a 5c b7 4d 35 a1 e7  7a 07 c2 af 07 e8 4c 56  |.z\.M5..z.....LV|
00000100  3b 24 2f fd fc 73 5e c1  69 6f 97 e4 61 9b 8a 89  |;$/..s^.io..a...|
00000110  56 69 6b a8 24 af b1 c5  5d f8 4e df 61 11 c4 a0  |Vik.$...].N.a...|
[/FONT][FONT=&quot]00000120  74 1c 57 a8 c9 6e e3 86  43 8e e0 54 f3 e9 72 dc  |t.W..n..C..T..r.|
00000130  1b 7b 1e 18 74 45 83 e6  60 15 47 18 af 44 bb b2  |.{..tE..`.G..D..|
[/FONT][FONT=&quot]00000140  50 e4 14 e9 49 55 62 51  57 d4 f1 ad 43 4f 49 54  |P...IUbQW...COIT|
00000150  95 24 d7 73 a8 58 ee 04  64 29 3d fb 0a d2 33 b8  |.$.s.X..d)=...3.|
00000160  59 a4 78 a4 96 d3 c4 c4  13 c7 5c f7 ae c6 fb 4a  |Y.x.......\....J|
00000170  55 56 dc 41 c0 38 c5 69  19 bb d8 56 5b 9c 23 ae  |UV.A.8.i...V[.#.|
00000180  fc 36 4f 1c ee a5 b9 b5  48 86 ed bd 78 f6 35 a3  |.6O.....H...x.5.|
00000190  be dd 09 b1 97 aa 9d c8  48 e8 b8 aa b7 52 f9 08  |........H....R..|
000001a0  49 39 c7 38 aa 8d 93 b0  49 a6 8e 26 fa 02 dc 03  |I9.8....I..&....|
000001b0  f7 b3 d6 b7 ee 31 71 cb  00 47 5a bb 69 72 00 fe  |.....1q..GZ.ir..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 c8 00 00 00  |...........p....|
[/FONT][FONT=&quot]000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


 [/FONT]
  
```

---

### Post by Jonker on 2011-03-02
ah, and I had a 2gb memory stick connected to... incase this is showen in this file to.:D

---

### Post by sikander3786 on 2011-03-03
So, the recommended method of dual-boot is to let the Windows bootloader sit in Windows HDD and Grub in the Ubuntu HDD. We will install Grub to the MBR of your sdc HDD and then switch 'first boot device' in Bios to sdc and use Grub to dual boot. That way if Grub fails (very rare) you will at least be able to boot Windows independent of Grub.

Boot an Ubuntu Live CD 9.10, 10.04 or 10.10 and follow the commands below.

**Caution:** Your USB drive is being detected as 'sdb' at the moment. When you boot your PC to install Grub, just make sure that your Ubuntu HDD is still being detected as 'sdc' or the commands below won't work. You can check the drive info by typing,

```
sudo fdisk -l
```

And here are the command for re-installation of Grub. If sdc is not the Ubuntu HDD and say it is being detected as sdx this time, just replace the 'c' in following commands with 'x'.

```
sudo mount /dev/sdc1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]c[/COLOR]
```

For the second one it is just sdc without any integer.

Reboot and make your Ubuntu HDD the first boot device. If Windows is not listed in Grub menu, from installed Ubuntu's Terminal, run this command.

```
sudo update-grub
```

---

### Post by Jonker on 2011-03-03
Hello,
It all worked fine, thanks to your installation help. I'm very glad, and it is all working superb. Thanks, that you helped me sikander3786!!!

---

### Post by jobsworth on 2011-07-11
Hello sikander3786,
Thank you for your informative post. It saved me.
I run multiple disks in convoluted ways.
I have a 1TB internal drive with Ubuntu 11.04
and a 100GB external USB drive with Ubuntu 10.04.
The other day I reset the connections inside my machine to this
configuration and could not boot from the 1TB internal drive.
I booted off the external drive and did what you suggested and all works.
At first I thought that I had a power supply problem,
which is why I run my 2nd drive externally with its own power supply.
Then I thought that the new internal drive had failed.
SMART said it was ok. Somehow my GRUB(2) had been destroyed.
So easy when you know how.
Watch out for those American drones. I hope you are safe.

---

