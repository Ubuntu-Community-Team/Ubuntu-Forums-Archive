---
title: "Update destroyed 10.10"
date: 2010-12-09
forum: General Help
---

### Post by Green9090 on 2010-12-09
Update manager bugged me about installing updates as per usual, I let it do its thing, rebooted a little after it asked me to... and now the system freezes on login (login menu works as usual though). Even safe mode freezes before it loads anything I can use, and no keyboard shortcuts work. The only thing I can use is the recovery console, but that doesn't seem to be overly helpful. In the other modes I get one white bar along the bottom, my normal desktop background, and the ability to move my mouse cursor. 

I dual boot Windows, which I'm using now, and luckily that seems untouched. However, my entire Ubuntu half of the computer has become completely FUBARed. Any idea what I might be able to do to fix it, either through the recovery console or with a livecd? Or would it be better to just reinstall and pray it doesn't happen again?

---

### Post by Rubi1200 on 2010-12-09
Hi,
could you please confirm whether this is a regular or a Wubi install?

I also recommend you use a LiveCD to boot the computer and then run the boot info script linked at the bottom of my post.

Get the results back here so we can get a better overview of your setup.

Thanks.

---

### Post by Green9090 on 2010-12-09
It's not a wubi install, it has its own partition. 

I'll do the boot script and post back when that's done, thanks.

---

### Post by sikander3786 on 2010-12-09
**Added:** I was too lazy to post. Didn't see Rubi1200's post above. You definitely need to answer their queries as well ;-)

If this is not a Wubi install, boot Recovery Mode > Drop to Root Shell and do these commands.

