---
title: "Can't activate compiz on 10.04/ video drivers not found"
date: 2010-04-30
forum: General Help
---

### Post by gueshew on 2010-04-30
Hello all,

I have just upgraded from a fully functional 9.10  to 10.04 which doesn't seem to find the correct intel video drivers when trying to activate compiz extra desktop effects on my laptop...

lspci output is 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)




I tried reinstalling the video drivers using sudo apt-get install xserver-xorg-video-intel    with no luck, telling me I already am using the latest version.

what can I do?

---

### Post by serbforce on 2010-04-30
i have the very same issue, there are no drivers offered in hardware driver section on my geforce 9600gt, no visual effects can be enabled. Please help

---

### Post by dino99 on 2010-04-30
try with nomodeset on the boot line (edit into grub-menu)

try into console:

sudo rm -f /etc/X11/xorg.conf

---

### Post by gueshew on 2010-04-30
> **dino99 said:**
> sudo rm -f /etc/X11/xorg.conf

sudo apt-get install nvidia-current
sudo apt-get install nvidia-current-modaliases
sudo apt-get install nvidia-common

sudo dpkg-reconfigure jockey-gtk

then goto system --> admin --> hardware driver, you might have nvidia-current activated


thanks for your quick response mate, but it doens't seem to work. I followed every step but the system tells me that I already have all the latest nvidia drivers installed and it none of them show in restricted hardware drivers...

would you happen to have any other way to approach this?

---

### Post by gueshew on 2010-04-30
> **gueshew said:**
> thanks for your quick response mate, but it doens't seem to work. I followed every step but the system tells me that I already have all the latest nvidia drivers installed and it none of them show in restricted hardware drivers...

would you happen to have any other way to approach this?


daboss@WhoAmI:~$ sudo rm -f /etc/X11/xorg.conf
daboss@WhoAmI:~$ 
daboss@WhoAmI:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
daboss@WhoAmI:~$ sudo apt-get install nvidia-current-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current-modaliases is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
daboss@WhoAmI:~$ sudo apt-get install nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
daboss@WhoAmI:~$ 
daboss@WhoAmI:~$ sudo dpkg-reconfigure jockey-gtk
daboss@WhoAmI:~$

---

### Post by dino99 on 2010-04-30
have modified my previous post (mixing two different problems, sorry)

maybe some help here

