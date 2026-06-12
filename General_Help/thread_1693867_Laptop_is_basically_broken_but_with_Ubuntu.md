---
title: "Laptop is basically broken but with Ubuntu"
date: 2011-02-23
forum: General Help
---

### Post by bartymany on 2011-02-23
Hi, I just signed up for these forums because I desperately need help, I am an Ubuntu noob and overall not the best with computers. 

I am using a ASUS X5DC Laptop With Windows 7. I would give more information but i'm not too sure on how to do that in Linux, the only other thing I know is that my graphics card is a SiS Mirage one.

It started when I first installed Ubuntu because I heard it was good and I felt like a change of OS, but it didn't recognise my monitor and because of that it was stuck at the resolution 800x600 (I think) and so it didn't quite look right, also it made going on the Internet really awkward, so I searched on the internet to find out how to fix it and I couldn't find anything that worked, so instead I installed Ubuntu netbook version thinking that it would recognise it because it is meant for laptops, so I put the ISO on a USB and it installed but if I tried to do it again it just tried to reinstall itself (I think it was just because I didn't delete the other Ubuntu) and so I just stopped using the USB, so I eventually gave up and tried to delete linux.

I used the Wubi installer for the original Linux so I used that (in the C drive in the Ubuntu folder) to uninstall it too which looked like it uninstalled it fine, I then made the stupid mistake of using EASUS (I think, I cant check anymore) Partition editor and deleted all of the linux sections and made the C drive bigger, after it finished that my laptop doesn't boot up and im stuck at a black screen with it saying to reboot and insert proper boot device. With it not booting I couldn't do anything, but then I remembered the USB and so I put that in and now it boots to Linux, but I really want my windows 7 back because this linux isn't even installed and wont install, the only way I can use it is by exiting the installer and then using the ubuntu that doesn't really look right and doesn't save anything I do. Is there anyway to get my windows 7 back or am I stuck using this?

As I said, I am a Ubuntu Noob, so please make the instructions you give me clear and easy to do. 
By the way, I have probably missed some details, so feel free to ask.
Thanks in advance.

---

### Post by bcbc on 2011-02-23
Please download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here (as described in that link). Thanks

---

### Post by bartymany on 2011-02-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,208,383   488,206,336  83 Linux
/dev/sda2         488,210,430   488,396,799       186,370   5 Extended
/dev/sda5         488,210,432   488,396,799       186,368  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,903,794     3,903,732   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1294d085-c36e-4daf-88b1-0c2382ba3ac5   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ffa74c58-72ca-4c8f-9857-b8fed434681b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60AC-756E                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/DRIVER_CD_WIN7_30 udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1294d085-c36e-4daf-88b1-0c2382ba3ac5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1294d085-c36e-4daf-88b1-0c2382ba3ac5 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1294d085-c36e-4daf-88b1-0c2382ba3ac5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffa74c58-72ca-4c8f-9857-b8fed434681b none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  86.0GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
  86.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 08 00  |.X.SYSLINUX..@..|
