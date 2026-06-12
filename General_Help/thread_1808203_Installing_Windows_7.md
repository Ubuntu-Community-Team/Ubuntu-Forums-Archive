---
title: "Installing Windows 7"
date: 2011-07-20
forum: General Help
---

### Post by sageofmali on 2011-07-20
Okay, I need help installing Windows 7 Ultimate 64 bit, using Unetbootin, without a USB, nor CD/DVD.  Is there anyway to do this?  When I used unetbootin and click to put windows 7 iso on hard disk it extracted it to the "/" directory. So, I rebooted my computer and went to grub, but Windows 7 ceased to exist.  Is there anything I could do?  Please help. :'(  I'm 15, haha, no money for DVD's to burn.  I have an eMachines ET1331G-05w Desktop.  So, what do I do?  I know it came pre-installed with Windows but I liked Ubuntu better.  I would now like to use windows so I could play games better(I hate using wine).

---

### Post by pinballwizard on 2011-07-20
The only thing I know is that Win7 kills GRUBs... I had to install Win7 first, and then install Ubuntu.

---

### Post by Niocora on 2011-07-20
I'm not that experienced, so I am not entirely sure, But for me win7  Does nothing to the mbr. (Master boot record) If you install win7 on a seperate partition, nothing will happen when you boot and you will have a useless OS. The only way I know is winslush first. Linux 2nd.

Have you tried PlayOnLinux? It is available via the ubuntu software center and works a little better.

---

### Post by mastablasta on 2011-07-20
both above are poor advice, becuase all you need to do to is restore grub.
 
now back to the original quesiton. no it is not possible to install windows without original CD/DVD and/or USBkey. unless you are trying to install pirated version. 
 
also since this is "how do i install windows?" question this belongs to windows forums or Microsoft support (call support or pages).
 
a hint: drive section needs to be formated for windows (probably in NTFS file system). it's best to designate it first. it has to be primary partition (not extended) and you will need to proceed with install from the original DVD from that point on.

---

### Post by alphaamanitin on 2011-07-20
> **mastablasta said:**
> both above are poor advice, becuase all you need to do to is restore grub.
 
now back to the original quesiton. no it is not possible to install windows without original CD/DVD and/or USBkey. unless you are trying to install pirated version. 
 



This is simply not true (the windows bit).  No you do not need the original DVD or USB.  All you need is a DVD or USB of the same version of your license (CD key).  Or in fact it you have the ability to modify the .iso or .img file of a windows dvd you can remove a certain file and make it be able to install any version of windows from that DVD (but not different architectures, so a x32 cannot install any x64 version and vice-versa).  And no that wouldn't be a pirated copy or an illegal copy in any way, because you would use the CD-Key or license that you purchased and had a legal right to install (the key should be on a sticker on the outside of your emachine some where).  And besides that is not what you asked.  You asked if it was possible to install Windows 7 without a cd/dvd/usb, and the answer is no.  The OS has to be on something that you can boot the computer from to install.  

Now, you also do not need to repair GRUB, because your post seems to indicate that you don't have windows 7 installed anywhere on the machine.  So despite what mastablasta said that is not an option.  From what I can tell you simply extracted an windows 7 iso (which given your post I question how you go it) into the root directory of your Ubuntu partition.  Well, so what, the files are probably still there but you didn't actually install Windows so it will not run.  From your post I would say there is no way for you to install windows 7.  If you cannot get and burn a DVD or use a USB there is simply no way for you to install windows 7.  

Find a way to buy a DVD, burn your windows 7 iso to it, boot your computer from the DVD drive, use your license key that is on your emachines somewhere and install windows 7 to your machine.  

AlphaA

---

### Post by oldfred on 2011-07-20
Some clues here:

Use unetbootin to copy windows iso to partition and install:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)

You do have to install to a primary partition formated NTFS with the boot flag (active partition in windows).

---