[https://launchpad.net/ubuntu/+ppas?name_filter=intel](https://launchpad.net/ubuntu/+ppas?name_filter=intel)

---

### Post by gueshew on 2010-04-30
> **dino99 said:**
> try with nomodeset on the boot line (edit into grub-menu)

try into console:

sudo rm -f /etc/X11/xorg.conf


ok sry if I sound like a noob in advance, but I tried sudo gedit /boot/grub/menu.lst
and it just opens a blank doc with no options...
should I just add nomodeset to this blank doc?

bear in mind I upgraded from 9.10 and only booting ubuntu on this system

---

### Post by gueshew on 2010-04-30
> **gueshew said:**
> ok sry if I sound like a noob in advance, but I tried sudo gedit /boot/grub/menu.lst
and it just opens a blank doc with no options...
should I just add nomodeset to this blank doc?

bear in mind I upgraded from 9.10 and only booting ubuntu on this system


the file opened with [FONT=monospace]sudo gedit [/FONT]/etc/default/grub

shows shall I just add nomodeset or create a line #kopt=nomodeset?


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

nomodeset
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

---

### Post by gueshew on 2010-04-30
but I just wondered why you would advise to use nvidia drivers on my intel video card?


please help!!!! this is so frustrating

---

### Post by dino99 on 2010-04-30
please read post 6

and modify this line you provided:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

( sudo gedit /etc/default/grub)

if you had previously grub1 (grub-legacy) installed, you have to remove/purge it with synaptic, only grub-pc and grub-common have to be installed now, then run again into console:

sudo grub-mkconfig && update-grub

(dont understand why you've talk about menu.list into your previous post)

---

### Post by gueshew on 2010-04-30
> **dino99 said:**
> please read post 6

and modify this line you provided:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

( sudo gedit /etc/default/grub)

if you had previously grub1 (grub-legacy) installed, you have to remove/purge it with synaptic, only grub-pc and grub-common have to be installed now, then run again into console:

sudo grub-mkconfig && update-grub

(dont understand why you've talk about menu.list into your previous post)


thanks for those pointers Dino, 

so I change grub to

[FONT=monospace]GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
GRUB_CMDLINE_LINUX=""


checked synaptic, no grub-legacy present, only pc and common are there so all good...

the output of [/FONT] sudo grub-mkconfig && update-grub is:


Generating grub.cfg ...
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
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
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=40578b39-6fe1-4b6f-9819-06fcdbdf53a3 ro   nomodeset quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=40578b39-6fe1-4b6f-9819-06fcdbdf53a3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=40578b39-6fe1-4b6f-9819-06fcdbdf53a3 ro   nomodeset quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=40578b39-6fe1-4b6f-9819-06fcdbdf53a3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40578b39-6fe1-4b6f-9819-06fcdbdf53a3
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
done
/usr/sbin/grub-mkconfig: You must run this as root



I restarted the computer but still same issue...  do you happen to have any idea?
I am so grateful you are helping me on this, you are a godsent!

---

### Post by dino99 on 2010-04-30
i've reread the first post to remember the real question and as i'm not used with compiz things, i've only googled around and found:

[http://wiki.compiz.org/Hardware/Intel](http://wiki.compiz.org/Hardware/Intel)

but you might dig out more i suppose: compiz+your chipset, even with other distro (fedora, suse, ...)

---

### Post by gueshew on 2010-04-30
> **dino99 said:**
> i've reread the first post to remember the real question and as i'm not used with compiz things, i've only googled around and found:

[http://wiki.compiz.org/Hardware/Intel](http://wiki.compiz.org/Hardware/Intel)

but you might dig out more i suppose: compiz+your chipset, even with other distro (fedora, suse, ...)

  thank you


do you think I am having those issues from not doing a clean install? should I consider it?

---

### Post by mattwilmott on 2010-04-30
Im having the exact say issue as the OP

Running on a Dell optiplex 745, Intel Graphics 

lscpi | grep VGA gives:

matt@matt-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

Tried reinstalling xserver-xorg-video-intel, reset /etc/X11/xorg.conf, added i915.modset=0 to grub and all manner of things still cant get it working. :(

When I try enabling the compiz effects it has the searching for available video drivers but non are found. I have enabled the video driver restricted repo even though they shouldn't be needed for intel drivers.

Dont know what else to do - if anyone needs more info let me know and I can provide it. 

Any ideas would be appreciated

Thanks

---

### Post by gueshew on 2010-05-01
> **mattwilmott said:**
> Im having the exact say issue as the OP

Running on a Dell optiplex 745, Intel Graphics 

lscpi | grep VGA gives:

matt@matt-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

Tried reinstalling xserver-xorg-video-intel, reset /etc/X11/xorg.conf, added i915.modset=0 to grub and all manner of things still cant get it working. :(

When I try enabling the compiz effects it has the searching for available video drivers but non are found. I have enabled the video driver restricted repo even though they shouldn't be needed for intel drivers.

Dont know what else to do - if anyone needs more info let me know and I can provide it. 

Any ideas would be appreciated

Thanks


FYI I ended up doing a clean install, now everything works great out of the box.... did you do and upgrade or fresh install?

good luck with your troubles.

---

### Post by mattwilmott on 2010-05-01
Yeah upgrade not a fresh install

Was hoping to avoid the reinstall but it may turn out easier

---

### Post by fmedina on 2010-05-03
I can't ge compiz effects going on 10.04 upgrade either.  They were working on Karmic, although I remember it took me a while to get them going too.

I actually get the searching for drivers message and it seems to switch modes, but I don't get borders on windows.

I have a Lenovo X61

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 0c)

Any help, would be appreciated.

thanks,

---

