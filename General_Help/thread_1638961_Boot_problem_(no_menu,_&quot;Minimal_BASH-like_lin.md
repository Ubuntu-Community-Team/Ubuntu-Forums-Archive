---
title: "Boot problem (no menu, &quot;Minimal BASH-like line editing...&quot;, grub&gt;)"
date: 2010-12-06
forum: General Help
---

### Post by Benead on 2010-12-06
Hello,

I'm new enough to linux, so much so that I'm not 100% sure which version I installed. It's Mint for sure, 9 I think...

I have an Acer laptop, bought 5 years ago with Windows XP on it. It's been working more or less fine for months with both systems, and I don't know why (possibly a package update), but things have suddenly changed.

Now, when I turn my computer on, I don't get the usual menu that lets me choose between Windows and Linux. Instead, I get this message:

```
 GNU GRUB version 1.98-1ubuntu5-1mint2

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>
```

I have been looking on the Internet for a fix, and found the following procedure:

```
set root=(hd0,5)
linux /vmlinuz root=/dev/sd5 ro
initrd /initrd.img
boot
```

The first two lines work fine.
But the third one returns:

```
 error: couldn't read file.
```

If I try "boot" after that, it returns a lot of lines, most of which are hard to read because the display is all weird (since I angrily slapped the laptop shut at some recent stage), but one of them definitely seems worrying:

```
 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Can someone tell me where the problem comes from and how to solve it?
Thank you.

---

### Post by Benead on 2010-12-10
So, I've been looking into this a little, and even though I still  haven't found a solution (still can't boot either Windows or Linux),  here's extra info.

I have a liveCD, Linux Mint Isadora 9, which  is the one I used to install Linux in the first place.
I tried a  chroot procedure I found on a page about grub2  ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)), and it didn't work.

I  also found out there was no **menu.lst** file anywhere to be found.  Would that help you help me? I can use my computer with the liveCD, but  it's a little bit of a pain, so I'd rather fix the problem.

Thank  you.

---

### Post by Habitual on 2010-12-10
Boot the Ubuntu Live CD.
Press Ctrl-Alt-F1
login as root
sudo grub-install /dev/sda
sudo update-grub

reboot. should work.

Other may confirm or deny.;)

---

### Post by drs305 on 2010-12-10
If you will run the boot info script and post the contents of RESULTS.txt we can see what is happening with your system:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Benead on 2010-12-11
So, I tried ctrl+alt+f1, loging in as root (did "sudo su" -- wasn't quite sure that's how you do it, however the prompt went from "mint@mint ~ $" to "mint mint #" as i did so). It didn't seem to work.
grub-install /dev/sda   returned the following lines :
```
                                  [SIZE=2]grub-probe: error: cannot find a device for /boot (is /dev mounted?).[/SIZE]
 [SIZE=2]/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).[/SIZE]
 [SIZE=2]No path or device is specified.[/SIZE]
 [SIZE=2]Try '/usr/sbin/grub-probe --help' for more information.[/SIZE]
 [SIZE=2]Auto-detection of a filesystem module failed.[/SIZE]
 [SIZE=2]Please specify the module with the option '--modules' explicitly.[/SIZE]

