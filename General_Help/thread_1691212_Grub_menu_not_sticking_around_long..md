---
title: "Grub menu not sticking around long."
date: 2011-02-19
forum: General Help
---

### Post by Turtle.eh on 2011-02-19
Hopefully I am in the right forum for this question, but I need help regarding Grub. 

I just installed Ubuntu 10.10 in hopes of dual-booting with Windows XP. (XP was already installed.) When I boot up, the Grub menu flashes briefly on the screen, then it immediately boots Ubuntu, which is the default. I've searched the forums and only found information regarding setting the defaults in /etc/default/grub. I already have them set to:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

I'm using a laptop with centrino processor, in case that has any bearing.  

Any ideas as to why the menu isn't sticking around long enough to make a selection?

Thanks for any help anyone can supply,
Turtle.

---

### Post by Rubi1200 on 2011-02-19
Hi and welcome to the forums :-)

In Ubuntu, run this command and post the output back here please:

```
sudo fdisk -lu
```

Thanks.

---

### Post by tredegar on 2011-02-19
> Any ideas as to why the menu isn't sticking around long enough to make a selection?
You need to run ```
sudo update-grub
``` for the changes you have made to the configuration files to take effect.

---

### Post by Turtle.eh on 2011-02-19
Firstly, thanks for the responses.

I hadn't run the grub update, since I didn't actually update the grub file, it was already set to 10 seconds. (Though, I just updated it now and it didn't help.)

I typed sudo fdisk -lu and this was the output...

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc864

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117542311    58771124+   7  HPFS/NTFS
/dev/sda2       117542910   234440703    58448897    5  Extended
/dev/sda5       117542912   234252287    58354688   83  Linux
/dev/sda6       234254336   234440703       93184   82  Linux swap / Solaris

Does that help my situation?

Thanks again,
Turtle.

---

### Post by tednix on 2011-02-19
If you edited your Grub configuration file I believe tredegar's suggestion of sudo update-grub is correct.

However if you want to try a graphical method use System > Administration > Start-up Manager.  This little program gives to the option of changing the length of time before Grub2 selects a boot choice.

---

### Post by Krytarik on 2011-02-19
Please uncomment "GRUB_HIDDEN_TIMEOUT" and run update-grub thereafter, this is the default "/etc/default/grub":
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Turtle.eh on 2011-02-19
Thanks, but I tried uncommenting the GRUB_HIDDEN_TIMEOUT, then ran update-grub, but the behaviour on booting hasn't changed. It still just flashes the Grub menu, then defaults immediately to Ubuntu. I've tried holding a number key down during the boot process, to see if it will pick up the "key down" when the menu flashes, but it just causes a series of annoying beeps, then still defaults. 

Anything else I can try?

Turtle

---

### Post by Rubi1200 on 2011-02-19
Something is not quite right.

Here is what I suggest (you can also do this from within Ubuntu if you want):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tredegar on 2011-02-20
> Thanks, but I tried uncommenting the GRUB_HIDDEN_TIMEOUT

It needs to be _commented_, if you want to see the menu, like this:```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```

*Then* run **sudo update-grub**

Then reboot.

---

### Post by Krytarik on 2011-02-20
Wether the option is activated and set to "0" or it is deactivated doesn't make any difference for the OP, since it is another OS installed, which is what this is all about.

However, I also didn't see that uncommenting is a valid option.

> 
[LIST]
[*]The default behavior is to hide the menu if only  one operating system is present. If a user with only Ubuntu wishes to  display the menu, place a **#** symbol at the start of this line to disable the hidden menu feature.
[/LIST]

**GRUB_HIDDEN_TIMEOUT=0**  on single operating system computers. 

[LIST]
[*]No menu is displayed. The system is immediately booted to the default OS.
[*]This is the default setting with only one identified operating system.
[LIST]
[*]To display the menu under this condition, place a **#** symbol at the start of the line and ensure the GRUB_TIMEOUT setting is a positive integer.
[/LIST]
 
[*]If the value is set to **0**, a *keystatus* check is performed to determine if the *SHIFT* key is depressed. If GRUB 2 determines the *SHIFT*  key is depressed during the boot process, the menu will be displayed.  This gives the user a method of interrupting an automatic boot which  would normally not display the menu.
[/LIST]
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")

---

### Post by tredegar on 2011-02-20
Krytarik,

You are right.

I find the options in /etc/default/grub very confusing.

Perhaps all the OP needs to do now is run update-grub

---

### Post by Krytarik on 2011-02-20
> **tredegar said:**
> Krytarik,

You are right.

I find the options in /etc/default/grub very confusing.

Perhaps all the OP needs to do now is run update-grub
He/she has already run update-grub, I assume more than once. ;-)

