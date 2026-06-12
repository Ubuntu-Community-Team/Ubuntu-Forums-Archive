---
title: "Need help in Editing my GRUB.cfg"
date: 2011-01-02
forum: General Help
---

### Post by staticjess on 2011-01-02
Hello Everyone, 
        To start off, I've been using linux as a plain user. I haven't got time to work around it since my job is time consuming as it is. When I left my computer at home my little brother seemed to have messed up my computer.

OS version: Ubuntu 11.04 Natty Narwhal and dual booted with windows xp
Problem: Missing Windows XP entry in my GRUB list. How do I edit and add my windows xp in it?

The menu.lst seems to be gone now and I don't know how to the new grub2.

Below are the list in my grub.cfg

menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

Thanks in advance.

Jess

---

### Post by wilee-nilee on 2011-01-02
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by staticjess on 2011-01-03
Here's the output wilee-nilee. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

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

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,797,952   346,595,327   141,797,376  83 Linux
/dev/sda3         346,597,374   488,396,799   141,799,426   5 Extended
/dev/sda5         346,597,376   486,443,007   139,845,632  83 Linux
/dev/sda6         486,445,056   488,396,799     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE2039952039658D                       ntfs                                     
/dev/sda2        69da1421-0db2-439a-9dce-bac48b02d244   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7e45b33f-ec0b-4799-9a76-7beddb08c14c   ext4                                     
/dev/sda6        a3184931-03c7-48c7-847a-51d2ee6de02d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sda1        /media/AE2039952039658D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=69da1421-0db2-439a-9dce-bac48b02d244 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7e45b33f-ec0b-4799-9a76-7beddb08c14c /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a3184931-03c7-48c7-847a-51d2ee6de02d none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 156.5GB: boot/grub/core.img
 156.5GB: boot/grub/grub.cfg
 105.4GB: boot/initrd.img-2.6.35-22-generic
 105.6GB: boot/initrd.img-2.6.35-23-generic
 156.5GB: boot/vmlinuz-2.6.35-22-generic
 156.5GB: boot/vmlinuz-2.6.35-23-generic
 105.6GB: initrd.img
 105.4GB: initrd.img.old
 156.5GB: vmlinuz
 156.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  7e 47 a4 42 c1 89 90 5d  2a 1c 6d a7 d6 3a 00 3e  |~G.B...]*.m..:.>|
