---
title: "Ubuntu bypassing my BIOS?"
date: 2010-09-29
forum: General Help
---

### Post by dwilbank on 2010-09-29
Hi.
I only recently installed Ubuntu on my Win 7 desktop computer.
Normally when I reboot, I see the splash screen for my Gigabyte motherboard, along with some messages from my BIOS.
Then I get a choice whether to boot into Win 7, or Ubuntu.

This morning, I had no choice.
Even when I power completely off and start up the conputer, it skips absolutely everything and boots into Ubuntu. Even the LEDs inside my computer blink differently.

Does the fact that I'm no longer seeing the BIOS or motherboard splash screen mean I have hardware damage?

For a while, I assumed that the MBR record (I'm new at this) of the Win 7 install was corrupted, and I tried to follow some instructions from Lifehacker about downloading ms-sys.
But even then, the cmd window said it couldn't find ms-sys on E:
I have no idea what it means by "E:"
I thought ms-sys was supposed to be downloaded from some "universal" software repository...

So basically, I'm asking if it is normal Ubuntu behavior to skip the BIOS and all that.

Thanks for any hints.

---

### Post by garvinrick4 on 2010-09-29
Ubuntu or most all grubs default is to not show grub when only one O.S. present.
See whats available in grub menu. Open a terminal in Ubuntu and:
```
grep menuentry /boot/grub/grub.cfg
```To see what is on your hard drive.
```
sudo fdisk -l 
```(lower case L)
fix GRUB_TIMEOUT IF SET TO O (should be an integer like 10 for 10 seconds)
```
gksudo gedit /etc/default/grub
```
must run this after changing and saving anything in grub
```
sudo update-grub
```

---

### Post by dwilbank on 2010-09-29
so my Windows install was corrupt...

thanks - will try all this and see what happens!

---

### Post by coffeecat on 2010-09-29
> **dwilbank said:**
> so my Windows install was corrupt...

Not necessarily. When you switch on a computer it goes through the BIOS POST before grub is invoked. So if you don't see your POST screen and grub behaviour has changed it looks as though there are two (possibly unrelated) issues.

Before you do anything, to see how grub and your partitions are set up, boot into Ubuntu and go to this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Run the bootinfo script and post the contents of the RESULTS.txt file. That contains your grub.cfg file, output of fdisk, blkids and a whole load more useful information.

---

### Post by dwilbank on 2010-09-29
Here's what I got.  My timeout was 10 seconds... Should I change GRUB HIDDEN TIMEOUT QUIET to false?    GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""

---

### Post by dwilbank on 2010-09-29
Thanks Mr Coffeecat. I ran the script. Here are the results. It was fun, but I have no idea what most of it means yet.

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /Windows/System32/winload.exe /ntldr 
                       /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,903,849,159 2,903,849,097   7 HPFS/NTFS
/dev/sda2       2,903,851,006 2,930,276,351    26,425,346   5 Extended
/dev/sda5       2,903,851,008 2,929,068,031    25,217,024  83 Linux
/dev/sda6       2,929,070,080 2,930,276,351     1,206,272  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   145,211,534   145,211,472   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   293,044,223   293,042,176   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        20A43AE7A43ABF5A                       ntfs       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5db80895-1894-4cb0-a22f-9874d43bd3c0   ext4                                     
/dev/sda6        a9c852e2-b244-412e-a58d-1f42d244b6d1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        802030192030191C                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9C04C17504C15346                       ntfs       F                             
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
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
search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5db80895-1894-4cb0-a22f-9874d43bd3c0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5db80895-1894-4cb0-a22f-9874d43bd3c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5db80895-1894-4cb0-a22f-9874d43bd3c0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5db80895-1894-4cb0-a22f-9874d43bd3c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5db80895-1894-4cb0-a22f-9874d43bd3c0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 20a43ae7a43abf5a
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 802030192030191c
    drivemap -s (hd0) ${root}
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
UUID=5db80895-1894-4cb0-a22f-9874d43bd3c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a9c852e2-b244-412e-a58d-1f42d244b6d1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


1497.7GB: boot/grub/core.img
1498.0GB: boot/grub/grub.cfg
1497.8GB: boot/initrd.img-2.6.32-21-generic
1498.2GB: boot/initrd.img-2.6.32-24-generic
1486.9GB: boot/vmlinuz-2.6.32-21-generic
1498.1GB: boot/vmlinuz-2.6.32-24-generic
1498.2GB: initrd.img
1497.8GB: initrd.img.old
1498.1GB: vmlinuz
1486.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3a 18 09 6e 27 25 73 25  63 39 14 f9 ed 52 09 a8  |:..n'%s%c9...R..|
00000010  e1 ce 66 c9 4e ca b4 b1  a8 3a 95 10 75 ab b4 be  |..f.N....:..u...|
00000020  af fd b2 e3 28 0b 95 32  0d 56 2c 6f b2 32 49 ab  |....(..2.V,o.2I.|
00000030  50 e8 3f fc 9a 14 aa 72  86 4e 9e 94 34 58 6f 86  |P.?....r.N..4Xo.|
00000040  12 1f 62 df 36 4f a8 30  5d 57 33 4d 98 1e 52 29  |..b.6O.0]W3M..R)|
00000050  a0 89 58 c8 e4 ca cc 19  37 bc 93 ba 6b ac 22 59  |..X.....7...k."Y|
00000060  16 b7 47 07 1f 00 ad 42  09 00 32 3b f0 34 82 84  |..G....B..2;.4..|
00000070  96 b2 af 9b 5f 95 5e 06  a0 fa 4f 7d ff 9c 4f 3e  |...._.^...O}..O>|
00000080  b1 f9 08 bb 0e 43 53 4f  40 c6 c6 89 4d bc aa fd  |.....CSO@...M...|
00000090  a6 b2 99 54 f7 25 5f f6  5b 1e 68 00 a4 10 09 79  |...T.%_.[.h....y|
000000a0  cb c7 a7 af 47 93 e5 f4  e8 78 c9 fe 59 4e 98 b3  |....G....x..YN..|
000000b0  b2 67 cd 99 7d 5b 43 c1  be 9e 50 68 ac 12 d4 82  |.g..}[C...Ph....|
000000c0  50 83 1b ac 52 c7 ab 54  11 27 5d 5c 55 43 e9 4e  |P...R..T.']\UC.N|
000000d0  b9 a0 0c 87 1a 28 c4 a3  32 50 5b 49 0e 6b 44 92  |.....(..2P[I.kD.|
000000e0  14 5c 1e 1c bb b4 ed f3  aa 7d e3 2f a6 45 b7 ba  |.\.......}./.E..|
000000f0  e6 0b a1 83 07 cf 20 a7  ee bd 9d 2a b7 e5 32 17  |...... ....*..2.|
00000100  68 87 ea ee 9a 16 7e 59  a0 1e f4 cd d9 58 e4 54  |h.....~Y.....X.T|
00000110  3e 29 5b 50 d0 67 5f f7  f5 ce b9 4c 88 f7 5d 6e  |>)[P.g_....L..]n|
00000120  b3 a9 e5 e5 a4 d8 22 6f  76 25 45 f9 71 36 41 66  |......"ov%E.q6Af|
00000130  d8 1d 89 5a 7d 5f 61 af  98 82 a0 7f 87 3b 5f 25  |...Z}_a......;_%|
00000140  d1 fa 1d d1 cd 66 71 a5  7b df e5 32 af 6d b1 01  |.....fq.{..2.m..|
00000150  b6 45 ee 70 b5 0c 95 7f  a8 81 a9 33 25 e7 d4 8d  |.E.p.......3%...|
00000160  29 03 3f 46 dd d9 d8 d5  fb f2 b9 24 b1 ef f2 55  |).?F.......$...U|
00000170  e2 a7 dc e0 7d 3d c4 5e  7e f1 cc e5 43 ed 0c a7  |....}=.^~...C...|
00000180  4a 80 6c e2 6b 9e aa 9e  c5 5d a2 3d 5a d4 ca aa  |J.l.k....].=Z...|
00000190  32 7a a9 6e 56 41 7c de  86 56 5f b1 00 6e a0 b1  |2z.nVA|..V_..n..|
000001a0  3d c4 b9 3e ae fc 57 7a  29 f8 06 8b 93 5a 35 2a  |=..>..Wz)....Z5*|
000001b0  10 c9 10 45 fe 7a 01 1d  1b 67 d1 81 02 c7 00 fe  |...E.z...g......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 80 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  80 01 00 70 12 00 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by coffeecat on 2010-09-29
> **dwilbank said:**
> Here's what I got.

