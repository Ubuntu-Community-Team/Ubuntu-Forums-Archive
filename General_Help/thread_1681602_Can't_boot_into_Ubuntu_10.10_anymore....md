---
title: "Can't boot into Ubuntu 10.10 anymore..."
date: 2011-02-04
forum: General Help
---

### Post by majare on 2011-02-04
Hey there. 

Having enjoyed Ubuntu 10.10 for about a week parallel to Win7, I can't boot it anymore.
I suppose it's because of the following: on win7 I have the Acronis Disk Director Suite (version 10.0). The Acronis OS Selector comes with it. So I thought it might be a good idea installing it before I install linux to be able to switch between the OS's afterwards. Then having ubuntu installed I ran windows and uninstalled the OS selector as I saw that ubuntu has it's own bootloader and the Acronis one didn't even run. I restarted my Laptop and win7 started automatically. No bootloader anymore. 
So I installed the Acronis OS Selector again and it can't even find linux (It was able to find both OS's before...) even though it shows the linux-partition (I ran the predefined installation where ubuntu partitions on its own) is still installed. So Ubuntu is still on there I just can't run it.

Where did my Ubuntu bootloader go??? (I NEED Ubuntu cuz Windows7 doesn't support my soundcard...)

---

### Post by majare on 2011-02-04
push

---

### Post by drs305 on 2011-02-04
majare

Welcome to Ubuntu and the Ubuntu forums.  :-)

Please download the boot info script from the following site and then post the contents of the RESULTS.txt which is generated when you run the script. It will give us a good idea of your boot file status and help you put things back together.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by majare on 2011-02-07
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   214,703,842   214,701,795   7 HPFS/NTFS
/dev/sda2    *    347,258,904   625,137,344   277,878,441   7 HPFS/NTFS
/dev/sda3         214,704,126   347,258,879   132,554,754   5 Extended
/dev/sda5         214,704,128   341,759,999   127,055,872  83 Linux
/dev/sda6         341,762,048   347,258,879     5,496,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5E240B24240AFF31                       ntfs                                     
/dev/sda2        808AF13D8AF12FF0                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda5        fe2d311a-f945-4e44-a68b-8a5f9217a890   ext4                                     
/dev/sda6        b3a50e98-3e65-4dee-af5f-e8a29279d9e7   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/5E240B24240AFF31  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro single 
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
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 808af13d8af12ff0
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
# / was on /dev/sda5 during installation
UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b3a50e98-3e65-4dee-af5f-e8a29279d9e7 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 172.3GB: boot/grub/core.img
 112.3GB: boot/grub/grub.cfg
 111.2GB: boot/initrd.img-2.6.35-22-generic
 111.4GB: boot/initrd.img-2.6.35-25-generic
 172.3GB: boot/vmlinuz-2.6.35-22-generic
 172.3GB: boot/vmlinuz-2.6.35-25-generic
 111.4GB: initrd.img
 111.2GB: initrd.img.old
 172.3GB: vmlinuz
 172.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 f8 06 bd 16 00 00  |.......|........|
000001b0  00 00 80 00 00 a1 0e 00  ae 38 12 c6 e0 c3 00 20  |.........8..... |
000001c0  21 00 07 fe ff ff 00 08  00 00 e3 16 cc 0c 80 dd  |!...............|
000001d0  c7 ff 07 fe ff ff 18 c0  b2 14 a9 16 90 10 00 b6  |................|
000001e0  c1 ff 05 dc ed ff fe 1f  cc 0c 02 a0 e6 07 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3

