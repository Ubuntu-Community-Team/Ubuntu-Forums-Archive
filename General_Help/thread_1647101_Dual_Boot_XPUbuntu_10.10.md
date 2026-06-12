---
title: "Dual Boot XP/Ubuntu 10.10"
date: 2010-12-16
forum: General Help
---

### Post by nikka08 on 2010-12-16
Hello all. New to the community as well as Linux. I followed a tutorial to install XP across my entire HDD. I installed Ubuntu 10.10 "Alongside another OS". Ubuntu loads fine, but when trying to load XP, the boot screen shows up, but then the computer restarts and returns to the GRUB menu.

I saw some threads on this site and tried to type:

sudo gedit /boot/grub/menu.lst

in the terminal. It returned a blank text document so I'm not sure if that information was outdated. I then typed:

sudo fdisk -l

and got this:

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099397

Device        Boot                       Start                     End                 Blocks               Id     System
/dev/sdb1       *                                1                 11024            88544079+             7         HPFS/NTFS
/dev/sdb2                                 11024                 30402         155654145               5          Extended
/dev/sdb5                                 11024                 29610          14295104               83         Linux
/dev/sdb6                                  29610                 30402         6358016                 82       Linux swap / Solaris


Not sure what any of this means, but I sure hope someone else does. I would say forget XP, but it's hard to let go of some of the games and software I use. I appreciate any responses, thank you.

EDIT: i tried to format the table as it appeared, but the forum corrected the extra spaces, I apologize.

---

### Post by oldfred on 2010-12-16
Formating is preserved if you use code tags which are the # sign in the menu above your message. Highlight and click on #.

So we can see your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by nikka08 on 2010-12-16
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

/dev/sda1    *             63   177,088,221   177,088,159   7 HPFS/NTFS
/dev/sda2         177,088,510   488,396,799   311,308,290   5 Extended
/dev/sda5         177,088,512   475,678,719   298,590,208  83 Linux
/dev/sda6         475,680,768   488,396,799    12,716,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9E502DA3502D835F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a0030333-5502-4a51-82ab-46a86112e0b1   ext4                                     
/dev/sda6        bca363ae-dee7-41d8-baf4-ad72e40ef304   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a0030333-5502-4a51-82ab-46a86112e0b1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a0030333-5502-4a51-82ab-46a86112e0b1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a0030333-5502-4a51-82ab-46a86112e0b1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a0030333-5502-4a51-82ab-46a86112e0b1 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set a0030333-5502-4a51-82ab-46a86112e0b1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e502da3502d835f
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=a0030333-5502-4a51-82ab-46a86112e0b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bca363ae-dee7-41d8-baf4-ad72e40ef304 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 150.9GB: boot/grub/core.img
 150.9GB: boot/grub/grub.cfg
  91.6GB: boot/initrd.img-2.6.35-22-generic
  91.7GB: boot/initrd.img-2.6.35-23-generic
 151.0GB: boot/vmlinuz-2.6.35-22-generic
 151.0GB: boot/vmlinuz-2.6.35-23-generic
  91.7GB: initrd.img
  91.6GB: initrd.img.old
 151.0GB: vmlinuz
 151.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  36 23 bd a3 ef ea 7b fa  be 7e a0 1f 82 8f e0 d1  |6#....{..~......|