### Post by sageofmali on 2011-07-20
Is there a way to partition without using a live CD?  I have one main partition(The one I'm using), which is /dev/sda1 I think.  Also, the Linux swap.

---

### Post by kroq-gar78 on 2011-07-20
If you haven't used all of your disk space yet, then I'm pretty sure you don't have to use a LiveCD to parition. Also, you don't have to burn a CD to use an ubuntu Live Image. Look here: [http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html](http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html)

I haven't tried it yet, so I probably won't be of any help.

And yes, you haven't installed Windows yet, so you don't need to repair GRUB (yet).

Sincerely,
kroq-gar78

---

### Post by sageofmali on 2011-07-22
> **kroq-gar78 said:**
> If you haven't used all of your disk space yet, then I'm pretty sure you don't have to use a LiveCD to parition. Also, you don't have to burn a CD to use an ubuntu Live Image. Look here: [http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html](http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html)

I haven't tried it yet, so I probably won't be of any help.

And yes, you haven't installed Windows yet, so you don't need to repair GRUB (yet).

Sincerely,
kroq-gar78
I've been trying unetbootin, but it doesn't show up in the grub menu.  Another thing is that, when I boot my computer, the grub menu quickly disappears and goes straight to Ubuntu.

---

### Post by kroq-gar78 on 2011-07-22
> **sageofmali said:**
> I've been trying unetbootin, but it doesn't show up in the grub menu.  Another thing is that, when I boot my computer, the grub menu quickly disappears and goes straight to Ubuntu.
You have to hold down SHIFT almost right after the BIOS message (shows your manufacturer's logo, 'press F10 for boot menu options' or something like that). The reason why that happens is because GRUB deson't detect any other OS's and it's default is to then boot into Ubuntu. I tried using UNetBootin to boot one of my 2000 (not really) linux ISO's, but it never worked. IMHO, grub iso booting looks more reliable, but I haven't tried it.

Hope it helps.

---

### Post by sageofmali on 2011-07-22
> **kroq-gar78 said:**
> You have to hold down SHIFT almost right after the BIOS message (shows your manufacturer's logo, 'press F10 for boot menu options' or something like that). The reason why that happens is because GRUB deson't detect any other OS's and it's default is to then boot into Ubuntu. I tried using UNetBootin to boot one of my 2000 (not really) linux ISO's, but it never worked. IMHO, grub iso booting looks more reliable, but I haven't tried it.

Hope it helps.
It showed up, but it gave me an error: "error you have to load the kernel first."  Or something like that.  It could be that I uninstalled grub2 then installed grub1 then reinstalled grub2.  I did that on an accident.

---

### Post by oldfred on 2011-07-22
Often if you have both versions of grub installed it gets very confused. Best to uninstall both and reinstall the one you want.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you need more details post this to see your entire boot configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by sageofmali on 2011-07-24
> **oldfred said:**
> Often if you have both versions of grub installed it gets very confused. Best to uninstall both and reinstall the one you want.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you need more details post this to see your entire boot configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
I get:
```

brandon@brandon-ET1331G:~$ chroot & grub uninstall & reinstall -drs305
[1] 16327
[2] 16328
chroot: missing operand
Try `chroot --help' for more information.
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
reinstall: command not found
[1]-  Exit 125                chroot
[2]+  Exit 127                grub uninstall
```
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 42326568 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /bootmgr /boot/bcd /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,457,287,167 1,457,285,120  83 Linux
/dev/sda2       1,457,289,214 1,465,147,391     7,858,178   5 Extended
/dev/sda5       1,457,289,216 1,465,147,391     7,858,176  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01d3dad1-4247-49c5-8674-ff4a22550c86   ext4       
/dev/sda5        3b3e6b90-f139-46e7-b851-64543e63d120   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=01d3dad1-4247-49c5-8674-ff4a22550c86

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

title		Ubuntu 11.04, kernel 2.6.38-11-generic
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-10-generic
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-10-generic

title		Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro  single
initrd		/boot/initrd.img-2.6.38-10-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		01d3dad1-4247-49c5-8674-ff4a22550c86
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


title UNetbootin
root (hd0,0)
linux  /boot/ubnkern 
initrd /boot/ubninit 
boot

--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro splash vga=799  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro single splash vga=799
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro splash vga=799  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro single splash vga=799
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro splash vga=799  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 ro single splash vga=799
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01d3dad1-4247-49c5-8674-ff4a22550c86
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
#menuentry "Boot Windows ISO" {
#loopback loop (hd0,1)/home/brandon/Desktop/Downloads/Windows 7.ULTIMATE.SP1.ALL.EDITIONS.32-64.bit-MAFIAA/Windows.7.SP1.ENG.x86-x64.MAFIAA.iso
#linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/brandon/Desktop/Downloads/Windows 7.ULTIMATE.SP1.ALL.EDITIONS.32-64.bit-MAFIAA/Windows.7.SP1.ENG.x86-x64.MAFIAA.iso file=(loop)/preseed/ubuntu.seed quiet splash --
#initrd (loop)/casper/initrd.lz
#}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


menuentry "UNetbootin" {
	set root=(hd0,1)
	linux  /boot/ubnkern 
	initrd /boot/ubninit 
}

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
UUID=01d3dad1-4247-49c5-8674-ff4a22550c86 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=3b3e6b90-f139-46e7-b851-64543e63d120 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.182907104 = 21.671231488   boot/grub/core.img                             1
 576.379611969 = 618.882895872  boot/grub/grub.cfg                             1
 576.379619598 = 618.882904064  boot/grub/menu.lst                             1
   4.068904877 = 4.368953344    boot/initrd.img-2.6.38-10-generic              2
  24.774414062 = 26.601324544   boot/initrd.img-2.6.38-11-generic              2
  22.755435944 = 24.433463296   boot/initrd.img-2.6.38-8-generic               2
  27.473945618 = 29.499924480   boot/vmlinuz-2.6.38-10-generic                 1
  31.122383118 = 33.417404416   boot/vmlinuz-2.6.38-11-generic                 1
  20.133792877 = 21.618495488   boot/vmlinuz-2.6.38-8-generic                  1
  24.774414062 = 26.601324544   initrd.img                                     2
   4.068904877 = 4.368953344    initrd.img.old                                 2
  31.122383118 = 33.417404416   vmlinuz                                        1
  27.473945618 = 29.499924480   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdd



========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sdd: Input/output error
hexdump: /dev/sdd: Input/output error
hexdump: /dev/sdd: Input/output error
unlzma: Decoder error

```

---

### Post by oldfred on 2011-07-25
You do not just type chroot. That was the title of the thread that the link takes you to: Follow the link for detailed instructions, they are moderately complex.

You have no boot loader installed to the MBR of sda. You did install grub to the PBR or partition boot sector of sda1. You almost never install grub2 to the PBR and only when multi-booting may install grub legacy to a PBR.

If you do not have a lot of data in your Ubuntu partition it may be better to start over. You can reinstall Ubuntu in less than an hour normally. 

You then could create a 50GB win7 NTFS partition with the boot flag for windows to install to. Then add a 100 to 200GB NTFS shared partition for any data you want in both. A extended partition for the rest of the drive for Linux or other installs or more data depending on what you want.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by sageofmali on 2011-07-25
> **oldfred said:**
> You do not just type chroot. That was the title of the thread that the link takes you to: Follow the link for detailed instructions, they are moderately complex.

You have no boot loader installed to the MBR of sda. You did install grub to the PBR or partition boot sector of sda1. You almost never install grub2 to the PBR and only when multi-booting may install grub legacy to a PBR.

If you do not have a lot of data in your Ubuntu partition it may be better to start over. You can reinstall Ubuntu in less than an hour normally. 

You then could create a 50GB win7 NTFS partition with the boot flag for windows to install to. Then add a 100 to 200GB NTFS shared partition for any data you want in both. A extended partition for the rest of the drive for Linux or other installs or more data depending on what you want.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
Okay, I am confused.  I understood what you said but I'm too stupid to do it.  I'll just have my dad get me a dvd.

---