00000010  70 07 fd 08 f6 3c 53 1d  4f e3 e1 72 f1 8a e2 80  |p....<S.O..r....|
00000020  d6 16 a2 d1 bb 83 de d2  63 34 9a d8 0e 38 9e fe  |........c4...8..|
00000030  3b 7b cf 5e f4 01 7f 68  6c c0 73 1f e5 92 1f 45  |;{.^...hl.s....E|
00000040  fd 99 2f 90 cb e2 17 2d  1c 20 e2 06 18 16 f2 c0  |../....-. ......|
00000050  d2 a6 8c a4 f4 a9 bc b0  04 a0 2a 5d 0f 41 46 57  |..........*].AFW|
00000060  fe d1 4a cf c1 d1 70 15  1d cb 3a a3 38 53 1d ac  |..J...p...:.8S..|
00000070  1f 90 e9 4c bd 11 40 e0  49 85 5f 6a 30 ed 05 3c  |...L..@.I._j0..<|
00000080  26 26 e7 4e dc a2 db d0  a5 5d 3c 95 e9 de 87 15  |&&.N.....]<.....|
00000090  a5 00 72 28 31 e1 59 b5  bf 8b 95 03 b3 14 1c ed  |..r(1.Y.........|
000000a0  43 72 e5 f5 3a eb ab c7  46 94 18 c4 e2 5a fd 70  |Cr..:...F....Z.p|
000000b0  4b 9a a4 fe 40 92 a1 97  c1 5a 6b 12 f7 44 62 bc  |K...@....Zk..Db.|
000000c0  1b 0f a4 38 75 40 1b ce  f9 71 01 fb 87 54 6a c0  |...8u@...q...Tj.|
000000d0  f8 a1 f5 88 72 48 73 e0  4f 12 4e 1f 3e 67 c3 c2  |....rHs.O.N.>g..|
000000e0  28 f4 34 1c 15 3e 3b e3  e3 2b 2d 38 5e 69 1b 71  |(.4..>;..+-8^i.q|
000000f0  53 42 75 dc a0 ba 85 d1  4d be 3a 65 d3 e5 45 dd  |SBu.....M.:e..E.|
00000100  f5 40 4b 59 61 a2 33 62  76 40 20 10 5d b3 31 24  |.@KYa.3bv@ .].1$|
00000110  3d bc 02 08 79 7e d0 38  5a 3a 78 5a 84 39 01 b8  |=...y~.8Z:xZ.9..|
00000120  af 0a b5 f3 ba 67 7e d9  e9 fe f7 29 1d 5c 8e 21  |.....g~....).\.!|
00000130  a4 4d 2a 85 3a a1 60 83  af 3e 8e dc b7 99 d6 b5  |.M*.:.`..>......|
00000140  e1 89 d4 9f 6c 7a 1f bd  e8 e1 d4 be 8e a3 3d 3a  |....lz........=:|
00000150  f5 d6 72 08 f1 43 08 42  11 2f cc 58 b2 00 d8 b5  |..r..C.B./.X....|
00000160  09 0c 7a 73 03 39 33 2e  f0 9a bd e6 26 6a ad 52  |..zs.93.....&j.R|
00000170  da de d2 67 47 ea 51 ce  3a bc fa d8 90 90 91 15  |...gG.Q.:.......|
00000180  16 b5 5b 3b 4d 3e ea 3b  8c 60 9a 0e 46 85 b3 bb  |..[;M>.;.`..F...|
00000190  bf 37 62 8b 1e a2 f6 1e  f2 9f a5 2c 47 3b 99 ae  |.7b........,G;..|
000001a0  5d ff 94 2b 4a d7 70 b2  1c cb 6c 9e 72 dc b7 83  |]..+J.p...l.r...|
000001b0  98 39 47 6a eb d7 15 d3  4f b5 d3 35 95 f7 00 fe  |.9Gj....O..5....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 55 08 00 fe  |............U...|
000001d0  ff ff 05 fe ff ff 02 e0  55 08 00 d0 1d 00 00 00  |........U.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-01-03
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini **/ntldr /NTDETECT.COM**

Your missing the highlighted files, you might wait for more opinions on this. Do you have a XP disc?

---

### Post by josephpmh on 2011-01-03
And, when your editing goes wrong, and you can't even get back in to restore the old grub.cfg, make sure you have a copy of [Rescatux]("http://www.supergrubdisk.org/") on hand.

After hours of trying to fix grub, I finally downloaded an iso of rescatux and within minutes, I was back up and running fine, thank you very much.

---

### Post by Rubi1200 on 2011-01-03
The file grub.cfg should NOT be edited directly; there is even a warning at the top of the file informing users of this.

@staticjess:
wilee-nilee is correct about the missing boot files. No amount of editing will change that fact.

First you need to restore the Windows bootloader/boot sector.

Once that is done, you can reinstall GRUB and you should be good to go.

By the way, you are not running 11.04, but 10.10; look at the results.

There is currently a bug in About Ubuntu which is showing the wrong version.

In a terminal:
```
cat /etc/*release
```
This gives the correct version information.

---

### Post by staticjess on 2011-01-03
> **wilee-nilee said:**
> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini **/ntldr /NTDETECT.COM**

Your missing the highlighted files, you might wait for more opinions on this. Do you have a XP disc?

Yes I have. How do I fill in the missing files?

---

### Post by staticjess on 2011-01-03
> **josephpmh said:**
> And, when your editing goes wrong, and you can't even get back in to restore the old grub.cfg, make sure you have a copy of [Rescatux]("http://www.supergrubdisk.org/") on hand.

After hours of trying to fix grub, I finally downloaded an iso of rescatux and within minutes, I was back up and running fine, thank you very much.

@josephpmh
What is it for? Do I need to download it for this case?

---