```As for boot_info_script, here's the result.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Boot file info:     Grub 2 in the file /super_grub_disk_hybrid-1.98s1.iso 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location.
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   185,608,399   185,608,337   7 HPFS/NTFS
/dev/sda2         185,610,238   312,580,095   126,969,858   5 Extended
/dev/sda5         185,610,240   307,310,591   121,700,352  83 Linux
/dev/sda6         307,312,640   312,580,095     5,267,456  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FA2C69932C694BA7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a3593235-b881-4cdf-8aa4-9982e55ce3bd   ext4                                     
/dev/sda6        b55f0dd7-74ee-4233-8491-a4549f2d8688   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
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
search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3593235-b881-4cdf-8aa4-9982e55ce3bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3593235-b881-4cdf-8aa4-9982e55ce3bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a3593235-b881-4cdf-8aa4-9982e55ce3bd
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
UUID=a3593235-b881-4cdf-8aa4-9982e55ce3bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b55f0dd7-74ee-4233-8491-a4549f2d8688 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  97.3GB: boot/grub/core.img
 147.3GB: boot/grub/grub.cfg
 148.5GB: boot/initrd.img-2.6.32-21-generic
  98.2GB: boot/vmlinuz-2.6.32-21-generic
 148.5GB: initrd.img
  98.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  bc e0 fb 0c 13 fe f7 fe  84 cd 4a 3a 2b 7f 5b 0d  |..........J:+.[.|
00000010  a1 ae e1 30 37 12 19 b8  3f de 27 d7 fd ff 00 e3  |...07...?.'.....|
00000020  a4 fa fa ff 00 90 1c 4f  c4 64 fb 6d e5 bd b0 3f  |.......O.d.m...?|
00000030  ba b4 56 90 c6 0f 57 90  ed dc ff 00 f0 0f 93 fd  |..V...W.........|
00000040  da cb 11 53 96 f1 ff 00  b7 e5 ff 00 b6 ff 00 f2  |...S............|
00000050  67 a1 85 56 57 fe 6f fd  26 26 25 ad 8c 11 26 c9  |g..VW.o.&&%...&.|
00000060  57 68 23 20 2e 3e 61 ff  00 3c 7f bd f3 37 c9 fe  |Wh# .>a..<...7..|
00000070  ed 79 d2 77 6f 5e 9c df  84 bf f4 9f 88 ea bd f6  |.y.wo^..........|
00000080  fe bf af b2 50 96 53 20  5b 9d 54 66 43 fe a2 c1  |....P.S [.TfC...|
00000090  1b e5 51 d3 cd bb 6c fd  ef e0 d9 fd df ba b5 a2  |..Q...l.........|
000000a0  4b 54 b6 fe 7f ef 72 fd  8f fd 2e 3f de 1a be df  |KT....r....?....|
000000b0  0f f5 f6 7f f6 d1 fe 1f  55 bb d6 2c ed af 99 0b  |........U..,....|
000000c0  47 21 22 33 85 41 8c fc  a1 09 ea bf fa 0d 45 54  |G!"3.A........ET|
000000d0  d4 1b e9 3f f3 8f ff 00  b4 39 3b 2f eb ff 00 25  |...?.....9;/...%|
000000e0  ff 00 d2 63 fd e3 cd bc  34 ac 25 b9 50 73 8b 99  |...c....4.%.Ps..|
000000f0  08 cf 61 bf ff 00 64 fb  d5 ef 62 df 5b ff 00 5f  |..a...d...b.[.._|
00000100  fd b1 79 6e 95 67 fe 29  1a fa fe 23 8f cc e7 62  |..yn.g.)...#...b|
00000110  44 d9 3e 9d fe 5e 7e ef  fb 0b fc 55 8e 1b 7b 76  |D.>..^~....U..{v|
00000120  99 dd 99 c6 f6 68 97 55  d2 de dd ac e3 0e 19 0c  |.....h.U........|
00000130  71 ee 29 d4 13 cf 95 9c  ff 00 77 e6 ff 00 7a b3  |q.).......w...z.|
00000140  a7 3b c5 bd b9 bd ef fe  db fe de 3c aa d2 53 69  |.;.........<..Si|
00000150  ae df f6 ff 00 fd bc 49  24 69 13 c9 0b 8d ca 5c  |.......I$i.....\|
00000160  a8 60 d9 18 ea 3d b0 bf  79 7f e9 a5 17 ff 00 e4  |.`...=..y.......|
00000170  bf f4 91 25 67 fd 7f e4  df fb 79 a3 a7 ea f7 fa  |...%g.....y.....|
00000180  4c 89 38 95 99 19 54 ab  a1 e1 40 e7 6c 89 cf cb  |L.8...T...@.l...|
00000190  fc 7f ef 57 2c e9 c6 77  fe 7f fc 06 5f f8 17 fe  |...W,..w...._...|
000001a0  4a 27 1b ad bd df eb e2  ff 00 db 8f 4f f0 bf 8d  |J'..........O...|
000001b0  20 d5 8a 41 75 84 ba 7e  23 20 60 49 c6 7a 00 fe  | ..Au..~# `I.z..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 41 07 00 fe  |............A...|
000001d0  ff ff 05 fe ff ff 02 00  41 07 00 68 50 00 00 00  |........A..hP...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by parti on 2010-12-11
first try to mount your old fs (after sudo su, the same way as #3 described):
```
mkdir /mnt/broken
mount /dev/sda5 /mnt/broken
```
whats the output of:
```
ls /mnt/broken/boot/
```and
```
ls /mnt/broken/boot/grub/
```

---

### Post by drs305 on 2010-12-11
Run *parti's* commands. Do you see the kernel (vmlinuz-2.6..... and initrd.img-2.6.... in /boot, and lots of *.mod files in /boot/grub?  RESULTS.txt shows they are there.

One other thing you might check since you have an older BIOS. Your files are past the 137GB limit on your hard drive. Older BIOS's sometimes can't see files past that point unless you enable 'large drives' in the BIOS or update it to a newer version. If you boot and go into BIOS, check to make sure the BIOS sees the real size of your hard drive (even if your system sees the files after you boot). 

If BIOS doesn't see the entire drive, look for a setting to change as mentioned above. If not, see if there is a BIOS update. If neither of those is possible, you may have to create a separate /boot partition in the first part of your drive. Fortunately with the way you have your drive partitioned this won't be difficult. 

Let us know about the BIOS issue and we can then decide what to do next.

---

### Post by Benead on 2010-12-12
So, I did that, and i can see both vmlinuz and initrd.img in /boot. And /boot/grub is indeed filled with lots of *.mod files (exact contents below).
As for the 137Gb idea, BIOS (Info. tab) has a line that says "HDD1 Model Name: SAMSUNG HM160HC". It seems that it sees the whole 160Gb of the drive, right? I can't see any other reference to HD size anywhere else. (I have no HDD2, in case that's relevant).

