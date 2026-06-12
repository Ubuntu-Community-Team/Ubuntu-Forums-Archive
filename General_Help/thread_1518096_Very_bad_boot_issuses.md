---
title: "Very bad boot issuses"
date: 2010-06-26
forum: General Help
---

### Post by demon6 on 2010-06-26
**system specs:**
Operating System
 MS Windows 7 Home Premium 64-bit
CPU
 AMD Athlon II X2 245 29 °C
 Regor 45nm Technology
RAM
 4.0GB Dual-Channel DDR2 @ 401MHz  6-6-6-18
Motherboard
 MSI K9N6PGM2-V2 (MS-7309) (CPU1)
Graphics
 DELL S2209W @ 1920x1080
 ATI Radeon HD 4650 (XFX Pine Group) 50 °C
Hard Drives
 488.39GB Western Digital WDC WD5000AAJB-00UHA0 ATA Device (IDE) 40 °C
 488.39GB Western Digital WDC WD50 00AADS-00S9B SCSI Disk Device (IDE)
Optical Drives
 ATAPI DVD A  DH24AAS SCSI CdRom Device
Audio
 Realtek High Definition Audio
 
**WHAT I DID:**
I downloaded the 64 bit version of ubuntu 10.04 desktop ISO onto my HD in c:\ubuntu.
Then I shrank my C:\ from 201 GB free space and gave me a 31 GB partition which left c:\ at 180 GB.
Next I extracted the ISO and started wubi install.
Made the install for 29 GB to take up the partition.
Next after the install finished inside windows I rebooted and the install continued after choosing ubuntu from the list which showed WINDOWS 7 and UBUNTU.
The install continued fine and then restarted the computer once again.
I choose UBUNTU from the list once again and I get the GRUB menu.
It went to a blinking cursor top left corner of screen and then it gave me the error that /dev/sdb3 does not exist and it dropped to busybox shell.
I then EDITED the grub boot and changed /dev/sdb3 to /dev/sdb1 and it finaly booted into the GUI.
After I ran my driver activation and downloaded the updates, I also continued without installing grub which I suspect would have not allowed me to boot into windows 7 again.
I restarted ubuntu.
I had to change /dev/sdb3 to /dev/sdb1 which I thought would load UBUNTU.
 
This time I got the blinking cursor again but it only took a moment for it to give me a error and say the root disk did not exist this time and dropped to busybox shell again.
 
So that is where I am now and I have no idea how to continue.  I have read a few things on the forum about this but nothing is clear as to how to fix the problem.  I want to keep my LEGAL copy of windows 7 running because I have lots of things installed ATM otherwise I would switch over fully.  Sorry for the long post I hope some one can help.  Thanks.
 
Loyal ubuntu user for 3 years now by the way.

---

### Post by wilee-nilee on 2010-06-26
When you do a wubi install you don't build a partition it is just a file inside of windows that can be made to what size you want with the installer. I know this because I did a wubi install today just to have a copy of the boot script myself, and to know more about the wubi exsperience.

Two things post the bootscript in my signature, with the codetags as described. Do you have a install or recovery disc for W7

---

### Post by yetiman64 on 2010-06-26
Note a wubi install places Ubuntu into a file **within** the Windows partition. When done like this Ubuntu can be uninstalled from Windows from the Programs and features section of control panel just like a normal Windows program. Wubi is good for trialling Ubuntu but is not really the best form of dual booting (depends on your needs).

You have allowed free space on the drive for a side by side style of dual boot (as compared to wubi). Probably be best if you removed wubi install, burnt the Ubuntu iso to a live cd, boot from the live cd and test it without installing, then if you like it use the installer link on the live cd desktop to install to the free space you have already created.

---

### Post by demon6 on 2010-06-26
I will try the dual boot from the live disc this time around and see what happens.  But I am upset that 10.04 did not work like 9.x did with windows 7 with the wubi installer.  And now I suppose I have to put the windows boot loader back in after I do a full install of ubuntu.
 
Thanks for the quick replys.
 
If this issuse gets resolved I will be more pleased with the software.

---

### Post by dino99 on 2010-06-26
nothing is better than a real install

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by wilee-nilee on 2010-06-26
> **demon6 said:**
> I will try the dual boot from the live disc this time around and see what happens.  But I am upset that 10.04 did not work like 9.x did with windows 7 with the wubi installer.  And now I suppose I have to put the windows boot loader back in after I do a full install of ubuntu.
 
Thanks for the quick replys.
 
If this issuse gets resolved I will be more pleased with the software.

The only thing I see here is that you may have installed grub to a windows partition so a new install may still need a fix. So post the boot script so we can confirm that grub isn't in a windows partition and just see the setup. Personally I would hold off on the reinstall until you post the script you could possibly make it a worse situation.

---