### Post by staticjess on 2011-01-03
**[SIZE=2][FONT=Times New Roman][B]I found the instructions below on how to recover the said files. Do you think I can be able to load my ubuntu once I do this? Bec. there are cases wherein when I try to fix my windows and my GRUB **bootloader is gone.[/FONT][/SIZE]
[/B]

[B]
[/B]

**Using the Windows Recovery Console**

  The Windows 2000 and Windows XP CDs supplied by Microsoft has a tool called the Recovery Console which can be used to repair   errors that prevent Windows XP from starting using the command line. OEM versions of Windows XP, including computers that were   supplied with Windows XP preinstalled, may not have this utility.
  
[LIST]
[*]Insert the **Windows CD** and start the computer.
[*]When the **Welcome to Setup** screen appears, press **R**.
[*]Type a number corresponding to the Windows installation you wish to repair (usually **1**) and press     **Enter**.
[*]When prompted, type the **administrator password** and press **Enter**.
[*]From the command prompt, copy NTLDR and NTDETECT.COM from the i386  folder of the CD to the root folder of the hard drive.     In the example commands given below, C: is the hard drive and D: is  the CD-ROM drive. You will need to change the drive letters     if appropriate:
    [B]COPY D:\I386\NTLDR C:\
    COPY D:\I386\NTDETECT.COM C:\[/B]
[*]Remove the Windows XP CD from the drive and **restart the computer**.
[/LIST]

---

### Post by wilee-nilee on 2011-01-03
Yay

---

### Post by staticjess on 2011-01-03
I already copied the NTDLR and NTDETECT.COM. The problem now is to add my windows xp in the bootloader section.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

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

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,797,952   346,595,327   141,797,376  83 Linux
/dev/sda3         346,597,374   488,396,799   141,799,426   5 Extended
/dev/sda5         346,597,376   486,443,007   139,845,632  83 Linux
/dev/sda6         486,445,056   488,396,799     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE2039952039658D                       ntfs                                     
/dev/sda2        69da1421-0db2-439a-9dce-bac48b02d244   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7e45b33f-ec0b-4799-9a76-7beddb08c14c   ext4                                     
/dev/sda6        a3184931-03c7-48c7-847a-51d2ee6de02d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sda1        /media/AE2039952039658D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/17072010          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=69da1421-0db2-439a-9dce-bac48b02d244 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 69da1421-0db2-439a-9dce-bac48b02d244
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=69da1421-0db2-439a-9dce-bac48b02d244 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7e45b33f-ec0b-4799-9a76-7beddb08c14c /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a3184931-03c7-48c7-847a-51d2ee6de02d none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 156.5GB: boot/grub/core.img
 156.5GB: boot/grub/grub.cfg
 105.4GB: boot/initrd.img-2.6.35-22-generic
 105.6GB: boot/initrd.img-2.6.35-23-generic
 156.5GB: boot/vmlinuz-2.6.35-22-generic
 156.5GB: boot/vmlinuz-2.6.35-23-generic
 105.6GB: initrd.img
 105.4GB: initrd.img.old
 156.5GB: vmlinuz
 156.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  7e 47 a4 42 c1 89 90 5d  2a 1c 6d a7 d6 3a 00 3e  |~G.B...]*.m..:.>|