Connect to internet:
```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

Reconfigure your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot!

```
sudo shutdown -r now
```

If any errors are encountered, post them.

---

### Post by Green9090 on 2010-12-09
```
Boot script output (spoiler and hide tags don't seem to work on this forum, is there an alternative? Until then huge post woo!)
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

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

    File system:       ext3
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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   124,920,661   124,713,814   7 HPFS/NTFS
/dev/sda3         124,921,501   156,296,384    31,374,884   5 Extended
/dev/sda5         124,921,503   154,882,664    29,961,162  83 Linux
/dev/sda6         154,882,728   156,296,384     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A0C003B9C0039526                       ntfs       System Reserved               
/dev/sda2        C0B807C2B807B646                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        93b39c45-838e-40ed-8d30-b4a9ebde5cb0   ext3                                     
/dev/sda6        a656f98f-2dd7-4379-80ea-332eb6c50f5b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
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
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=93b39c45-838e-40ed-8d30-b4a9ebde5cb0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=93b39c45-838e-40ed-8d30-b4a9ebde5cb0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93b39c45-838e-40ed-8d30-b4a9ebde5cb0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93b39c45-838e-40ed-8d30-b4a9ebde5cb0 ro single 
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
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 93b39c45-838e-40ed-8d30-b4a9ebde5cb0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a0c003b9c0039526
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
UUID=93b39c45-838e-40ed-8d30-b4a9ebde5cb0 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a656f98f-2dd7-4379-80ea-332eb6c50f5b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  65.3GB: boot/grub/core.img
  65.3GB: boot/grub/grub.cfg
  65.3GB: boot/initrd.img-2.6.35-22-generic
  65.4GB: boot/initrd.img-2.6.35-23-generic
  65.3GB: boot/vmlinuz-2.6.35-22-generic
  65.3GB: boot/vmlinuz-2.6.35-23-generic
  65.4GB: initrd.img
  65.3GB: initrd.img.old
  65.3GB: vmlinuz
  65.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  74 ed ff 00 e0 02 c2 fd  5f a1 0b 66 d5 18 30 c4  |t......._..f..0.|
00000010  1a 1a 49 e4 9e ff a5 35  5c 7c fd 20 f2 80 c1 c5  |..I....5\|. ....|
00000020  4d 44 c3 63 d6 21 5c 0d  3b 31 2f 23 4c 7e ff fe  |MD.c.!\.;1/#L~..|
00000030  e7 e5 75 85 2c d8 d2 b2  1a 5a 31 93 c0 b9 eb 14  |..u.,....Z1.....|
00000040  4c b2 00 1f a4 fe a7 de  ab dd 62 1a a3 d2 90 ea  |L.........b.....|
00000050  11 2d 45 de 3b 76 e4 cc  7c 94 7f 53 a4 15 66 7a  |.-E.;v..|..S..fz|
00000060  bf 3f 8c 5e c4 d2 25 5f  aa 91 27 d0 8e fd bf da  |.?.^..%_..'.....|
00000070  8d 08 2b e1 34 78 4d 40  9f 3e da b7 93 c0 c5 cc  |..+.4xM@.>......|
00000080  99 9e 4d bb 70 a9 9d a9  1f 05 ee cc fc 7c 8c cd  |..M.p........|..|
00000090  8d d3 52 19 6a 6f 6c b5  bc 9f 51 3a 54 bd e3 24  |..R.jol...Q:T..$|
000000a0  fc 05 79 87 42 34 74 80  23 49 0b f6 4e 64 78 59  |..y.B4t.#I..NdxY|
000000b0  fc 3a 73 42 6f 08 32 e4  fc 24 89 eb 4a 27 ae d5  |.:sBo.2..$..J'..|
000000c0  f0 11 cb f7 3d 53 f0 02  04 91 bf 77 e9 4d ab e3  |....=S.....w.M..|
000000d0  46 32 6c 22 aa f6 0a 22  b2 8c d1 65 d0 02 54 d3  |F2l"..."...e..T.|
000000e0  94 4f d8 dd 8a 67 e4 17  2f db 93 df 4a f3 90 1b  |.O...g../...J...|
000000f0  06 57 00 2c ff df 3d 63  a0 d2 35 8b d9 8f 82 57  |.W.,..=c..5....W|
00000100  7d 05 1f a9 06 78 97 31  8e cd dc e2 89 47 38 a3  |}....x.1.....G8.|
00000110  ca ed 41 ab 11 9f 21 77  2d 55 6b 72 5f fc f1 62  |..A...!w-Ukr_..b|
00000120  ac f3 87 a7 ed 71 6b 21  7f 7c c7 8f e2 22 8f ac  |.....qk!.|..."..|
00000130  ac 6c fd 46 d1 e3 c0 8f  6b 33 e3 fa da 47 23 c1  |.l.F....k3...G#.|
00000140  6b 82 e3 f2 24 0a e4 77  ab 57 ab eb 67 bd f1 fb  |k...$..w.W..g...|
00000150  f6 1c e0 bd 37 4c 1e a5  ee 82 df fa be 1f 49 11  |....7L........I.|
00000160  20 3c be 80 c0 30 12 58  31 05 b4 dd c9 11 ac 21  | <...0.X1......!|
00000170  58 24 e2 4a de 6d a1 33  b2 f5 2d 60 7f fe e5 88  |X$.J.m.3..-`....|
00000180  72 ed 44 9a a9 a2 52 f6  af 56 ae fc 71 ff bf 43  |r.D...R..V..q..C|
00000190  b9 6c 5f e2 4c 63 5a e7  bc a9 1f bf 77 c7 53 e4  |.l_.LcZ.....w.S.|
000001a0  df 6c 37 51 9f e0 ad d2  fc ff c5 71 5f 9a 9a 1f  |.l7Q.......q_...|
000001b0  ca ba 88 d1 25 56 ab eb  3a 2d ef 3a d3 38 00 fe  |....%V..:-.:.8..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 ca 2b c9 01 00 fe  |...........+....|
000001d0  ff ff 05 fe ff ff cc 2b  c9 01 58 92 15 00 00 00  |.......+..X.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Green9090 on 2010-12-09
@Sikander, how do I know what to put in place of eth0? Alternatively, is this something I can do from the livecd rather than the recovery console?

---

### Post by Rubi1200 on 2010-12-09
Do you know how this > grldr got on the Windows partition sda1?

I suggest you delete it from the LiveCD and then try booting again.

---

### Post by Green9090 on 2010-12-09
> **Rubi1200 said:**
> Do you know how this  got on the Windows partition sda1?

I suggest you delete it from the LiveCD and then try booting again.

Not only do I not know, but I have no clue what it is or how to go about deleting it. I haven't had to mess with this stuff much in the past, sorry :(

---

### Post by sikander3786 on 2010-12-09
> **Green9090 said:**
> @Sikander, how do I know what to put in place of eth0? Alternatively, is this something I can do from the livecd rather than the recovery console?
Your bootinfoscript output seems pretty ok to me. Wait for Rubi1200's suggestion on that. I am a bit concerned by /grldr on Windows partition but that shouldn't cause a problem to Ubuntu itself. Rubi1200 might enlighten better on that.

And doing those commands from Live CD would need you to do some un-necessary stuff for chrooting your install. It is just better to carry on from Recovery Mode instead.

I am pretty sure you were using the default network interface so just try eth0.

---

### Post by Green9090 on 2010-12-09
> **sikander3786 said:**
> Your bootinfoscript output seems pretty ok to me. Wait for Rubi1200's suggestion on that. I am a bit concerned by /grldr on Windows partition but that shouldn't cause a problem to Ubuntu itself. Rubi1200 might enlighten better on that.

And doing those commands from Live CD would need you to do some un-necessary stuff for chrooting your install. It is just better to carry on from Recovery Mode instead.

I am pretty sure you were using the default network interface so just try eth0.
Alright thanks, I'll do that after Rubi tells me how to get rid of grldr, since I'm on Livecd anyway.

---

### Post by Rubi1200 on 2010-12-09
You should be able to mount the partition from the Places menu and then find and delete the file.

I have seen this before and it seems it may be something left over from a Wubi install (though this is not certain).

Forum member oldfred, one of our more experienced users, recommends deleting the file.

If you cannot access it, run this command in the terminal:
```
gksudo nautilus
```
Then browse to the partition and delete the file.

Be very careful using this as you have root privileges!

---

### Post by Green9090 on 2010-12-09
Grldr is no more, now I'm off to try that other string of commands. Will post back shortly. Thanks a ton for your help so far!

---

### Post by Rubi1200 on 2010-12-09
No problem, let us know how it goes or if you need any other help.

---

### Post by Green9090 on 2010-12-09
Sikander's list of commands unfortunately didn't seem to do anything- most were met with either no response or a list of "0 new 0 installed" etc. Ubuntu still freezes the same way at login.

I'll probably just overwrite it with a fresh install in an hour or so, unless anyone has any more ideas?

---

### Post by Rubi1200 on 2010-12-09
Are you still able to boot Windows normally?

Just want to check on that.

You can try this method from the LiveCD:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```This will bring you to a root command prompt:
```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install -f
dpkg --configure -a
```No need to use sudo since you already have a root prompt.

When finished, and assuming there are no errors, exit and unmount:
```
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```Reboot.

To explain, chroot means that you are taking control of the file-system as if you had booted normally into Ubuntu. Be careful with the commands and report any problems or errors.

---

### Post by Green9090 on 2010-12-09
Windows boots normally, but seems to have discovered that it's a pirated copy. Oddly, that doesn't seem to have any negative effects yet, it just tells me about it. Luckily I don't use Windows much anymore anyway.

No dice on that latest string of commands.

---