For more details:
I booted with the liveCD, pressed ctrl+alt+f1, typed "sudo su", then "mkdir /mnt/broken" and "mount /dev/sda5 /mnt/broken".
"ls /mnt/broken/boot/" returns:
```
abi-2.6.32-21-generic
config-2.6.32-21-generic
grub (blue)
memtest86+.bin
vmcoreinfo-2.6.32-21-generic
boot (blue)
gfxmenu (blue)
initrd.img-2.6.32-21-generic (yellow)
System.map-2.6.32-21-generic
vmlinuz-2.6.32-21-generic

```and "ls /mnt/broken/boot/grub/":```

915resolution.mod              gcry_seed.mod         part_sun.mod
acpi.mod                       gcry_serpent.mod      parttool.lst
affs.mod                       gcry_sha1.mod         parttool.mod
afs_be.mod                     gcry_sha256.mod       password.mod
afs.mod                        gcry_sha512.mod       password_pbkdf2.mod
aout.mod                       gcry_tiger.mod        pbkdf2.mod
ata.mod                        gcry_twofish.mod      pci.mod
ata_pthru.mod                  gcry_whirlpool.mod    play.mod
at_keyboard.mod                gettext.mod           png.mod
befs_be.mod                    gfxmenu.mod           probe.mod
befs.mod                       gfxterm.mod           pxeboot.img
biosdisk.mod                   gptsync.mod           pxecmd.mod
bitmap.mod                     grldr.img             pxe.mod
bitmap_scale.mod               grub.cfg              raid5rec.mod
blocklist.mod                  grubenv               raid6rec.mod
boot.img                       gzio.mod              raid.mod
boot.mod                       halt.mod              read.mod
bsd.mod                        handler.lst           reboot.mod
bufio.mod                      handler.mod           reiserfs.mod
cat.mod                        hashsum.mod           relocator.mod
cdboot.img                     hdparm.mod            scsi.mod
chain.mod                      hello.mod             search_fs_file.mod
charset.mod                    help.mod              search_fs_uuid.mod
cmp.mod                        hexdump.mod           search_label.mod
command.lst                    hfs.mod               search.mod
configfile.mod                 hfsplus.mod           serial.mod
core.img                       iso9660.mod           setjmp.mod
cpio.mod                       jfs.mod               setpci.mod
cpuid.mod                      jpeg.mod              sfs.mod
crc.mod                        kernel.img            sh.mod
crypto.lst                     keystatus.mod         sleep.mod
crypto.mod                     linux16.mod           tar.mod
datehook.mod                   linuxmint.png         terminal.lst
date.mod                       linux.mod             terminal.mod
datetime.mod                   lnxboot.img           terminfo.mod
diskboot.img                   loadenv.mod           test.mod
dm_nv.mod                      locale (blue)         tga.mod
drivemap.mod                   loopback.mod          trig.mod
echo.mod                       lsmmap.mod            true.mod
efiemu32.o                     ls.mod                udf.mod
efiemu64.o                     lspci.mod             ufs1.mod
efiemu.mod                     lvm.mod               ufs2.mod
elf.mod                        mdraid.mod            uhci.mod
example_functional_test.mod    memdisk.mod           unicode.pf2
ext2.mod                       memrw.mod             usb_keyboard.mod
extcmd.mod                     minicmd.mod           usb.mod
fat.mod                        minix.mod             usbms.mod
font.mod                       mmap.mod              usbtest.mod
fshelp.mod                     moddep.lst            vbeinfo.mod
fs.lst                         msdospart.mod         vbe.mod
functional_test.mod            multiboot2.mod        vbetest.mod
gcry_arcfour.mod               multiboot.mod         vga.mod
gcry_blowfish.mod              normal.mod            vga_text.mod
gcry_camellia.mod              ntfscomp.mod          video_fb.mod
gcry_cast5.mod                 ntfs.mod              video.lst
gcry_crc.mod                   ohci.mod              video.mod
gcry_des.mod                   part_acorn.mod        videotest.mod
gcry_md4.mod                   part_amiga.mod        xfs.mod
gcry_md5.mod                   part_apple.mod        xnu.mod
gcry_rfc2268.mod               part_gpt.mod          xnu_uuid.mod
gcry_rijndael.mod              partmap.lst           zfsinfo.mod
gcry_rmd160.mod                part_msdos.mod        zfs.mod
```

