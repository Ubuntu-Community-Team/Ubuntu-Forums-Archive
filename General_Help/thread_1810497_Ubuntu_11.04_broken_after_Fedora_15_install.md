---
title: "Ubuntu 11.04 broken after Fedora 15 install"
date: 2011-07-23
forum: General Help
---

### Post by kokoshmusun on 2011-07-23
I installed Fedora 15 on top of Ubuntu 11.04 (running in Classic mode, not Unity). First, Fedora took over grub completely and ubuntu disappeared. I tried to restore the Ubuntu option in the fedora grub. It worked (and I also restored ubuntu's own grub later on -with the same result as I'm about to describe), but I still can't log into Ubuntu, because when I choose Ubuntu at boot, and enter my password, it refreshes the same gdm screen as if nothing happened. In the meanwhile, there is an error about gnome power settings at the top right corner, and the gdm screen also looks different than it used to when I had everything intact. Any thoughts?
 
The error reads "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."
 
Any thoughts how I can restore Ubuntu?

---

### Post by kokoshmusun on 2011-07-23
By doing something that was sort of the following (scrambled from the web, BEWARE, I didn't absolutely know what I was doing), I managed to get rid of the GNOME power manager error warning, but I still can't log in to Ubuntu at all.
 
>  
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
dpkg --configure -a
apt-get -f install 


---

### Post by coffeecat on 2011-07-23
That error message about the gnome power manager is often a spurious one caused by your root partition being full. The last two commands that you posted have probably created a little bit of room, but not enough.

Also - there would have been a "mount" command that preceded those posted commands because it looks as though you have chrooted into your Ubuntu partition from Fedora - which is an eminently sensible thing to do. Well done! :) The missing command would have been something like:

```
sudo mount /dev/sd-*something* /mnt
```

Is that correct?

Anyway, run those chroot commands again, and instead of:

```
dpkg --configure -a
apt-get -f install 
```

Run this:

```
apt-get clean
```

This will remove all the downloaded and cached packages, hopefully releasing some space. You'll need to create more space, but it might be enough to allow you to boot into Ubuntu. If it does, from Ubuntu, post the terminal output of:

```
df -h
```

And we'll take it from there.

---

### Post by kokoshmusun on 2011-07-23
Ahh, thanks so much.  Yes, I forgot the first line, I added it now.  I just went into my ubuntu hard disk partition from the live CD and removed a few big directories to save space.  And ubuntu now boots!!!!!
 
However, no sign of fedora.  How do I add Fedora back to Ubuntu's grub now?  I'm trying to use the grub-customizer GUI but I don't know what to do.  And my wife is pulling me away from the computer because I wasted too much time on this.  Aaaaahhhhh...

---

### Post by Quackers on 2011-07-23
run sudo update-grub in the terminal and openSUSE should appear.

---

### Post by coffeecat on 2011-07-23
> **Quackers said:**
> run sudo update-grub in the terminal and openSUSE should appear.

Or possibly Fedora. :p

@kokoshmusun, I agree with Quackers. Run "sudo update-grub" in Ubuntu.

---

### Post by kokoshmusun on 2011-07-23
sudo update-grub doesn't find the Fedora partition.

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done


---

### Post by coffeecat on 2011-07-23
Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post your RESULTS.txt file in code tags for legibility. That will give us an overview of your system so that we can see what has happened to Fedora. I'm out this evening so will not be able to post back for some hours, but Quackers may be around and if so he'll be able to help you with interpreting that.

---