00000000  b6 65 38 de fe 2f 15 03  e3 26 2a f6 fa 7b 36 eb  |.e8../...&*..{6.|
00000010  66 91 5d cc 5b 46 45 ef  b3 04 2a ac 83 16 d7 32  |f.].[FE...*....2|
00000020  a5 ad db 1f 4c 40 6f 32  91 8c ab 0a 05 ec 83 b9  |....L@o2........|
00000030  37 6a cd 9c 5e 08 73 e0  c8 e5 5f 59 84 65 9a 0e  |7j..^.s..._Y.e..|
00000040  e1 6d 64 0e 10 91 37 02  97 3f de e5 07 f2 7f c0  |.md...7..?......|
00000050  6a 65 b6 49 e5 bd 9b a3  44 c1 d0 fb 90 fe 9d 54  |je.I....D......T|
00000060  8e ff f2 12 62 7f 87 ce  12 9a de e9 24 f1 51 57  |....b.......$.QW|
00000070  17 e4 39 39 0a c3 df 90  47 f7 a6 fb c6 39 03 5c  |..99....G....9.\|
00000080  c7 c0 ab 84 67 70 87 f4  24 04 cb 7a 77 48 17 e6  |....gp..$..zwH..|
00000090  62 46 70 c7 f4 75 60 09  ed e9 f7 b3 44 81 ef 87  |bFp..u`.....D...|
000000a0  ad 1b ae cb 3d bf 4e db  ea d4 cd f0 28 55 f3 ca  |....=.N.....(U..|
000000b0  6c eb 81 5a bf 36 3b 73  5a f5 e9 82 2b 30 7f 3b  |l..Z.6;sZ...+0.;|
000000c0  61 66 13 42 01 ce 06 de  85 76 f9 b5 52 7a fe 66  |af.B.....v..Rz.f|
000000d0  4e 32 89 4b 8d 68 90 2a  b0 7d a0 cd 9b a0 d2 d2  |N2.K.h.*.}......|
000000e0  02 04 06 47 de fb c4 60  18 3d 78 1d 12 15 60 14  |...G...`.=x...`.|
000000f0  35 7f ab 01 79 69 86 8d  06 e1 32 f0 b7 3d 09 af  |5...yi....2..=..|
00000100  af 54 9c 40 e9 a7 b5 bd  c1 94 68 93 91 87 34 37  |.T.@......h...47|
00000110  38 2e 03 d7 ac 9c 34 fc  87 7f c4 4d 9d 61 45 32  |8.....4....M.aE2|
00000120  8c b8 fa 8b 44 34 ed 55  9d d3 e6 71 e5 32 9c 30  |....D4.U...q.2.0|
00000130  76 9f b1 2d 3b 58 bf d8  48 bc 77 42 6d 6d a4 bb  |v..-;X..H.wBmm..|
00000140  b8 91 43 87 13 fe 91 8e  cf 5f 16 18 36 76 bb 5e  |..C......_..6v.^|
00000150  13 37 d6 64 50 07 43 85  72 ef 66 31 48 bb 44 a8  |.7.dP.C.r.f1H.D.|
00000160  52 3b 93 91 74 69 c1 c3  7b 96 13 e6 a2 ae a9 25  |R;..ti..{......%|
00000170  30 4d 97 dd 04 06 e6 5e  23 7f b8 7a 49 b3 4c 5c  |0M.....^#..zI.L\|
00000180  77 18 0a 11 84 d2 9d 55  b9 d9 01 40 43 3d 8e db  |w......U...@C=..|
00000190  e9 4a 0b f8 7c b5 c6 c0  7a ca 8c 7d 95 b4 d7 34  |.J..|...z..}...4|
000001a0  4a 8b c5 60 69 97 43 a8  ab 87 fd 81 44 87 85 ea  |J..`i.C.....D...|
000001b0  61 87 5a 13 d4 71 fd 14  97 34 fb 97 4e 1c 00 fe  |a.Z..q...4..N...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 92 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  92 07 00 e8 53 00 00 00  |............S...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2011-02-07
majare,

There is currently no reference to a bootloader in the MBR. 

You can install GRUB 2 from the LiveCD, which will allow you to boot either Ubuntu or Windows:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
After you boot into normal Ubuntu, if you didn't see Windows in the menu, run:
```
sudo update-grub
```

You should be able to access Windows assuming your experiments with other bootloaders left the Windows boot files intact.

If Grub2 isn't working and you just want to try restore the Windows bootloader,
from the LiveCD:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by majare on 2011-02-07
Thanks for helping drs305.
Unfortunately the first step didn't work. I installed Grub2 from the LiveCD successfully but on the restart, Win7 started and not the bootloader. 
I'm gonna try the Windows bootloader now, however I think that it won't work as there is only Win7 listed as operating system in msconfig... well, we'll see.

---

### Post by drs305 on 2011-02-07
> **majare said:**
> Thanks for helping drs305.
Unfortunately the first step didn't work. I installed Grub2 from the LiveCD successfully but on the restart, Win7 started and not the bootloader. 
I'm gonna try the Windows bootloader now, however I think that it won't work as there is only Win7 listed as operating system in msconfig... well, we'll see.

You could run the boot script again and check the first lines. If it installed correctly the first lines should read something like 

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  partition #5 for (,msdos5)/boot/grub.

If it says that, you could try holding down the SHIFT key during boot to see if the G2 menu appears.

---

### Post by majare on 2011-02-07
Okay, I'll try that. 
Windows bootloader didn't work btw, computer restarted into Windows again.

---

### Post by drs305 on 2011-02-07
> **majare said:**
> Okay, I'll try that. 
Windows bootloader didn't work btw, computer restarted into Windows again.

It's possible the bootloader you experimented with isn't allowing the commands to write to the MBR or the section immediately following for some reason, but I'm not very familiar with Windows any longer. That would make some sense since Windows is booting; you don't have another drive or flash drive connected do you?

---

### Post by majare on 2011-02-07
> **drs305 said:**
> It's possible the bootloader you experimented with isn't allowing the commands to write to the MBR or the section immediately following for some reason 
Hmm... I uninstalled that bootloader, can it still have any influence on the system?

> **drs305 said:**
> you don't have another drive or flash drive connected do you? 

Nope, no connections beside electricity and mouse.

Boot script says Lilo is installed in the MBR. I'm gonna uninstall Lilo and reinstall grub for a try...

---

### Post by majare on 2011-02-07
Hmm... I ran the commands you listed above for the grub installation again and checked if Lilo is installed in the Software-Center. It isn't. This is what Boot Script is showing:
```
                Boot Info Script 0.55    dated February 15th, 2010                    
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   214,703,842   214,701,795   7 HPFS/NTFS
/dev/sda2    *    347,258,904   625,137,344   277,878,441   7 HPFS/NTFS
/dev/sda3         214,704,126   347,258,879   132,554,754   5 Extended
/dev/sda5         214,704,128   341,759,999   127,055,872  83 Linux
/dev/sda6         341,762,048   347,258,879     5,496,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5E240B24240AFF31                       ntfs                                     
/dev/sda2        808AF13D8AF12FF0                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda5        fe2d311a-f945-4e44-a68b-8a5f9217a890   ext4                                     
/dev/sda6        b3a50e98-3e65-4dee-af5f-e8a29279d9e7   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/5E240B24240AFF31  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /mnt                     ext4       (rw)


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
search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 ro single 
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
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fe2d311a-f945-4e44-a68b-8a5f9217a890
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 808af13d8af12ff0
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
# / was on /dev/sda5 during installation
UUID=fe2d311a-f945-4e44-a68b-8a5f9217a890 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b3a50e98-3e65-4dee-af5f-e8a29279d9e7 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 172.3GB: boot/grub/core.img
 112.3GB: boot/grub/grub.cfg
 111.2GB: boot/initrd.img-2.6.35-22-generic
 111.4GB: boot/initrd.img-2.6.35-25-generic
 172.3GB: boot/vmlinuz-2.6.35-22-generic
 172.3GB: boot/vmlinuz-2.6.35-25-generic
 111.4GB: initrd.img
 111.2GB: initrd.img.old
 172.3GB: vmlinuz
 172.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  b6 65 38 de fe 2f 15 03  e3 26 2a f6 fa 7b 36 eb  |.e8../...&*..{6.|
00000010  66 91 5d cc 5b 46 45 ef  b3 04 2a ac 83 16 d7 32  |f.].[FE...*....2|
00000020  a5 ad db 1f 4c 40 6f 32  91 8c ab 0a 05 ec 83 b9  |....L@o2........|
00000030  37 6a cd 9c 5e 08 73 e0  c8 e5 5f 59 84 65 9a 0e  |7j..^.s..._Y.e..|
00000040  e1 6d 64 0e 10 91 37 02  97 3f de e5 07 f2 7f c0  |.md...7..?......|
00000050  6a 65 b6 49 e5 bd 9b a3  44 c1 d0 fb 90 fe 9d 54  |je.I....D......T|
00000060  8e ff f2 12 62 7f 87 ce  12 9a de e9 24 f1 51 57  |....b.......$.QW|
00000070  17 e4 39 39 0a c3 df 90  47 f7 a6 fb c6 39 03 5c  |..99....G....9.\|
00000080  c7 c0 ab 84 67 70 87 f4  24 04 cb 7a 77 48 17 e6  |....gp..$..zwH..|
00000090  62 46 70 c7 f4 75 60 09  ed e9 f7 b3 44 81 ef 87  |bFp..u`.....D...|
000000a0  ad 1b ae cb 3d bf 4e db  ea d4 cd f0 28 55 f3 ca  |....=.N.....(U..|
000000b0  6c eb 81 5a bf 36 3b 73  5a f5 e9 82 2b 30 7f 3b  |l..Z.6;sZ...+0.;|
000000c0  61 66 13 42 01 ce 06 de  85 76 f9 b5 52 7a fe 66  |af.B.....v..Rz.f|
000000d0  4e 32 89 4b 8d 68 90 2a  b0 7d a0 cd 9b a0 d2 d2  |N2.K.h.*.}......|
000000e0  02 04 06 47 de fb c4 60  18 3d 78 1d 12 15 60 14  |...G...`.=x...`.|
000000f0  35 7f ab 01 79 69 86 8d  06 e1 32 f0 b7 3d 09 af  |5...yi....2..=..|
00000100  af 54 9c 40 e9 a7 b5 bd  c1 94 68 93 91 87 34 37  |.T.@......h...47|
00000110  38 2e 03 d7 ac 9c 34 fc  87 7f c4 4d 9d 61 45 32  |8.....4....M.aE2|
00000120  8c b8 fa 8b 44 34 ed 55  9d d3 e6 71 e5 32 9c 30  |....D4.U...q.2.0|
00000130  76 9f b1 2d 3b 58 bf d8  48 bc 77 42 6d 6d a4 bb  |v..-;X..H.wBmm..|
00000140  b8 91 43 87 13 fe 91 8e  cf 5f 16 18 36 76 bb 5e  |..C......_..6v.^|
00000150  13 37 d6 64 50 07 43 85  72 ef 66 31 48 bb 44 a8  |.7.dP.C.r.f1H.D.|
00000160  52 3b 93 91 74 69 c1 c3  7b 96 13 e6 a2 ae a9 25  |R;..ti..{......%|
00000170  30 4d 97 dd 04 06 e6 5e  23 7f b8 7a 49 b3 4c 5c  |0M.....^#..zI.L\|
00000180  77 18 0a 11 84 d2 9d 55  b9 d9 01 40 43 3d 8e db  |w......U...@C=..|
00000190  e9 4a 0b f8 7c b5 c6 c0  7a ca 8c 7d 95 b4 d7 34  |.J..|...z..}...4|
000001a0  4a 8b c5 60 69 97 43 a8  ab 87 fd 81 44 87 85 ea  |J..`i.C.....D...|
000001b0  61 87 5a 13 d4 71 fd 14  97 34 fb 97 4e 1c 00 fe  |a.Z..q...4..N...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 92 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  92 07 00 e8 53 00 00 00  |............S...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2011-02-07
Try the LiveCD with this one more time. If *lilo* is installing, so should Grub2.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Don't include the partition number in the second command.

---

### Post by majare on 2011-02-07
It worked, eventhough I overlooked that advice concerning the partition number... 

Do I always have to press shift when booting? When I installed Ubuntu, grub appeared automatically...

---

### Post by drs305 on 2011-02-07
> **majare said:**
> It worked, eventhough I overlooked that advice concerning the partition number... 

Do I always have to press shift when booting? When I installed Ubuntu, grub appeared automatically...

If it is booting directly to Ubuntu it is because it found no other operating system. You can try running "sudo update-grub" to see if Grub2 will find the Windows OS. If it does, it should add it to the menu and the menu should automatically appear at boot.

You can also make the menu appear with only one OS by editing /etc/default/grub and adding a # icon at the start of one of the lines (below).

Open the Grub2 configuration file for editing:
```
gksu gedit /etc/default/grub
```

Add the # icon to this line:
> **[COLOR="Red"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT="0"

Save the file, then run this command to make the change to the boot menu:
```
sudo update-grub
```

---