00000010  70 07 fd 08 f6 3c 53 1d  4f e3 e1 72 f1 8a e2 80  |p....<S.O..r....|
00000020  d6 16 a2 d1 bb 83 de d2  63 34 9a d8 0e 38 9e fe  |........c4...8..|
00000030  3b 7b cf 5e f4 01 7f 68  6c c0 73 1f e5 92 1f 45  |;{.^...hl.s....E|
00000040  fd 99 2f 90 cb e2 17 2d  1c 20 e2 06 18 16 f2 c0  |../....-. ......|
00000050  d2 a6 8c a4 f4 a9 bc b0  04 a0 2a 5d 0f 41 46 57  |..........*].AFW|
00000060  fe d1 4a cf c1 d1 70 15  1d cb 3a a3 38 53 1d ac  |..J...p...:.8S..|
00000070  1f 90 e9 4c bd 11 40 e0  49 85 5f 6a 30 ed 05 3c  |...L..@.I._j0..<|
00000080  26 26 e7 4e dc a2 db d0  a5 5d 3c 95 e9 de 87 15  |&&.N.....]<.....|
00000090  a5 00 72 28 31 e1 59 b5  bf 8b 95 03 b3 14 1c ed  |..r(1.Y.........|
000000a0  43 72 e5 f5 3a eb ab c7  46 94 18 c4 e2 5a fd 70  |Cr..:...F....Z.p|
000000b0  4b 9a a4 fe 40 92 a1 97  c1 5a 6b 12 f7 44 62 bc  |K...@....Zk..Db.|
000000c0  1b 0f a4 38 75 40 1b ce  f9 71 01 fb 87 54 6a c0  |...8u@...q...Tj.|
000000d0  f8 a1 f5 88 72 48 73 e0  4f 12 4e 1f 3e 67 c3 c2  |....rHs.O.N.>g..|
000000e0  28 f4 34 1c 15 3e 3b e3  e3 2b 2d 38 5e 69 1b 71  |(.4..>;..+-8^i.q|
000000f0  53 42 75 dc a0 ba 85 d1  4d be 3a 65 d3 e5 45 dd  |SBu.....M.:e..E.|
00000100  f5 40 4b 59 61 a2 33 62  76 40 20 10 5d b3 31 24  |.@KYa.3bv@ .].1$|
00000110  3d bc 02 08 79 7e d0 38  5a 3a 78 5a 84 39 01 b8  |=...y~.8Z:xZ.9..|
00000120  af 0a b5 f3 ba 67 7e d9  e9 fe f7 29 1d 5c 8e 21  |.....g~....).\.!|
00000130  a4 4d 2a 85 3a a1 60 83  af 3e 8e dc b7 99 d6 b5  |.M*.:.`..>......|
00000140  e1 89 d4 9f 6c 7a 1f bd  e8 e1 d4 be 8e a3 3d 3a  |....lz........=:|
00000150  f5 d6 72 08 f1 43 08 42  11 2f cc 58 b2 00 d8 b5  |..r..C.B./.X....|
00000160  09 0c 7a 73 03 39 33 2e  f0 9a bd e6 26 6a ad 52  |..zs.93.....&j.R|
00000170  da de d2 67 47 ea 51 ce  3a bc fa d8 90 90 91 15  |...gG.Q.:.......|
00000180  16 b5 5b 3b 4d 3e ea 3b  8c 60 9a 0e 46 85 b3 bb  |..[;M>.;.`..F...|
00000190  bf 37 62 8b 1e a2 f6 1e  f2 9f a5 2c 47 3b 99 ae  |.7b........,G;..|
000001a0  5d ff 94 2b 4a d7 70 b2  1c cb 6c 9e 72 dc b7 83  |]..+J.p...l.r...|
000001b0  98 39 47 6a eb d7 15 d3  4f b5 d3 35 95 f7 00 fe  |.9Gj....O..5....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 55 08 00 fe  |............U...|
000001d0  ff ff 05 fe ff ff 02 e0  55 08 00 d0 1d 00 00 00  |........U.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-01-03
Have you tried in Ubuntu
sudo update-grub.

---

### Post by staticjess on 2011-01-03
[@wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")
Your one of the reasons why the community and the OS of ubuntu is a live and kicking. That solved my problem. I apologize for being so ignorant :(

---

### Post by staticjess on 2011-01-03
Now how do I change this thread to [SOLVED]?

---

### Post by wilee-nilee on 2011-01-03
> **staticjess said:**
> [@wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")
Your one of the reasons why the community and the OS of ubuntu is a live and kicking. That solved my problem. I apologize for being so ignorant :(

Actually you helped me with that reloading the files post I saved that in my cheat file, this was a group effort.:)

the solved is in the thread tools dropdown, if your logged in.

If you had run the fixmbr command you would of just had to reload grub to the mbr, I can understand your worry with adding the missing files back. Those are in the sda1 partition the mbr is sda.

---