---

### Post by drs305 on 2010-12-12
Benead,

Thanks for checking that. However, it's not conclusive. What you reported from BIOS was the 'name' of the drive. Since it was in quotes, it doesn't tell us what the BIOS *sees*.

Another way to check would be from the Grub prompt. Type:
```
ls (hd0,5)/boot/initrd.img-2.6.32-21-generic
```
If it sees it then it's not a partition size limitation, since the initrd image is currently located past the 137GB point.

If it doesn't find it, next try:
```
ls (hd0,5)/bootboot/vmlinuz-2.6.32-21-generic
```
This is within the first 137GB, so if it sees vmlinuz... but not initrd... we have probably found the problem.

If it sees both, I would recommend purging/reinstalling G2 via the procedures outlined in the "G2-Chroot" link in my signature line if it's not exactly what you said you did in Post #2.

---

### Post by Benead on 2010-12-15
Ok. Hi again. Sorry I couldn't get back to you earlier.

About what BIOS sees, here's what i get when i don't boot with the liveCD:

```
grub> ls (hd0,5)/boot/vmlinuz-2.6.32-21-generic
vmlinuz-2.6.32-21-generic
grub> ls (hd0,5)/boot/initrd.img-2.6.32-21-generic
initrd.img-2.6.32-21-generic
```