### Post by kokoshmusun on 2011-07-23
Wow, you're so kind, many thanks. Here's the output of boot-info:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   157,982,719   157,980,672  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris
/dev/sda3         157,982,720   159,006,719     1,024,000  83 Linux
/dev/sda4         159,006,720   224,827,391    65,820,672  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2ef2237f-3029-4999-9afb-13f05259a425   ext4       
/dev/sda3        39a1bf01-c88b-4b26-a3b6-38776a6d2a0c   ext4       
/dev/sda4        5NGjXR-kr9S-Zpkt-y8cu-tAqi-XrQg-RdphnE LVM2_member 
/dev/sda5        44e8de97-eaf2-4e6a-965d-ac48ca51695a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=2ef2237f-3029-4999-9afb-13f05259a425 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=2ef2237f-3029-4999-9afb-13f05259a425 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2ef2237f-3029-4999-9afb-13f05259a425
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2ef2237f-3029-4999-9afb-13f05259a425 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=44e8de97-eaf2-4e6a-965d-ac48ca51695a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  38.373115540 = 41.202819072   boot/grub/core.img                             1
   0.186573029 = 0.200331264    boot/grub/grub.cfg                             1
  30.065685272 = 32.282783744   boot/initrd.img-2.6.35-23-generic              2
  19.186782837 = 20.601651200   boot/initrd.img-2.6.35-24-generic              2
  15.079101562 = 16.191062016   boot/initrd.img-2.6.35-25-generic              2
  65.641601562 = 70.482132992   boot/initrd.img-2.6.35-28-generic              3
  67.865024567 = 72.869515264   boot/initrd.img-2.6.38-10-generic              2
  18.059787750 = 19.391549440   boot/initrd.img-2.6.38-8-generic               2
  37.680854797 = 40.459509760   boot/vmlinuz-2.6.35-23-generic                 1
  37.981540680 = 40.782368768   boot/vmlinuz-2.6.35-24-generic                 1
  38.039981842 = 40.845119488   boot/vmlinuz-2.6.35-25-generic                 1
  40.125926971 = 43.084886016   boot/vmlinuz-2.6.35-28-generic                 1
   2.622379303 = 2.815758336    boot/vmlinuz-2.6.38-10-generic                 1
  63.587219238 = 68.276256768   boot/vmlinuz-2.6.38-8-generic                  1
  74.022975922 = 79.481565184   grub/core.img                                  1
  67.865024567 = 72.869515264   initrd.img                                     2
  18.059787750 = 19.391549440   initrd.img.old                                 2
   2.622379303 = 2.815758336    vmlinuz                                        1
  63.587219238 = 68.276256768   vmlinuz.old                                    1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_fedora15-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-35.fc15.i686.PAE)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.8-35.fc15.i686.PAE ro root=/dev/mapper/vg_fedora15-lv_root rd_LVM_LV=vg_fedora15/lv_root rd_LVM_LV=vg_fedora15/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=trq rhgb quiet
title Fedora (2.6.38.6-26.rc1.fc15.i686.PAE)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686.PAE ro root=/dev/mapper/vg_fedora15-lv_root rd_LVM_LV=vg_fedora15/lv_root rd_LVM_LV=vg_fedora15/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=trq rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.PAE.img
title	Ubuntu 11.04
	root (hd0,0)
	kernel /boot/grub/core.img
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.590823174 = 81.165028352   grub/grub.conf                                 1
  75.590823174 = 81.165028352   grub/menu.lst                                  1
  75.590249062 = 81.164411904   grub/stage2                                    1
  75.363133430 = 80.920548352   initramfs-2.6.38.6-26.rc1.fc15.i686.PAE.img    3
  75.350286484 = 80.906754048   vmlinuz-2.6.38.6-26.rc1.fc15.i686.PAE          2
  75.367711067 = 80.925463552   vmlinuz-2.6.38.8-35.fc15.i686.PAE              2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  07 2c be 67 06 22 52 ac  0b 8b 91 91 12 16 a3 f3  |.,.g."R.........|
