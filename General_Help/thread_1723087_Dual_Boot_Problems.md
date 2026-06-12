---
title: "Dual Boot Problems"
date: 2011-04-06
forum: General Help
---

### Post by dirtynorth on 2011-04-06
Hello all,

I installed Windows after ubuntu ( I know that was a bad idea).  Anyway, I reinstalled the Grub2 using the instructions found here [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Everything seemed to work well and when I rebooted I got an empty Grub screen.  I tried to "refresh the grub list" which is the lst step in the instructions by entering  "sudo update-grub" and I get the error message

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I tried mounting the Ubuntu partition and I still get the same error.

Can anyone please help me get the Grub working?  Or, another method to gain acess to my two OS again (Im getting sick of windows 7)

Thanks

---

### Post by oldfred on 2011-04-06
Do you get grub menu. Or because it has not found the windows yet, you do not have menu.

If you hold shift key down from BIOS boot do you then get grub menu, or do you get an error message?

If not booting or grub error post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste

---

### Post by coffeecat on 2011-04-06
The method you linked to *should* have worked so I don't know why you get an empty grub screen. You posted the link again instead of your error message.

Anyway, the best way to see what is wrong is to run the boot info script. Boot up the live Ubuntu CD and select "try Ubuntu" to get to the live desktop. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script according to the instructions on that site and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags as described there. You can use the # icon in the message toolbar for this.

---

### Post by dirtynorth on 2011-04-06
Sorry about the error message.  

the error is 

```
 /usr/sbin/grup-probe: error: cannot find a device for / (is /dev mounted?) 
```

---

### Post by dirtynorth on 2011-04-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    71,890,874    71,684,027   7 HPFS/NTFS
/dev/sda3          71,890,942   173,453,311   101,562,370   5 Extended
/dev/sda5          71,890,944    75,796,479     3,905,536  82 Linux swap / Solaris
/dev/sda6          75,798,528   105,093,119    29,294,592  83 Linux
/dev/sda7         105,095,168   173,453,311    68,358,144  83 Linux
/dev/sda4         173,453,805 2,930,272,064 2,756,818,260   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6E925154925121BF                       ntfs       System Reserved               
/dev/sda2        269ABE0C3E744349                       ntfs       Windows 7                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6FE165975430A736                       ntfs                                     
/dev/sda5        fe58c1c5-81ff-42d4-a885-93ed7ea02f56   swap                                     
/dev/sda6        a949faa1-5d0f-49ee-9a32-7a371e31da27   ext4                                     
/dev/sda7        a0338d47-9e9b-47ea-b829-cab63d9617ae   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt                     ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a949faa1-5d0f-49ee-9a32-7a371e31da27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e925154925121bf
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=a949faa1-5d0f-49ee-9a32-7a371e31da27 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a0338d47-9e9b-47ea-b829-cab63d9617ae /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=fe58c1c5-81ff-42d4-a885-93ed7ea02f56 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  47.5GB: boot/grub/core.img
  47.7GB: boot/grub/grub.cfg
  47.7GB: boot/initrd.img-2.6.32-24-generic
  47.8GB: boot/initrd.img-2.6.32-27-generic
  47.8GB: boot/initrd.img-2.6.32-28-generic
  47.6GB: boot/vmlinuz-2.6.32-24-generic
  47.6GB: boot/vmlinuz-2.6.32-27-generic
  47.8GB: boot/vmlinuz-2.6.32-28-generic
  47.8GB: initrd.img
  47.8GB: initrd.img.old
  47.8GB: vmlinuz
  47.6GB: vmlinuz.old

=================== sda7: Location of files loaded by Grub: ===================


  58.2GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb ec 43 75 b5 fd 49 ad  0a 0b 60 62 81 4c 4d 8f  |..Cu..I...`b.LM.|
00000010  b8 49 bd b7 2c 78 3a 29  03 14 41 51 88 27 19 15  |.I..,x:)..AQ.'..|
00000020  93 b4 8e c9 de 59 c6 c9  b9 67 13 4d f6 dc cf f9  |.....Y...g.M....|
00000030  48 81 8b 06 81 4c 44 62  91 84 86 22 93 72 a3 3f  |H....LDb...".r.?|
00000040  fa 97 6f e7 67 29 8c b3  a2 7d 2b db d1 24 26 a8  |..o.g)...}+..$&.|
00000050  39 a2 37 af b1 0d d6 d7  f5 26 b4 10 84 80 14 e4  |9.7......&......|
00000060  0c c7 1b 20 bb ce d4 b3  db fe 3c ea 17 f0 24 c9  |... ......<...$.|
00000070  33 09 fd 71 5a 55 ba d0  56 d4 3f 6c be fd d2 df  |3..qZU..V.?l....|
00000080  f5 a4 c1 8c c1 68 ae 8b  56 85 7f 6a ff ff 6f 43  |.....h..V..j..oC|
00000090  a9 49 33 7f ba b3 cd 29  ab 47 57 41 47 67 39 6c  |.I3....).GWAGg9l|
000000a0  88 ac 8e c6 2b 86 0e af  3b b0 cf 07 9f 51 40 35  |....+...;....Q@5|
000000b0  04 91 d3 12 6f b2 76 a5  9e df e2 7b 38 43 a8 2c  |....o.v....{8C.,|
000000c0  23 85 67 13 cf 54 d3 26  59 93 a9 6e a4 e8 3d f4  |#.g..T.&Y..n..=.|
000000d0  96 bf ad 26 09 0b 30 8d  14 c2 4b 1a cc 22 7b 6d  |...&..0...K.."{m|
000000e0  5f ff ed e8 75 29 26 6f  f7 56 79 a5 35 68 ea e8  |_...u)&o.Vy.5h..|
000000f0  2c 76 73 96 c8 96 47 98  b3 1d 5e af 1c d1 b6 ed  |,vs...G...^.....|
00000100  09 00 91 7c 12 45 04 44  97 bb 53 7f 24 97 fc 1b  |...|.E.D..S.$...|
00000110  ac 25 97 ee 54 be 60 92  c0 64 58 20 15 5c e2 64  |.%..T.`..dX .\.d|
00000120  42 e8 50 d9 ef 20 73 89  b7 75 64 37 6f fa 0c 4c  |B.P.. s..ud7o..L|
00000130  74 4b ce 69 a8 72 6e e7  2d 5b ff cd 3d 5a ac cd  |tK.i.rn.-[..=Z..|
00000140  37 35 bf fa a4 e7 ce cd  55 63 4d 9a cc 73 b1 dd  |75......UcM..s..|
00000150  8d 31 cd 28 1a 13 e3 7f  f2 9b ae 14 01 01 12 b8  |.1.(............|
00000160  35 48 a8 4c ff fb 92 0c  32 00 02 df 4f 5a 1d 61  |5H.L....2...OZ.a|
00000170  40 02 5c e9 eb 33 ac 34  00 4f ad 41 5e 79 96 80  |@.\..3.4.O.A^y..|
00000180  02 0d a8 2b cf 32 d0 00  47 3b b3 7f 04 45 f0 83  |...+.2..G;...E..|
00000190  75 84 52 fd 4c 2f a0 34  9e 0e a3 90 c0 76 ba 46  |u.R.L/.4.....v.F|
000001a0  d9 f5 19 23 33 7a ae 96  ee b6 a3 b7 f5 52 24 50  |...#3z.......R$P|
000001b0  75 2a f4 9a 8a 92 56 ee  92 eb 6f ff 45 6b 00 fe  |u*....V...o.Ek..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 98  3b 00 00 08 bf 01 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by coffeecat on 2011-04-06
When you re-installed grub to the mbr, you defined the root partition as sda7, which is your home partition, instead of sda6.

Boot up the live 10.04 CD and open a terminal. Now:

```
sudo mount /dev/sda6 /mnt
```

and...

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Now reboot. Your grub.cfg looks OK so your grub menu should be OK, but if there are any problems, once you are in Ubuntu on your hard drive, run:

```
sudo update-grub
```

Somehow /boot/grub/core.img has got into your home (sda7) partition. Perhaps when you tried to repair grub. It doesn't belong there.

---

### Post by dirtynorth on 2011-04-06
Stupid mistake.  thanks alot all.

---

### Post by coffeecat on 2011-04-06
Good luck! :)

---