Perhaps you missed my post. Run that script otherwise we're groping in the dark.

**Edit:**oh, you have, but it's unreadable. Edit your post, highlight the script output and click on the # button to enclose it in code brackets to make it readable.

---

### Post by dwilbank on 2010-09-29
I fixed the results list now.
And I wonder why WinXP is on one of the partitions.
I never wanted it there...

---

### Post by coffeecat on 2010-09-29
> **dwilbank said:**
> And I wonder why WinXP is on one of the partitions.
I never wanted it there...

Well...

> sdb1:________________________________________________________________________      File system:       ntfs     
Boot sector type:  Windows XP     
Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows 7     
Boot files/dirs:   /boot.ini /Windows/System32/winload.exe /ntldr                         /NTDETECT.COMIt's picked up ntldr which, iirc, is part of the XP bootloader. Vista and W7 use something different. What do you think is on sdb1?

As far as I can see there is nothing wrong with your partitions, your grub install or grub.cfg, but I'll have a closer look later. I need to reply now and then do some other things.

Which means that grub *should* be offering you both Ubuntu and Windows 7 in the menu. But for now I'd like to go back to the missing POST screen. That's not right. I wonder if something has happened to your BIOS and that this is affecting grub somehow. You should be able to reset the BIOS back to defaults using a jumper on the motherboard. Can you do this? So long as you never set  any particularly complicated options in the BIOS, this would be worth doing.