00000010  1a c4 30 cc 9f 29 c5 cf  9f 25 77 46 44 99 8e 9d  |..0..)...%wFD...|
00000020  2f 40 f4 f6 6a 90 e5 c6  c8 d5 22 db 1a d2 43 8f  |/@..j....."...C.|
00000030  0d eb 43 8f 0d f3 f8 63  c3 7d 01 0b c8 ac e5 a4  |..C....c.}......|
00000040  d6 1b fa 22 d7 a0 81 99  20 2e 18 d2 7d a9 9e 55  |...".... ...}..U|
00000050  71 7d f5 7a f5 58 5f d4  4d dc 75 14 55 f4 fc 10  |q}.z.X_.M.u.U...|
00000060  8a 2a 9a 78 54 d1 64 ee  82 d1 97 e8 7c 1f c1 ca  |.*.xT.d.....|...|
00000070  7c dc 3a b0 1e 64 84 a3  5e 53 f1 47 21 3f cd 2c  ||.:..d..^S.G!?.,|
00000080  c6 b6 d6 6f 83 82 f9 33  d9 0c f2 7b dd da 20 fa  |...o...3...{.. .|
00000090  e3 47 12 db 17 1b 31 aa  f4 ff 07 de 68 06 4f 86  |.G....1.....h.O.|
000000a0  ca 30 a4 f5 ff 81 95 e1  3b 0d 2b c3 6d df ff af  |.0......;.+.m...|
000000b0  ac ac 28 54 86 f2 f9 55  56 d6 15 2a 63 46 2d c3  |..(T...UV..*cF-.|
000000c0  ff 90 67 57 2c 4e 74 f4  28 88 bf 5b 17 b6 d9 c6  |..gW,Nt.(..[....|
000000d0  27 99 2c 6d 6c b1 ef 32  ea e3 de 7c 45 ac 6b e0  |'.,ml..2...|E.k.|
000000e0  53 ea 68 af 41 3f a4 8f  f3 a7 e9 d8 4c 32 77 0d  |S.h.A?......L2w.|
000000f0  1e 37 d7 a4 e6 37 d0 96  86 b3 d6 cd fd 3a cd dd  |.7...7.......:..|
00000100  21 c1 c0 02 37 dc aa 6b  df c3 d3 7c ed 05 5c 63  |!...7..k...|..\c|
00000110  f2 87 d1 f7 8c fe cf 20  d7 30 36 84 a2 89 e3 b1  |....... .06.....|
00000120  43 5b 63 44 a7 96 18 2a  6f 1c 20 bf 96 ca 46 77  |C[cD...*o. ...Fw|
00000130  4e 65 2e 4c 5e d0 78 a2  26 dc 52 7d 4f da c5 0e  |Ne.L^.x.&.R}O...|
00000140  92 9f c2 b1 10 d7 ab 6f  c5 69 3c c2 b7 aa 9f 41  |.......o.i<....A|
00000150  f4 cd 9f 40 60 03 9b 0a  5b 11 8b 0a 0a 1b 4f 08  |...@`...[.....O.|
00000160  d1 8d 17 02 29 2c 48 2a  90 c6 12 1d eb da ff 06  |....),H*........|
00000170  db 19 a3 99 37 01 73 22  31 77 ad f3 6b a8 c5 bf  |....7.s"1w..k...|
00000180  23 69 2d 0b f7 9b 7c df  9f c2 9a 80 7c 59 4b fc  |#i-...|.....|YK.|
00000190  3a c6 12 3f 06 4b cc 6e  aa 37 a0 29 45 59 62 33  |:..?.K.n.7.)EYb3|
000001a0  9a e7 d2 54 08 25 2e 63  89 ff 76 79 4b 0c 3c ae  |...T.%.c..vyK.<.|
000001b0  1c c3 cd 4d 3d 11 15 7c  70 39 8f f2 a7 a4 00 fe  |...M=..|p9......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


---

### Post by Quackers on 2011-07-23
Where did openSUSE go? :wink:  :-)  Altright then, Fedora.

Is Fedora supposed to be in sda3?
Some of its boot files are there, but no operating system is shown.

---

### Post by Blasphemist on 2011-07-23
Fedora and ubuntu are using different grub versions, legacy vs. 2. Please boot the ubuntu live cd and run this.
```
sudo mount /dev/sda3 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
```
This will install grub2 for fedora.
Then run this.
```
sudo update-grub
```
Then reboot and all should be good.

---

### Post by kokoshmusun on 2011-07-23
Thanks Blasphemist! But that did not go well. Ater the last line, I got a "/usr/sbin/grub-probe: error: cannot stat 'aufs'". And now I lost Ubuntu again. I only have the black grub rescue screen.
 
Edit: I cannot get Ubuntu back using the method I had used before to get it back.  Now I'm really stuck at the grub screen.  What's weird is this screen doesn't recognize any of the commands I f&#305;nd from the web (e.g., root, setup, etc.)

---

### Post by coffeecat on 2011-07-23
Installing grub2 to the mbr of sda, pointing to the Fedora partition sda3 was never going to work (Fedora uses legacy grub), so let's get you booting back into Ubuntu.

Boot up with the Ubuntu 11.04 live CD and open a terminal. Then:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

The problem with Fedora is that sda3 is simply the Fedora boot partition, which is only about 524MB in size. The Fedora root partition is sda4, which is a LVM volume, which really complicates matters, and this could be why update-grub (or rather os-prober) is not detecting Fedora. It may be possible to create a stanza for your Ubuntu /etc/grub.d/40_custom file, but it's too late here for me to try to work out how you would do this. I'll look at this thread in the morning when I'm fresher to see if I can come up with something for you. In the meantime the code above will get you back into Ubuntu.

---

### Post by kokoshmusun on 2011-07-23
Thanks for saving me from the grub screen coffeecat!  Really, don't bother to waste more time on this.  All of this started because I just wanted to show various distros to my wife, who I convinced to switch from Mac to Linux, and I just thoughtlessly installed Fedora thinking two of the major linux distros would know not to override each other at boot.  I will probably just reinstall Fedora, paying attention to the process, so that it can coexist with Ubuntu.  And if that seems to mess it up even more, I will just wipe the disk and start over.

---

### Post by coffeecat on 2011-07-23
> **kokoshmusun said:**
> I will probably just reinstall Fedora, paying attention to the process, so that it can coexist with Ubuntu.

Good idea. I can't remember exactly what it is called, but in the Fedora installer (Anaconda) there is an option similar to the "advanced/manual" option in Ubuntu Maverick and before or "something else" in Natty. Basically, you can tell the installer what partitions you want, what size and what filesystem. Which means you can override Fedora's obsession with separate boot partitions and LVM volumes. Of course, Fedora will still not include Ubuntu in its grub menu, but you've solved that problem before.

Good luck! :)

---

### Post by oldfred on 2011-07-23
If you install Fedora's old grub to the boot partition then you have another option of a chainboot entry in 40_custom to boot with.

Some users with similar issues:

HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

Fedora rescue mode & reinstall grub
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-rescuemode-boot.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-rescuemode-boot.html)

---

