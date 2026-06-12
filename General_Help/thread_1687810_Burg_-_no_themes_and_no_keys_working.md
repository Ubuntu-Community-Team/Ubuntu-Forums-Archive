---
title: "Burg - no themes and no keys working"
date: 2011-02-14
forum: General Help
---

### Post by doles2 on 2011-02-14
Hi there,
i was trying to install burg on my Ubuntu maverick, but there are some problems. I have no themes at all and there are no such keys like "t" for switching themes and functional keys. Burg is working, i can something like this with "sudo burg-emu -D" and there is the same screen during booting system.
[IMG]http://img696.imageshack.us/img696/3748/zrzutekranunn.png[/IMG]
I installed it on /dev/sda using:
```
sudo burg-install "(hd0")
```

And then i got themes and stuff from apt, just everything went fine using this link:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

Here is my /etc/default/burg:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
#GRUB_SAVEDEFAULT=true

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# In the boot menu, use hotkey 'r' to popup a resolution selection menu.

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# GRUB_THEME's value can be 'saved' or a specific BURG theme name, you can also
# set it to the pathname of a GRUB2 theme file.
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=saved

# GRUB_FOLD's value can be 'saved', 'true' or 'false'.
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved

# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="

# For a complete list of supported variables, refer to this wiki page:
# http://code.google.com/p/burg/wiki/ConfigurationVariables
GRUB_GFXMODE=1366x768
GRUB_DISABLE_LINUX_RECOVERY="true"
```

It seems that burg works out of the box, but for me :/ I have no idea what's wrong. Some ideas ?

---

### Post by aircrack on 2011-03-14
Im having exactly the same Problem.
Did anyone manage to fix this?

I thought Id rather not start a new thread with exactly the same content, so I continued this one.

---

### Post by Mi11z on 2011-03-30
Same problem over here too. :(

---

### Post by stinkeye on 2011-03-30
I'm assuming you have already added the repo
and installed the appropriate packages.
If so skip this bit.
```
sudo add-apt-repository ppa:bean123ch/burg
sudo apt-get update
sudo apt-get install burg-pc burg-themes burg-emu burg-common burg-themes-common
```



Enter in the terminal
```
sudo fdisk -l
```
your boot drive is marked with an asterisk
Usually sda.
eg```
glen@MavMusic:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e1e4b27

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   [COLOR="Red"]*[/COLOR]           1       15340   123218518+   7  HPFS/NTFS
/dev/sda2           15341       45503   242284297+   7  HPFS/NTFS
/dev/sda3           45504       60801   122881185    f  W95 Ext'd (LBA)
/dev/sda5           45504       60801   122881153+  83  Linux
```


Then run
```
sudo burg-install /dev/[COLOR="DarkOrchid"]sda[/COLOR]
```
[COLOR="#9932cc"]**Using the drive shown to you in the previous command**[/COLOR].
**Do not use /dev/sda1, use /dev/sda as you want to install to the drive not the partition.**


**[SIZE="2"]or[/SIZE]**
```
sudo dpkg-reconfigure burg-pc
```
and you will be asked to select your drive.


Run 
```
sudo update-burg
```

---

### Post by Mi11z on 2011-04-02
Thanks for that reply, I'm trying now...


**********************************************EDITED*********************************************************

Thanks again, I did and tried everything you mentioned above and I'm back to normal cheers! I'll make a note of this for future occurrences. :D

**********************************************EDITED*********************************************************

LOL and a special thanks again to you too stinkeye, we meet again in cyberspace! :D

---

### Post by FokkerCharlie on 2011-05-02
I have (re) tried all the above steps, but still seeing my old-style GRUB menu.  Anything else to try?

Charlie

---

### Post by stinkeye on 2011-05-02
> **FokkerCharlie said:**
> I have (re) tried all the above steps, but still seeing my old-style GRUB menu.  Anything else to try?

Charlie
Download this script and place it in your home folder.
It will show all the info about your boot environment.
[**_[COLOR="DarkRed"]http://sourceforge.net/projects/bootinfoscript/[/COLOR]_**]("http://sourceforge.net/projects/bootinfoscript/")

Then run in terminal with
```
sudo bash ~/boot_info_script055.sh
```

This will place a **RESULTS.txt** file in your home folder.

Copy and paste the entire contents of RESULTS.txt in a post using the code tags ("#" button)
Someone with a better knowledge of grub than me will be able to help you.

---

### Post by FokkerCharlie on 2011-05-07
Cool.  Grateful for anyone who can help me with this!

Charlie

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/burg.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   105,466,724   102,392,677   7 HPFS/NTFS
/dev/sda3         105,467,904   154,294,271    48,826,368  83 Linux
/dev/sda4         154,296,318   976,771,071   822,474,754   5 Extended
/dev/sda5         154,296,320   170,295,295    15,998,976  82 Linux swap / Solaris
/dev/sda6         170,297,344   976,771,071   806,473,728  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9CBE38ACBE3880B6                       ntfs       System                        
/dev/sda2        92BE5E75BE5E51B9                       ntfs       TI30596700A                   
/dev/sda3        b261fe00-4cf7-45a9-a27c-bef9bab1452e   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1361952c-f6f5-40e4-918f-443ef83064f5   swap                                     
/dev/sda6        0c1f5efe-a15e-4920-9692-9c6d858c3569   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda6        /home                    ext4       (rw,commit=600)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  set gfxpayload=keep
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro  vga=792 splash quiet  quiet splash video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro single  vga=792 splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro  vga=792 splash quiet  quiet splash video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro single  vga=792 splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro  vga=792 splash quiet  quiet splash video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	echo	'Loading Linux 2.6.35-29-generic ...'
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro single  vga=792 splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro  vga=792 splash quiet  quiet splash video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro single  vga=792 splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro  vga=792 splash quiet  quiet splash video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e ro single  vga=792 splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root b261fe00-4cf7-45a9-a27c-bef9bab1452e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9CBE38ACBE3880B6
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 92BE5E75BE5E51B9
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=b261fe00-4cf7-45a9-a27c-bef9bab1452e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0c1f5efe-a15e-4920-9692-9c6d858c3569 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1361952c-f6f5-40e4-918f-443ef83064f5 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  56.3GB: boot/grub/core.img
  56.4GB: boot/grub/grub.cfg
  68.0GB: boot/initrd.img-2.6.32-24-generic
  66.8GB: boot/initrd.img-2.6.32-25-generic
  65.8GB: boot/initrd.img-2.6.35-29-generic
  67.9GB: boot/initrd.img-2.6.38-8-generic
  77.0GB: boot/initrd.img-2.6.38-9-generic
  57.7GB: boot/vmlinuz-2.6.32-24-generic
  57.5GB: boot/vmlinuz-2.6.32-25-generic
  62.2GB: boot/vmlinuz-2.6.35-29-generic
  73.0GB: boot/vmlinuz-2.6.38-8-generic
  73.5GB: boot/vmlinuz-2.6.38-9-generic
  77.0GB: initrd.img
  67.9GB: initrd.img.old
  73.5GB: vmlinuz
  73.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 20 f4 00 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  f4 00 00 d8 11 30 00 00  |....... .....0..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by radolavv on 2012-09-09
I have the same problem, the above solution dosent work for me.

---

### Post by wildmanne39 on 2012-09-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