### Post by yetiman64 on 2010-06-26
> **demon6 said:**
> I will try the dual boot from the live disc this time around and see what happens.  But I am upset that 10.04 did not work like 9.x did with windows 7 with the wubi installer.  And now I suppose I have to put the windows boot loader back in after I do a full install of ubuntu.
 
Thanks for the quick replys.
 
If this issuse gets resolved I will be more pleased with the software.

Do as wilee-nilee suggests with the script just to be on the safe side.

Though if you do go to a side by side install DON'T reinstall the Windows bootloader as grub will be doing the OS selection from the MBR of the drive.

Putting the Windows bootloader back in will kill your access to Ubuntu. Remember wubi and side by side installs are very different beasts.

---

### Post by Barafu Albino Cheetah on 2010-06-26
I advise you to read articles before trying to change anything else, because you obviously don't understand, how linux boot process works, and what it consists of. If you try it by guess, you will definitely join the hoards of users who lost thier data completely while trying to install Linux. 
There is nearly no difference how Koala and Lynx installations work.

---

### Post by demon6 on 2010-06-26
To tell you all the truth I have installed linux many times on many difernt computers and so I guess I need to read up on this new version of ubuntu.  This is my first time running into any major problems so could someone explain how to get the script to post on here please I am not good with commands and scripts as of yet.  Don't know where to look for that sort of thing.  I am all copy and past so far since my memory is not good.

---

### Post by wilee-nilee on 2010-06-26
> **demon6 said:**
> To tell you all the truth I have installed linux many times on many difernt computers and so I guess I need to read up on this new version of ubuntu.  This is my first time running into any major problems so could someone explain how to get the script to post on here please I am not good with commands and scripts as of yet.  Don't know where to look for that sort of thing.  I am all copy and past so far since my memory is not good.

Just click on the bootscript link in my signature and download it, then drag it or copy and paste it to your desktop then run this command in the terminal. Just copy and paste the command to the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

This will make another file on the desktop open it then copy the txt and paste it to a reply then highlight the txt and click on the # in the reply panel.

---

### Post by demon6 on 2010-06-26
I would but I can't get into ubuntu atm, I am on windows 7 since ubuntu will not boot :(

---

### Post by wilee-nilee on 2010-06-26
> **demon6 said:**
> I would but I can't get into ubuntu atm, I am on windows 7 since ubuntu will not boot :(

You will need a live cd to install and this bootscript can be run from a Ubuntu install or a live cd. Boot a Ubuntu live cd and follow the instructions, just come to the forums to copy and paste the script while still booted on the live cd.

---

### Post by demon6 on 2010-06-26
I said screw it and I uninstalled the wubi off windows and installed a fresh copy on my second partition and so far it seems to be running fine.  In the middle of the updates so if I get back on after they are finished I will post a happy face LOL.

---

### Post by wilee-nilee on 2010-06-26
> **demon6 said:**
> I said screw it and I uninstalled the wubi off windows and installed a fresh copy on my second partition and so far it seems to be running fine.  In the middle of the updates so if I get back on after they are finished I will post a happy face LOL.

I was just about to post that you were probably okay if you could boot windows, and I recognized you knew what your doing.

---

### Post by demon6 on 2010-06-26
everything has worked out nicely after the updates.  so real install GOOD, wubi winblows install BAD! LOL.

:guitar::lolflag::p

---

### Post by yetiman64 on 2010-06-26
> **demon6 said:**
>  wubi winblows install BAD! LOL. +1 agree here. ;)

If all is fine could you check out link #5 in my sig, thanks. cheers yetiman64

---

### Post by wilee-nilee on 2010-06-26
I did a wubi today just for the experience as I said. A real dual boot is much easier to deal with especially if you need to reload a bootloader into the mbr. Once a wubi gets messed up or the MS all hell can break loose.

---

### Post by demon6 on 2010-06-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   913,283,071   913,076,224   7 HPFS/NTFS
/dev/sda3         913,285,118   976,773,119    63,488,002   5 Extended
/dev/sda5         913,285,120   974,817,279    61,532,160  83 Linux
/dev/sda6         974,819,328   976,773,119     1,953,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BC98DC7298DC2D20                       ntfs       System Reserved               
/dev/sda2        FE84DE5F84DE19CB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6de93d38-32ed-4730-a918-99a0ee6f7ac8   ext4                                     
/dev/sda6        14d70f9e-77fb-4637-9f3f-8b9849b34d6e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A250C55550C53139                       ntfs       HD                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6de93d38-32ed-4730-a918-99a0ee6f7ac8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6de93d38-32ed-4730-a918-99a0ee6f7ac8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6de93d38-32ed-4730-a918-99a0ee6f7ac8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6de93d38-32ed-4730-a918-99a0ee6f7ac8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6de93d38-32ed-4730-a918-99a0ee6f7ac8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bc98dc7298dc2d20
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6de93d38-32ed-4730-a918-99a0ee6f7ac8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=14d70f9e-77fb-4637-9f3f-8b9849b34d6e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 487.0GB: boot/grub/core.img
 472.3GB: boot/grub/grub.cfg
 487.2GB: boot/initrd.img-2.6.32-21-generic
 487.1GB: boot/initrd.img-2.6.32-22-generic
 487.0GB: boot/vmlinuz-2.6.32-21-generic
 468.1GB: boot/vmlinuz-2.6.32-22-generic
 487.1GB: initrd.img
 487.2GB: initrd.img.old
 468.1GB: vmlinuz
 487.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  64 a8 73 9f 27 ce 12 5a  16 bb 61 21 1b 97 e7 47  |d.s.'..Z..a!...G|