00000010  02 40 03 00 00 f8 ef 00  3f 00 ff 00 3f 00 00 00  |.@......?...?...|
00000020  f4 90 3b 00 80 00 29 6e  75 ac 60 4e 4f 20 4e 41  |..;...)nu.`NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 1a 02 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
There you go, I hope I did the code wrap bit right.

---

### Post by bcbc on 2011-02-23
So, unfortunately you've installed 10.10 on your hard drive - and selected to use the whole drive. Windows is gone.

This is what your hard drive contains (just Ubuntu on the first partition and a swap partition inside the extended partition)
> Drive: sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,208,383   488,206,336  83 Linux
/dev/sda2         488,210,430   488,396,799       186,370   5 Extended
/dev/sda5         488,210,432   488,396,799       186,368  82 Linux swap / Solaris


These are your options: 
1. reinstall Windows from your backup disks or the disks you received when you bought the computer. If you don't have these, then you'll need to contact the manufacturer to send some new ones.
2. use Ubuntu in which case you'll need to figure out the resolution issue.
3. if you had data on your drive that is important and was not backed up, you could still recover some of it using a tool called [photorec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step").

---

### Post by bartymany on 2011-02-23
> **bcbc said:**
> So, unfortunately you've installed 10.10 on your hard drive - and selected to use the whole drive. Windows is gone.

This is what your hard drive contains (just Ubuntu on the first partition and a swap partition inside the extended partition)


These are your options: 
1. reinstall Windows from your backup disks or the disks you received when you bought the computer. If you don't have these, then you'll need to contact the manufacturer to send some new ones.
2. use Ubuntu in which case you'll need to figure out the resolution issue.
3. if you had data on your drive that is important and was not backed up, you could still recover some of it using a tool called [photorec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step").


I didn't have anything too important on there, And I have all of the really important things on my desktop computer just in case I ever needed to recover them.
The only problem is the disk that came with my laptop only works on windows it seems, I went inside the disk and the only thing that would help to run it is the .exe there but it seems Linux cant do anything with that.

Any ideas on how I should run it?

---

### Post by bcbc on 2011-02-23
If it's a bootable DVD then you have to tell your BIOS to boot from it. Usually there's a boot override key F12?? (check your manual or online), but some bios have a boot 'booster' that bypasses the splash, so you might need to disable this first.

---

### Post by bartymany on 2011-02-23
It doesn't seem to boot, I made the CD/DVD priority at the top and it just did the same thing saying to insert a usable driver or something along those lines. Im not sure if it is bootable, or if it will restore my windows 7 as it says its the Asus Driver and Utility disk but it is the only disk that came with the laptop so I am not sure.

---

### Post by bcbc on 2011-02-23
The driver and utility disks are usually just the drivers for your asus specific hardware. The utility are the asus tools.

So, normally you'd install Windows first. Then you need to install the drivers afterwards to get the wireless card, graphics drivers and other specific hardware to work properly.

In other words, you cannot use this to reinstall windows. Asus should provide you with an OEM Windows disk if you request it, although they'll probably charge you for the pleasure (it should still be less than buying a windows disk from the store). 

These days, it seems manufacturers advise to create system restore disks when you get a new computer  - and don't supply the OS as a separate disk.

---

### Post by bartymany on 2011-02-23
Ugh, Im not going to pay for something that I already should own, I guess ill stick with Ubuntu, ill just need to find a way to install it properly and to fix the resolution. Any ideas or should I make a new thread asking?

---

### Post by bcbc on 2011-02-23
Another option - you probably have a sticker on the bottom of the computer with the windows license key. So all you have to do is borrow a windows 7 disk from someone, and enter your own license key when prompted. (You probably have to make sure it's the same version - e.g. starter/home premium/ultimate/pro whatever you originally had).


This thread seems to have a solution for Sis Mirage card: [http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)

---

### Post by bartymany on 2011-02-23
Okay, I just tried that and it didn't work, I think it is probably because Ubuntu is still just on the USB and will not install properly to the hard drive and so the changes didn't save, any ideas?

Also, thanks for the idea with the friends with windows seven, none of my friends have it at the moment, if any .of them get it ill be sure to ask, but for now if I can fix this ill stick with Linux

---

### Post by bcbc on 2011-02-23
> **bartymany said:**
> Okay, I just tried that and it didn't work, I think it is probably because Ubuntu is still just on the USB and will not install properly to the hard drive and so the changes didn't save, any ideas?

Also, thanks for the idea with the friends with windows seven, none of my friends have it at the moment, if any .of them get it ill be sure to ask, but for now if I can fix this ill stick with Linux

What happens when you boot without your USB plugged in? From the bootinfoscript results, it looks like your hard drive install should boot fine.

---

### Post by bartymany on 2011-02-23
Last time I tried it just gave me a black screen saying something about putting in the proper boot device, ill try again.

---

### Post by bcbc on 2011-02-23
Hold on, there is a problem with this version of bootinfoscript - it doesn't always report the drive that the Grub2 bootloader is referencing accurately.

Do this: 
Boot to your live environment
Then drop to a terminal (CTRL+ALT+t) and run:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should fix it - then reboot without the USB plugged in.

---

### Post by bartymany on 2011-02-23
> **bcbc said:**
> Hold on, there is a problem with this version of bootinfoscript - it doesn't always report the drive that the Grub2 bootloader is referencing accurately.

Do this: 
Boot to your live environment
Then drop to a terminal (CTRL+ALT+t) and run:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```That should fix it - then reboot without the USB plugged in.


Okay, I just did this now, Rebooting...

---

### Post by bcbc on 2011-02-23
Something else... since you are using netbook-edition, you might want to check the session settings when you login: click on your user name and look at the bottom of the screen. The 10.10 netbook-edition uses Unity by default and this doesn't work well on all graphics cards. Try selecting the gnome desktop manager and see if that works better for you.

It doesn't sound like this is your problem, as that other thread indicates you need a different driver, but you may have additional problems with Unity (it doesn't work at all on my computer).

---

### Post by bartymany on 2011-02-23
> **bcbc said:**
> Something else... since you are using netbook-edition, you might want to check the session settings when you login: click on your user name and look at the bottom of the screen. The 10.10 netbook-edition uses Unity by default and this doesn't work well on all graphics cards. Try selecting the gnome desktop manager and see if that works better for you.

It doesn't sound like this is your problem, as that other thread indicates you need a different driver, but you may have additional problems with Unity (it doesn't work at all on my computer).

I just rebooted, it is the exact same thing happening, and by the way, I just copied down an error I get every time, Im going to say what I do to get to mozilla firefox and everything just to make it clear and see if that is the problem.