I will take a closer look at the RESULTS.txt output later in case I missed something.

---

### Post by dwilbank on 2010-09-29
a jumper on the motherboard?

never done it, but found some instructions online...

hope all these parts are accessible without completely taking apart my puter...

thx though

---

### Post by coffeecat on 2010-09-29
OK, I've has a closer look at your RESULTS.txt and the rest of the thread and I still can't find anything wrong with grub.cfg, but I have found a few curiosities.

> **dwilbank said:**
> Then I get a choice whether to boot into Win 7, or Ubuntu.

That would be the grub menu. However, your grub.cfg (see below) is showing an entry for XP on sdb1 as well, even though you were wondering why XP is on one of your partitions.

> **dwilbank said:**
> Here's what I got.  My timeout was 10 seconds... Should I change GRUB HIDDEN TIMEOUT QUIET to false?    GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""

That was useful. That's your /etc/default/grub file and it is showing the default entries. That's OK and doesn't need changing.

> **dwilbank said:**
>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

Grub is correctly installed on sda, but there is also evidence of Windows once being on both the sdb and sdc drives (and your system seems to think that a full XP is on sdb1). The Windows MBR is still in the MBR of both sdb and sdc. It isn't doing any harm, but neither is it doing anything at all.

Now these are the two entries for Windows:

> **dwilbank said:**
> 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 20a43ae7a43abf5a
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 802030192030191c
    drivemap -s (hd0) ${root}
    chainloader +1
}

When you were getting the grub menu, are you sure you weren't seeing 2 Windows menu entries as in the quotes in the menuentry lines below all the Ubuntu menu entries?

> **dwilbank said:**
> a jumper on the motherboard?

never done it, but found some instructions online...

hope all these parts are accessible without completely taking apart my puter...

thx though

Should be easily found. Make sure the instructions are for your particular motherboard. The instructions are fairly clear in the motherboard manuals for all the motherboards I've owned. And ground yourself before you touch any component. One spark of static can kill them.

To recap. Your grub menu *should* be displaying, and should be displaying four Ubuntu entries - one normal and one recovery mode entry for each of two kernels - then two memtest entries and lastly an entry for Windows 7 and an entry for Windows XP. There is no "hiddenmenu" command in grub.cfg and the timeout is 10 seconds. This has to be a BIOS issue, although frankly I'm puzzled. If the BIOS is not POSTing then the machine shoudn't be able to boot up at all.

---

### Post by dwilbank on 2010-09-29
Thx.
I'll read up on all this stuff.

But meanwhile,
If I put in my Win7 DVD and choose "repair", do you foresee any horrible results?
Does the presence of Ubuntu complicate things?

---

### Post by dwilbank on 2010-09-29
When I  had the bootloader, I did see XP and multiple versions of Ubuntu, which I didn't understand...

Thought the XP was a mistake.

---

### Post by dwilbank on 2010-09-29
Turns out Windows got corrupted during a forced 2am update.

Thanks Microsoft.

A system restore to the day before fixed it.

---

### Post by CharlesA on 2010-09-29
> **dwilbank said:**
> Turns out Windows got corrupted during a forced 2am update.

Thanks Microsoft.

A system restore to the day before fixed it.

That's lame. Glad you got it figured out.

Don't forget to mark the thread as solved from thread tools.

---