00000010  4e 76 72 86 0e ae a9 8a  9c 77 ca ae 4d 7d 96 03  |Nvr......w..M}..|
00000020  f7 47 94 fe 88 8f 70 fd  53 97 d6 0a 5e ae 2b f6  |.G....p.S...^.+.|
00000030  b9 17 66 e2 37 72 04 ef  b7 1c d9 d2 68 91 b9 a0  |..f.7r......h...|
00000040  63 04 75 20 c7 6a 40 1d  6a cd 37 b1 eb 0b 53 fc  |c.u .j@.j.7...S.|
00000050  8a 12 a4 eb e4 cd 2a bf  d0 ad 49 91 f7 11 1d 53  |......*...I....S|
00000060  44 92 ef 1a cf f6 27 1b  bb 84 cf e6 1a 58 7c 6c  |D.....'......X|l|
00000070  0b b9 fd 42 da 1f 1c dd  b4 6e 6f 73 2d 52 40 43  |...B.....nos-R@C|
00000080  b2 9e 4d 7e a5 b6 f2 e9  ce ed 2f 05 4f 75 59 d7  |..M~....../.OuY.|
00000090  f5 69 34 7b f2 88 7c 3e  19 86 ac 73 2c 05 44 d1  |.i4{..|>...s,.D.|
000000a0  b9 97 4f d7 0e 41 2b 34  20 6b fa 63 67 e2 ee f3  |..O..A+4 k.cg...|
000000b0  80 f9 4e a8 83 80 7b 72  92 9b 4c 0f c2 88 f8 b8  |..N...{r..L.....|
000000c0  df df f6 9d 54 33 77 1d  e9 5b 74 c6 36 03 c8 9f  |....T3w..[t.6...|
000000d0  f9 33 07 3e 5f 9a 53 60  26 db ae b0 6e eb b8 db  |.3.>_.S`&...n...|
000000e0  ce 81 4f d4 66 0f 4f 6a  37 ce 07 ed 72 eb 46 71  |..O.f.Oj7...r.Fq|
000000f0  cf 4f 8e 4e 7b 2f 37 2b  9b 3b 21 a9 5c ed 8c 30  |.O.N{/7+.;!.\..0|
00000100  95 c0 47 27 bc a3 34 9f  d3 24 4b 16 49 1a 88 da  |..G'..4..$K.I...|
00000110  4a b3 a4 aa f6 fc 17 8f  ca 7e 34 e2 5e d8 68 db  |J........~4.^.h.|
00000120  66 99 dd 4d d3 3a 50 79  bb 10 1f 26 40 70 60 3a  |f..M.:Py...&@p`:|
00000130  29 3f 24 6f 75 de 1e 4a  05 6f a3 5b ef 2e 7c 04  |)?$ou..J.o.[..|.|
00000140  ba ef 73 3e 1d 22 27 77  4a 96 ae ae a8 56 0a 8e  |..s>."'wJ....V..|
00000150  8a 57 bb 6e 32 d9 75 39  66 88 a3 d1 1e d9 ab 5d  |.W.n2.u9f......]|
00000160  d4 1c f7 45 47 c1 de 03  87 76 82 4a a2 0b 72 02  |...EG....v.J..r.|
00000170  5f 81 cc 6f d0 94 9f f2  2d cb 62 6a 48 8a b5 71  |_..o....-.bjH..q|
00000180  26 28 d1 cb d9 b8 c9 3c  9f 26 ec 54 65 01 7a 0f  |&(.....<.&.Te.z.|
00000190  d1 ec ee 37 95 11 cb cf  c6 6a b4 d2 4d 28 af 9c  |...7.....j..M(..|
000001a0  c9 32 91 3f a1 2a 55 3e  82 08 18 83 39 14 99 ed  |.2.?.*U>....9...|
000001b0  7d be 01 95 82 59 88 30  e9 8e 02 ba ab 88 00 fe  |}....Y.0........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 aa 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e8  aa 03 00 d8 1d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

```

---