I supposed it meant it could see both files, so i tried again the chroot procedure (this time from the G2-chroot link in drs305's signature, just to be sure). I tried it from both ctrl+alt+f1 and the terminal.

Here's what happens in the terminal:

```
mint@mint ~ $ sudo mkdir /mnt/temp
mint@mint ~ $ sudo mount /dev/sda5 /mnt/temp
mint@mint ~ $ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
mint@mint ~ $ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
mint@mint ~ $ sudo chroot /mnt/temp
 _______________________________________
/ You shall be rewarded for a dastardly \
\ deed.                                 /
 ---------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

mint / # apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Hit http://archive.ubuntu.com lucid Release.gpg                                
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US              
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US          
Hit http://packages.medibuntu.org lucid Release                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US            
Hit http://archive.canonical.com lucid Release                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Get:2 http://packages.linuxmint.com isadora Release [7,235B]         
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                                  
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://packages.medibuntu.org lucid/non-free Packages              
Hit http://security.ubuntu.com lucid-security/restricted Packages      
Hit http://archive.canonical.com lucid/partner Packages
Hit http://security.ubuntu.com lucid-security/universe Packages      
Ign http://packages.linuxmint.com isadora/main Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid/main Packages                    
Ign http://packages.linuxmint.com isadora/upstream Packages          
Hit http://archive.ubuntu.com lucid/restricted Packages              
Ign http://packages.linuxmint.com isadora/import Packages
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Ign http://packages.linuxmint.com isadora/main Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Ign http://packages.linuxmint.com isadora/upstream Packages
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://packages.linuxmint.com isadora/import Packages
Hit http://packages.linuxmint.com isadora/main Packages
Hit http://packages.linuxmint.com isadora/upstream Packages
Hit http://packages.linuxmint.com isadora/import Packages
Fetched 7,433B in 1s (6,978B/s)                          
Reading package lists... Done
mint / # apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libtorrent-rasterbar5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 67 not upgraded.
After this operation, 4,899kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 165366 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
mint / # apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtorrent-rasterbar5
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 67 not upgraded.
Need to get 0B/1,632kB of archives.
After this operation, 4,899kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  grub-common grub-pc
Authentication warning overridden.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 165082 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu5-1mint2_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu5-1mint2_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98-1ubuntu5-1mint2) ...

Setting up grub-pc (1.98-1ubuntu5-1mint2) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

mint / # update-grub
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
mint / # exit
exit
mint@mint ~ $ for i in /dev/pts /dev /proc /sys /boot / ; do sudo umount /mnt/temp$i ; done
umount: /mnt/temp/boot: not mounted
mint@mint ~ $ reboot
```

Just remarking: after I chroot, the prompt line doesn't include the word 'root' in it. For the umount command at the end, while trying the procedure from the ctrl+alt+f1 screen, i got
```
-bash: syntax error near unexpected token '/dev/pts'
```

It kind of seems that the umount command didn't work in both case. I also wonder, if it sees the initrd.img file but cannot read it (Post #1), could the problem come from this particular file?

For info, during the chroot procedure, I encountered the following windows:
```
Configuring grub-pc
The following Linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary.
```
followed by an *empty* line. I know you mentioned something like that would appear while explaining the procedure, but it still seemed odd that it would be empty. I tabbed to <Ok> and proceeded further.

And
```

[*] /dev/sda
[ ] - /dev/sda1
[ ] - /dev/sda2
[ ] - /dev/sda5
[ ] - /dev/sda6
```
There was more text in this last one, but I just wanted to double check I ticked the correct line.

I'd like to know if it's simpler to reinstall Linux altogether. Would that delete the data I have on the current Linux partition, though?

Thank you so much for taking time to help me.

---

### Post by drs305 on 2010-12-15
Benead,

Grub sees your kernel and initrd from the grub prompt, so I don't think BIOS/disk size is the issue.

It looks like the chroot reinstalled G2. Have you tried to reboot yet? If not, go ahead and try.

If it still doesn't work, you can run the boot info script and post the RESULTS.

If you want to reinstall, you can mount your Ubuntu partition from the LiveCD and save any files you wish before reinstalling.

---

### Post by Benead on 2010-12-19
Yes, I rebooted at the time, but it didn't change anything.

I have since saved all the important data and tried to reinstall it from the liveCD, but it suggests to create two new partitions (sda7 and swap on sda8.) and leave me with the old sda5 (and swap sda6)... is it possible to just re-use the old linux partition and re-install it there?

I guess I'm going to start looking for another thread that deals with that issue. I shouldn't be the first newb to encounter that problem. ^^

---

### Post by drs305 on 2010-12-19
> **Benead said:**
> I have since saved all the important data and tried to reinstall it from the liveCD, but it suggests to create two new partitions (sda7 and swap on sda8.) and leave me with the old sda5 (and swap sda6)... is it possible to just re-use the old linux partition and re-install it there?

Yes, you can use the old partitions. When the installation gets to the partitioning page, select the bottom option (manual partitioning) during the installation. You should be presented with your existing partitions. Find the correct one for /, select it, then designate the format and mount point ( / ) for it. Tick the option to format it, being sure you have selected the correct partition.

---