We are still waiting for the results of the boot info script, maybe that gives us the solution.
I somehow suspect a corrupted "/etc/grub.d/00_header" script, which results in the timeout not being set as specified.

---

### Post by Turtle.eh on 2011-02-20
Well, I did as Rubi1200 said and this was the outcome. 

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
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,542,311   117,542,249   7 HPFS/NTFS
/dev/sda2         117,542,910   234,440,703   116,897,794   5 Extended
/dev/sda5         117,542,912   234,252,287   116,709,376  83 Linux
/dev/sda6         234,254,336   234,440,703       186,368  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        AE7420627420300F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        82664147-ffe2-4b75-adee-62f06606442b   ext4                                     
/dev/sda6        2ac10bd4-52f8-4fe7-8204-266790b05a40   swap                                     
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
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82664147-ffe2-4b75-adee-62f06606442b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        82664147-ffe2-4b75-adee-62f06606442b
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        82664147-ffe2-4b75-adee-62f06606442b
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        82664147-ffe2-4b75-adee-62f06606442b
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        82664147-ffe2-4b75-adee-62f06606442b
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro single 
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
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ae7420627420300f
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
# / was on /dev/sda5 during installation
UUID=82664147-ffe2-4b75-adee-62f06606442b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2ac10bd4-52f8-4fe7-8204-266790b05a40 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.6GB: boot/grub/core.img
 109.8GB: boot/grub/grub.cfg
 112.0GB: boot/grub/menu.lst
 112.0GB: boot/initrd.img-2.6.35-22-generic
  60.5GB: boot/vmlinuz-2.6.35-22-generic
 112.0GB: initrd.img
  60.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  af 23 5b 2e 8c c7 dc 12  db 2d 2b 77 00 5c a1 21  |.#[......-+w.\.!|