00000010  fa b1 fe 57 3f d1 4f f5  33 f0 99 7e ae 5f e8 97  |...W?.O.3..~._..|
00000020  fa 15 f6 1a 7c 43 fe 2d  f8 04 7e a7 df 13 e7 a6  |....|C.-..~.....|
00000030  fe 00 7e d4 9f f4 67 fd  05 fb 9f fe aa ff d3 df  |..~...g.........|
00000040  c0 6f fa bb fe 81 fd d4  11 8c 63 84 89 60 24 2c  |.o........c..`$,|
00000050  0d 1f 75 f3 83 f2 ef da  98 9f da 35 86 dc 4f ed  |..u........5..O.|
00000060  19 d7 f8 c6 9a c0 44 34  eb b4 05 bf 10 f5 b3 8e  |......D4........|
00000070  64 76 e9 c8 26 8a 79 cf  f3 a2 c2 ef 74 34 13 15  |dv..&.y.....t4..|
00000080  8c 6e a2 99 18 26 3a 3a  9a 89 69 de ea 58 26 b6  |.n...&::..i..X&.|
00000090  89 63 e2 9a 78 70 5c 3c  6f e8 67 7c 13 cb fc 66  |.c..xp\<o.g|...f|
000000a0  12 50 2f 21 18 1d 4e 84  4a 6c 92 98 a4 26 19 98  |.P/!..N.Jl...&..|
000000b0  cc 24 c7 93 00 5f 0a 93  d2 a4 02 53 c3 f1 69 1d  |.$..._.....S..i.|
000000c0  cb a4 a1 65 5a 93 ce a4  37 19 4c 46 93 c9 64 c6  |...eZ...7.LF..d.|
000000d0  13 1f 5f 16 bc 59 c1 34  70 36 93 dd e4 30 39 4d  |.._..Y.4p6...09M|
000000e0  2e 6a 64 43 fd 6e 86 ea  dc 26 8f c9 4b ac 7c 26  |.jdC.n...&..K.|&|
000000f0  bf 29 60 0a a2 53 90 2b  64 0a 9b 3f 4c 11 f3 a7  |.)`..S.+d..?L...|
00000100  29 0a 16 35 c5 4c 71 53  c2 94 04 0b c1 a5 50 a5  |)..5.LqS......P.|
00000110  4d 19 da 97 35 e5 4c 79  53 c1 54 84 2b e0 c9 86  |M...5.LyS.T.+...|
00000120  af 12 de ca 60 19 b8 14  2d 4a 9a bf 4c 15 53 d5  |....`...-J..L.S.|
00000130  54 33 d5 4d 0d 53 93 96  b5 c0 52 70 6d 53 c7 d4  |T3.M.S....RpmS..|
00000140  35 f5 c8 d7 07 6b c2 7f  a3 1a 80 f5 e0 86 44 69  |5....k........Di|
00000150  64 1a 9b 26 a6 29 d8 d4  34 33 cd 4d 0b d3 d2 b4  |d..&.)..43.M....|
00000160  32 ad 4d 1b b0 ad 69 67  da 9b 0e 94 b7 c7 1a 9b  |2.M...ig........|
00000170  8e a6 93 e9 6c ba 98 ae  e6 1f ea 36 35 dd c0 6e  |....l......65..n|
00000180  a6 bb e9 61 7a 9a 5e a6  b7 e9 63 fa 12 b3 12 51  |...az.^...c....Q|
00000190  fb 11 b7 3f d8 10 1e 60  e6 e9 81 66 0e 7b 6c 80  |...?...`...f.{l.|
000001a0  19 84 77 30 d8 0f 1e 62  86 9a 61 66 b8 19 61 46  |..w0...b..af..aF|
000001b0  9a 51 d4 1a 6d c6 98 3b  7a 2c fe 61 66 9c 00 fe  |.Q..m..;z,.af...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 cc 11 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  cc 11 00 10 c2 00 00 00  |....... ........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by oldfred on 2010-12-16
I do not see anything in the boot script. Grub's osprober found the XP install and added the entry so all the boot files were there.

Are you getting  a windows error? Blue screen? Grub now tries to recover from windows boot errors and return rather than just crashing.

I would try running chkdsk from a XP CD.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by nikka08 on 2010-12-18
No error or blue screen. It shows the XP boot screen for about 30 sec, and then goes black like it's going to show the welcome screen, but restarts instead. The HP logo pops back up. It's an HP G60-125NR, by the way, if that helps. 

I booted the XP disc and tried to run chkdsk, but there is no option for it. Instead of showing the initial screen, it shows the partition selection screen. So....not sure what that's about.

Thank you for your timely responses.

---

### Post by oldfred on 2010-12-18
I saved these instructions, but have not had to use them.

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

---

### Post by nikka08 on 2010-12-19
I finally got the recovery mode to show up. However, after running it, Ubuntu disappeared. From "My Computer" and I couldn't get it to boot. It just kept booting straight into XP. So, I said screw it and formatted and just installed Ubuntu. I'd rather have that than Windows, anyway. Thank you for your help and responses, they were much appreciated. My brother thinks I might have a hardware issue because I set this up on his laptop without a problem. Either way, thank you again and take care for now.

---

### Post by oldfred on 2010-12-19
Just about anything windows does, ends up installing its boot loader to the MBR. 

You probably did not have to reinstall but just install the grub2 boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