When I reboot with the USB in, I get the ubuntu loading screen, a load of text in a terminal looking page and then When it loads I see an installer, I have to exit that because it doesn't install, it then freezes for about 2 minutes then I get to a login screen and an error comes up saying " No required driver detected for unity you will need to choose the ubuntu desktop session once you select user name if on ubuntu CS the username is ubuntu and you will have to enter a blank password "  So I follow those instructions to log in then go to firefox. Any ideas?     Also I never actually seem to get to choose my login name, where on the other ubuntu it asked when installing (Which it does on this one but it doesn't install properly)

---

### Post by bcbc on 2011-02-23
> **bartymany said:**
> I just rebooted, it is the exact same thing happening, and by the way, I just copied down an error I get every time, Im going to say what I do to get to mozilla firefox and everything just to make it clear and see if that is the problem.

When I reboot with the USB in, I get the ubuntu loading screen, a load of text in a terminal looking page and then When it loads I see an installer, I have to exit that because it doesn't install, it then freezes for about 2 minutes then I get to a login screen and an error comes up saying " No required driver detected for unity you will need to choose the ubuntu desktop session once you select user name if on ubuntu CS the username is ubuntu and you will have to enter a blank password "  So I follow those instructions to log in then go to firefox. Any ideas?     Also I never actually seem to get to choose my login name, where on the other ubuntu it asked when installing (Which it does on this one but it doesn't install properly)

If you are booting from the live USB - which you are - then you don't get to login. It will boot to the desktop automatically.

So it seems there is some problem with the installed Ubuntu. When you boot again (without the USB) hold down the SHIFT key and you should see a grub menu. Then choose to boot either the recovery mode, or 'e'dit the first entry and remove 'quiet splash', then CTRL+x to boot. That should show where it's failing.

---

### Post by bartymany on 2011-02-23
> **bcbc said:**
> If you are booting from the live USB - which you are - then you don't get to login. It will boot to the desktop automatically.

So it seems there is some problem with the installed Ubuntu. When you boot again (without the USB) hold down the SHIFT key and you should see a grub menu. Then choose to boot either the recovery mode, or 'e'dit the first entry and remove 'quiet splash', then CTRL+x to boot. That should show where it's failing.

I rebooted and held Shift and nothing different happened, I then tried repeatedly pressing it and nothing happened.

---

### Post by bcbc on 2011-02-23
> **bartymany said:**
> I rebooted and held Shift and nothing different happened, I then tried repeatedly pressing it and nothing happened.

OK I see you mentioned earlier that it asks to 'insert a proper boot device'. So that means your bios can't boot from the hard drive. Not really sure why this would be. 

If you go to the disk utility (boot the USB, then click on system, administration, Disk Utility) - see whether there are any errors.

Nothing that seems to stand out from the bootinfoscript, but I am at a bit of a loss to explain why it won't boot from it.
Also go into the BIOS and make sure the hard drive is selected as a boot device.

---

### Post by bartymany on 2011-02-23
> **bcbc said:**
> OK I see you mentioned earlier that it asks to 'insert a proper boot device'. So that means your bios can't boot from the hard drive. Not really sure why this would be. 

If you go to the disk utility (boot the USB, then click on system, administration, Disk Utility) - see whether there are any errors.

Nothing that seems to stand out from the bootinfoscript, but I am at a bit of a loss to explain why it won't boot from it.
Also go into the BIOS and make sure the hard drive is selected as a boot device.

I went into the disk utility and I cant see any errors. In BIOS Hard Drive is 3rd behind Removable Device and CD/DVD, should I put it at first?

---

### Post by bcbc on 2011-02-23
> **bartymany said:**
> I went into the disk utility and I cant see any errors. In BIOS Hard Drive is 3rd behind Removable Device and CD/DVD, should I put it at first?

No - I don't think it matters where it is in the boot order. It would have been strange if it wasn't there - but I thought it was worth checking because otherwise I can't explain why the BIOS doesn't see it as bootable, but it appears normal from the bootinfoscript.

So ... basically I am stumped.

---

### Post by bartymany on 2011-02-23
I desperately need help, I dont know what to do, I use my laptop for so much now that I cant really use it for that it seems pointless, It seems like nothing is going to fix it.

Extra information that I just figured out (I think) I was downloading something and it said that I only had 300mb left, I have a 250GB harddrive and I haven't downloaded that much on linux yet, So I think that it is trying to install to the USB and all of my files are too, although I cant install without the USB in but does this help at all?

I feel really annoyed at myself for making this happen =(

---

### Post by bcbc on 2011-02-23
I would try reinstalling again. I don't know why it shouldn't boot: you can see the drive and all the files appear to be in place. yet the bios complains there is no bootable device. This doesn't make any sense to me. 

Or you could try [chrooting to the install]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") (Method 3) and reinstalling grub that way. But I'd only bother with that if you had some data on it and it doesn't sound like you do.

---