00000010  0b 31 0e 9c 89 b0 f8 1a  8f 30 59 bb dd 88 a9 20  |.1.......0Y.... |
00000020  bc 2a 6a c8 86 87 24 0a  8c 3b eb b4 0c ca 51 9d  |.*j...$..;....Q.|
00000030  8d 03 4d 66 9c 16 7c e1  51 f9 ca ce b7 3f 5e 60  |..Mf..|.Q....?^`|
00000040  cf 57 06 9e 8a 24 92 36  61 a4 d4 3a be 98 92 d2  |.W...$.6a..:....|
00000050  44 d3 82 20 86 d1 4d 14  4d e5 c2 82 9d db 49 16  |D.. ..M.M.....I.|
00000060  e4 3e 8e 24 b3 8e 2e c4  98 21 27 34 0c c6 46 d3  |.>.$.....!'4..F.|
00000070  46 f0 09 01 20 42 95 47  c0 20 2b a3 de 5f ce e3  |F... B.G. +.._..|
00000080  3e a5 73 ed 92 52 49 06  37 28 bb 94 ed 9e 6e 0d  |>.s..RI.7(....n.|
00000090  8a f6 f5 7b d8 6f 73 3c  bb a7 83 98 e3 ba 6e ef  |...{.os<......n.|
000000a0  36 8e f2 96 81 e3 ae 8d  2c c0 14 51 47 41 16 5a  |6.......,..QGA.Z|
000000b0  08 9c 39 bf ee d8 7e 36  08 0a e6 c9 2b b0 21 64  |..9...~6....+.!d|
000000c0  75 89 91 8d 34 d3 cd 90  94 bb 56 b5 30 a4 92 9c  |u...4.....V.0...|
000000d0  31 d9 f2 48 e1 86 b6 16  ec 75 fc 97 67 79 84 53  |1..H.....u..gy.S|
000000e0  8f ec 85 85 b5 68 39 b8  8d 99 b5 7c 25 8d 22 df  |.....h9....|%.".|
000000f0  5b 50 66 e1 6c 5b a2 8a  69 95 40 d2 44 e7 e7 25  |[Pf.l[..i.@.D..%|
00000100  8a 35 05 e4 ce 84 80 fc  36 61 12 2c 43 a8 24 9d  |.5......6a.,C.$.|
00000110  b3 9a 95 c5 9e 28 74 a9  84 13 c7 28 75 0e d2 cb  |.....(t....(u...|
00000120  7e ed 2f 6f 6e c6 fb f1  1b 1f 71 d0 c2 cf 37 2a  |~./on.....q...7*|
00000130  b5 bb 4b 6d a0 b4 78 b9  36 ec 24 a3 53 56 38 e2  |..Km..x.6.$.SV8.|
00000140  aa 6d 6f cb 52 b3 75 2b  cc 4d 00 6a 9c da ef 40  |.mo.R.u+.M.j...@|
00000150  73 56 79 1e e2 66 cd 50  4a f0 ad 68 48 a0 62 43  |sVy..f.PJ..hH.bC|
00000160  a4 69 92 a2 e6 4d c8 36  a7 65 ab 6b 64 d3 1f 73  |.i...M.6.e.kd..s|
00000170  51 4e 2e cb 09 2c 08 39  c7 a2 4e 0d 99 ee c4 99  |QN...,.9..N.....|
00000180  63 93 ef d0 67 75 4a 6f  86 9d a6 91 31 78 5b 4f  |c...guJo....1x[O|
00000190  a3 2d 8b d4 f5 09 01 b4  19 13 25 01 c5 b6 30 05  |.-........%...0.|
000001a0  9a 7b a5 c5 b5 77 21 a6  f0 45 d0 f5 d0 dd 7b 92  |.{...w!..E....{.|
000001b0  f8 a5 fb af 4c 0f f8 ca  ec eb 95 e1 ee cd 00 fe  |....L...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 f4 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  f4 06 00 e0 02 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2011-02-20
You have a mix of legacy-GRUB and GRUB2.

The best thing to do would be to purge and reinstall GRUB from the LiveCD:

```
sudo mkdir /mnt/temp
sudo mount /dev/sda5 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```These commands will bring you to a root prompt, then:
```
apt-get update
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```Reboot without the LiveCD.

(purge and reinstall method courtesy of drs305)

---

### Post by Krytarik on 2011-02-20
Though I also would try a reinstall of Grub2, and definetely a purge of Grub1. But I'm wondering why the parallel install of both versions would be a problem, since there is only one Grub at the bootsector at a time. I also have some remnants of Grub2 at my mom's machine, though I removed the package (was the only solution to boot Windows7 again after a disk change).

And I suppose the OP doesn't need to do the purge/reinstall via the chroot procedure, since he/she can boot Ubuntu fine.

---

### Post by Turtle.eh on 2011-02-20
I tried running Rubi1200's fix, but it hasn't improved my situation. I still get a quick flash of a Grub menu, then straight into Ubuntu. The only thing noteworthy that happened during the Grub reinstall was that a window popped up titled "Configuring Grub-PC". It read something along the lines of "The following line is from /etc/default/grub or the 'kopt' parameter in Grub legacy's menu.lst. Please verify or correct it". It then had a blank command line and an O.K. button. I Okayed it and it went to completion. 

I have again run the script tool and will include the new output RESULTS.txt, which is as follows:

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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,542,311   117,542,249   7 HPFS/NTFS
/dev/sda2         117,542,910   234,440,703   116,897,794   5 Extended
/dev/sda5         117,542,912   234,252,287   116,709,376  83 Linux
/dev/sda6         234,254,336   234,440,703       186,368  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        AE7420627420300F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        82664147-ffe2-4b75-adee-62f06606442b   ext4                                     
/dev/sda6        2ac10bd4-52f8-4fe7-8204-266790b05a40   swap                                     
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
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

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
search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82664147-ffe2-4b75-adee-62f06606442b ro single 
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
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 82664147-ffe2-4b75-adee-62f06606442b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ae7420627420300f
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
# / was on /dev/sda5 during installation
UUID=82664147-ffe2-4b75-adee-62f06606442b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2ac10bd4-52f8-4fe7-8204-266790b05a40 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.6GB: boot/grub/core.img
  73.2GB: boot/grub/grub.cfg
 112.0GB: boot/initrd.img-2.6.35-22-generic
  60.5GB: boot/vmlinuz-2.6.35-22-generic
 112.0GB: initrd.img
  60.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  af 23 5b 2e 8c c7 dc 12  db 2d 2b 77 00 5c a1 21  |.#[......-+w.\.!|
00000010  0b 31 0e 9c 89 b0 f8 1a  8f 30 59 bb dd 88 a9 20  |.1.......0Y.... |
00000020  bc 2a 6a c8 86 87 24 0a  8c 3b eb b4 0c ca 51 9d  |.*j...$..;....Q.|
00000030  8d 03 4d 66 9c 16 7c e1  51 f9 ca ce b7 3f 5e 60  |..Mf..|.Q....?^`|
00000040  cf 57 06 9e 8a 24 92 36  61 a4 d4 3a be 98 92 d2  |.W...$.6a..:....|
00000050  44 d3 82 20 86 d1 4d 14  4d e5 c2 82 9d db 49 16  |D.. ..M.M.....I.|
00000060  e4 3e 8e 24 b3 8e 2e c4  98 21 27 34 0c c6 46 d3  |.>.$.....!'4..F.|
00000070  46 f0 09 01 20 42 95 47  c0 20 2b a3 de 5f ce e3  |F... B.G. +.._..|
00000080  3e a5 73 ed 92 52 49 06  37 28 bb 94 ed 9e 6e 0d  |>.s..RI.7(....n.|
00000090  8a f6 f5 7b d8 6f 73 3c  bb a7 83 98 e3 ba 6e ef  |...{.os<......n.|
000000a0  36 8e f2 96 81 e3 ae 8d  2c c0 14 51 47 41 16 5a  |6.......,..QGA.Z|
000000b0  08 9c 39 bf ee d8 7e 36  08 0a e6 c9 2b b0 21 64  |..9...~6....+.!d|
000000c0  75 89 91 8d 34 d3 cd 90  94 bb 56 b5 30 a4 92 9c  |u...4.....V.0...|
000000d0  31 d9 f2 48 e1 86 b6 16  ec 75 fc 97 67 79 84 53  |1..H.....u..gy.S|
000000e0  8f ec 85 85 b5 68 39 b8  8d 99 b5 7c 25 8d 22 df  |.....h9....|%.".|
000000f0  5b 50 66 e1 6c 5b a2 8a  69 95 40 d2 44 e7 e7 25  |[Pf.l[..i.@.D..%|
00000100  8a 35 05 e4 ce 84 80 fc  36 61 12 2c 43 a8 24 9d  |.5......6a.,C.$.|
00000110  b3 9a 95 c5 9e 28 74 a9  84 13 c7 28 75 0e d2 cb  |.....(t....(u...|
00000120  7e ed 2f 6f 6e c6 fb f1  1b 1f 71 d0 c2 cf 37 2a  |~./on.....q...7*|
00000130  b5 bb 4b 6d a0 b4 78 b9  36 ec 24 a3 53 56 38 e2  |..Km..x.6.$.SV8.|
00000140  aa 6d 6f cb 52 b3 75 2b  cc 4d 00 6a 9c da ef 40  |.mo.R.u+.M.j...@|
00000150  73 56 79 1e e2 66 cd 50  4a f0 ad 68 48 a0 62 43  |sVy..f.PJ..hH.bC|
00000160  a4 69 92 a2 e6 4d c8 36  a7 65 ab 6b 64 d3 1f 73  |.i...M.6.e.kd..s|
00000170  51 4e 2e cb 09 2c 08 39  c7 a2 4e 0d 99 ee c4 99  |QN...,.9..N.....|
00000180  63 93 ef d0 67 75 4a 6f  86 9d a6 91 31 78 5b 4f  |c...guJo....1x[O|
00000190  a3 2d 8b d4 f5 09 01 b4  19 13 25 01 c5 b6 30 05  |.-........%...0.|
000001a0  9a 7b a5 c5 b5 77 21 a6  f0 45 d0 f5 d0 dd 7b 92  |.{...w!..E....{.|
000001b0  f8 a5 fb af 4c 0f f8 ca  ec eb 95 e1 ee cd 00 fe  |....L...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 f4 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  f4 06 00 e0 02 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Did I at least manage to get down to one version of Grub? 

Many more thanks,
Turtle

---

### Post by SwedishWings on 2011-02-20
I have exactly the same problem on an old unbranded laptop that i just dusted of. 

I have multiple OS: XP, Lucid and Maverick. 

When i installed Maverick this problem came along (i'm now booting via Grub2 that was installed with Maverick).
  
No matter what i try it just boot the default OS. I have never had any problem like this before on that laptop. Maybe something is weird with Grub2?

EDIT: I should add that i can change what OS is booted via GRUB_DEFAULT=...  and then run update-grub. This was NOT happening with grub1.

---

### Post by Rubi1200 on 2011-02-20
> it hasn't improved my situation. I  still get a quick flash of a Grub menu, then straight into Ubuntu.
How strange!

> Did I at least manage to get down to one version of Grub? 
Yes.

The results indicate that you should be able to boot both operating systems.

So let's run through some other possibilities:

is BIOS set to boot from the HDD first?

was Windows booting normally before this all began?

did you run chkdsk on Windows after partitioning or after installing at some point?

do you have a Windows CD so you can run a chkdsk now?

---

### Post by Turtle.eh on 2011-02-20
O.K., the plot thickens!!
 
To Answer Rubi1200's questions, Yes, BIOS is set to boot from the HDD first and windows was completely normal before I installed Ubuntu. I hadn't run chkdsk on the partitioned drive, but I do have the Windows CD. 
 
Here's where it gets a little weird. I put the Windows CD in the drive and hit Esc during boot-up to bring up the alternate boot sources menu. I selected CD and hit enter. It gave me a message of "CD ROM Type - non-emulation booting. Press any key to boot from CD". I didn't hit anything and after a few seconds it brought up my Grub menu. Yup, little timer counting down from 10 and everything. I seleceted windows and hit enter, it suggested and ran chkdsk (0 bytes in bad sectors) and booted up into XP. I shut it down and tried it again, and once again, the Grub menu came up. I selected XP again and it booted up, no problem. If I boot from the HDD, it still just flashes the Grub menu and defaults and if I boot from the Ubuntu CD, it boots immediately from the CD. (Just for fun, I tried booting from a blank CD to see if the Grub menu would come up. No luck. It just keeps returning me to the device selection menu.)
 
 
Can this behavior be explained, other than my laptop is possessed!

---

### Post by Rubi1200 on 2011-02-20
> Can this behavior be explained, other than my laptop is possessed! 	
Yes, it can be explained, and, no, it is not possessed.

I saw a post about something very similar but it was a long time ago.

I will try and find it and get back to you.

---

### Post by oldfred on 2011-02-20
rubi1200 asked me if I remembered & I do not. I have nothing in my notes either that I can find.

I do vaguely remember some issues with an older version of grub2 that someone else just had a post on. It was related to grubenv. I think that issue was if grub had an issue booting it set a flag that then was supposed to boot to recovery mode next time. But All the windows CD should do is chainload to the hard drive's MBR and grub should boot the same way?

---

### Post by Krytarik on 2011-02-20
If no one comes up with a better idea, I suggest trying Grub-legacy instead of Grub2. As I said, I had difficulties to boot Windows7 through it after switching to a new HDD, altough Grub2 could boot it just fine before. It just left me with a blinking cursor. I tried each and every suggestion I found in the web at that time, before I decided to give Grub-legacy a try.

---

### Post by oldfred on 2011-02-20
Sometimes with XP even though users have been able to boot when on separate drives but not boot with grub, running the windows repairs resolved the issue. That may be worth doing.

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

If you run the fixMBR command, then you will have to reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Turtle.eh on 2011-02-21
I'm at work today, so it'll have to wait until I get home, but I'll give the XP fix a try later tonight. If that doesn't work, I'll try to find instructions on how to purge Grub2 and install Grub-legacy. 
 
In the interim, I made a copy of the windows CD that I can leave in the drive and use to force the Grub menu to show up. So at least I can boot XP, if need be. (I'm trying to break that habit.)
 
Given that this seems to be more of a BIOS/hardware issue, rather than a Grub/Ubuntu issue, should I tag this as resolved? Maybe it's time I invest in a laptop that isn't almost 10 years old!
 
Turtle.

---

### Post by Krytarik on 2011-02-21
Hey, I'm also at a 10-year-old computer, and it is still working good enough! :P

And I believe it's indeed a Grub issue, since it's its task to boot the different OSes, and all what your BIOS/computer needs to do is to bring you there, and it does that just fine.

---

### Post by Turtle.eh on 2011-02-23
Well, I'm still kicking at the elusive can!

I followed the instructions and ran the FIXMBR and FIXBOOT commands. When I rebooted, my laptop booted directly in to XP. (As was expected) I then used the link to figure out how to restore the Ubuntu bootloader. After I reinstalled Grub, booting once again just flashed the Grub menu and booted directly into Ubuntu. Obviously I missed something. When I ran FIXMBR and FIXBOOT, I figured I was re-initiating the Windows boot loader. I figure the next thing I want to do is to add Ubuntu to the Windows bootloader and use it's dual-boot abilities. Obviously not what I did. 

Next up, I'll do a little research to Windows dual-booting. Failing all else, I may try to revert back to Grub-legacy. (Once upon a time, I had Ubuntu 8.04 installed and Grub worked great with XP.)

Meanwhile, if anyone cares to point out my errors, I'm all ears.

Turtle.

---

### Post by Krytarik on 2011-02-23
I never set up the Windows boot loader to chainload into the Grub menu, but since I see it with Wubi it is apparently possible. Normally it is the other way around, like you had/have it, but it should of course work. ;-)

---

### Post by Turtle.eh on 2011-02-28
Well, I've solved my problem, sort of.

No matter what I did, I couldn't get the Grub2 menu to stick around long enough to choose an option, short of booting from the XP disk, as mentioned in an earlier post. So, I reverted back to plain old Grub and it works like a charm. Sure I'm a total failure, but I've learned a lot through all my efforts and I can finally dual boot XP and Ubuntu 10.10, which is what I was trying to accomplish. 

Hopefully my next "Forced Lesson" doesn't debilitate my laptop in the interim!

Thanks for all your help,
Turtle.

---

### Post by Krytarik on 2011-02-28
> **Turtle.eh said:**
> So, I reverted back to plain old Grub and it works like a charm. Sure I'm a total failure, but I've learned a lot through all my efforts and I can finally dual boot XP and Ubuntu 10.10, which is what I was trying to accomplish. 

Hey, it is not our fault that Grub2 isn't always working as it should. If that means, that we have to make a step backwards in some cases, well, so be it. I can live with it, when it lets me boot into the OS or kernel option of my choice, or even boot at all. ;-)

PS: Then please mark this thread as "solved", via "Thread Tools", unless you determines this on Grub2.

---

