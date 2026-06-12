---
title: "Help resolution change (xorg)"
date: 2011-08-12
forum: General Help
---

### Post by tarun86 on 2011-08-12
Hey Everyone

I have a msi wind notebook. I have installed Natty with xfce environment. All is well expect for the resolution which is showing only 800x600. I have tried to find xorg.conf but its not there in /etc/X11/xorg.conf ?

Its been an year since I used ubuntu and I dont know what has changed but I believe xorg.conf should have been there ? 

Anyways here is my lspci details. Please help me out with this thing. 

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Ralink corp. RT2860


Cheers

---

### Post by Carborundum on 2011-08-12
What happens if you try runnning these commands in order (one at a time)?

```
xrandr -s 0
xrandr -s 1
xrandr -s 2
```

---

### Post by Grenage on 2011-08-12
> **tarun86 said:**
> Hey Everyone

I have a msi wind notebook. I have installed Natty with xfce environment. All is well expect for the resolution which is showing only 800x600. I have tried to find xorg.conf but its not there in /etc/X11/xorg.conf ?

Its been an year since I used ubuntu and I dont know what has changed but I believe xorg.conf should have been there ? 

Anyways here is my lspci details. Please help me out with this thing. 



Cheers

Ideally, use xrandr; there's a good guide [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html").

If you want to use xorg.conf (I usually do), then there's a guide [here]("http://www.grenage.com/xorg.html").

Post back if you get stuck!

---

### Post by tarun86 on 2011-08-12
> **Carborundum said:**
> What happens if you try runnning these commands in order (one at a time)?

```
xrandr -s 0
xrandr -s 1
xrandr -s 2
```

xrandr -s 0 
**nothing happens**

xrandr -s 1
**Size index 1 is too large, there are only 1 sizes**

xrandr -s 2
**Size index 2 is too large, there are only 1 sizes**

what does this tell us ?

---

### Post by realzippy on 2011-08-12
run
```
xrandr -q
```
and post the output

---

### Post by tarun86 on 2011-08-12
> **Grenage said:**
> Ideally, use xrandr; there's a good guide [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html").

**This part adds a new entry(  1024x768  ) but doesn't change the resolution. Hence I tried my hands on the below too** 

> 
If you want to use xorg.conf (I usually do), then there's a guide [here]("http://www.grenage.com/xorg.html").

Post back if you get stuck!


Here the Xorg.conf I tried & X wont start up using this.

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection

EndSection


Few other outputs as well

> xmonkee@xmonkee-U-100:~$ **lspci |grep VGA**
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)


> xmonkee@xmonkee-U-100:~$ **sudo ddcprobe** 
vbe: VESA 3.0 detected.
oem: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r) 82945GM Chipset Family Graphics Controller Hardware Version 0.0
memory: 7872kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
xmonkee@xmonkee-U-100:~$ 

> xmonkee@xmonkee-U-100:~$ **xrandr -q**
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        57.0* 



This is horrible stuck with awful ratio of 800x600 even though its a notebook.

---

### Post by realzippy on 2011-08-12
1024x600 is your desired resolution ?
Can you post/attach Xorg.0.log file?

---

### Post by Grenage on 2011-08-12
Well you're missing key bits of information, so the xorg.conf is probably having issues.  Try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "MSI"
	ModelName "Wind"
	HorizSync 30 - 81
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 945GME"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

If that doesn't work, try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "MSI"
	ModelName "Wind"
	HorizSync 30 - 81
	VertRefresh 56 - 75
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 945GME"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

The EDID fail is the reason, it's not working (Ubuntu can't tell what the screen supports).  God only knows why there still isn't a force option in the GUI.

---

### Post by realzippy on 2011-08-12
@grenage
sure about *Modes "1024x768"/modeline* ?
(Op did not confirm,but msi wind usually has 1024x600 native.)

---

### Post by Grenage on 2011-08-12
> **realzippy said:**
> @grenage
sure about *Modes "1024x768"/modeline* ?
(Op did not confirm,but msi wind usually has 1024x600 native.)

Hi, realzippy.

I was only going by the OP's xorg attempt, but if that's not the recommended resolution for the netbook (I've not used one), then it certainly shouldn't be used.

OP:

Going by realzippy's information, you could try this alternative:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "MSI"
	ModelName "Wind"
	HorizSync 30 - 81
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 945GME"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x600"
	EndSubSection
EndSection
```

If that doesn't work, try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "MSI"
	ModelName "Wind"
	HorizSync 30 - 81
	VertRefresh 56 - 75
Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 945GME"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x600"
	EndSubSection
EndSection
```

---

### Post by realzippy on 2011-08-12
Another question would be why OP seems to use vesa and not intel.
Some modeset manually added?
Xorg.0.log might give a hint...

---

### Post by tarun86 on 2011-08-12
Thank you both for the efforts man. But this does seem to work.  Tried both xorg.conf for 1024x600. Even tried 1024x600 using xrandr but dint work.

I used this script too to get resolve the resolution for the  bootscreen but I hope this is not the one that messed it up. Earlier I had good resolution but from here(below script) on and playing with plymouth-manager messed it up

> #!/bin/bash
# ----------------------------------
# Author: D0rkye
# Homepage: [http://d0rkye.zsenialis.com/](http://d0rkye.zsenialis.com/)
# Most code probably by kyleabaker: [http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)
#
# Fix for Ubuntu 11.04, for BURG, and some extra bloat by Paolo Bernardi ([http://paolobernardi.wordpress.com/](http://paolobernardi.wordpress.com/))
# ----------------------------------

# Usage: install_if_not_installed package_name
function install_if_not_installed
{
	PACKAGE="$1"
	INSTALLED=$(dpkg -L "$PACKAGE" > /dev/null 2>&1 && echo OK || echo KO)
	if [ "$INSTALLED" == "KO" ]
	then
		sudo apt-get install "$PACKAGE" -y
	fi
}

# Usage: contains regexp file
function contains
{
	REGEXP="$1"
	FILE="$2"

	grep "$REGEXP" "$FILE" > /dev/null && echo OK || echo KO
}

install_if_not_installed v86d
install_if_not_installed hwinfo

sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/burg > ./newburg
sudo cp -f ./newburg /etc/default/burg
rm ./newburg

sed 's/\#GRUB\_GFXMODE\=640x480/GRUB\_GFXMODE\='$resolution'/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

if [ "$(contains uvesafb /etc/initramfs-tools/modules)" == 'KO' ]
then
	sudo echo "uvesafb mode_option=$resolution mtrr=3 scroll=ywrap" | sudo tee -a /etc/initramfs-tools/modules
fi

if [ "$(contains FRAMEBUFFER=y /etc/initramfs-tools/conf.d/splash)" == 'KO' ]
then
	echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
fi

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\(.*\)vt\.handoff\=7\(.*\)\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\1\2\"/g' /etc/grub.d/10_linux > ./new10linux
sudo cp -f ./new10linux /etc/grub.d/10_linux
rm ./new10linux
sudo chmod +x /etc/grub.d/10_linux

sudo update-grub2
which update-burg > /dev/null 2>&1 && sudo update-burg
sudo update-initramfs -u
echo "The resolution should be fixed after a reboot"



I am also attaching the Xorg.0.log tar file with this post. Let me just give it a last try before it settle down for life of 800x600 resolution

---

### Post by realzippy on 2011-08-12
```
sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution
```

what did you edit here when GUI asked?

Have you edited some *modeset* somewhere?

---

### Post by realzippy on 2011-08-12
[I]Earlier I had good resolution but from here(below script) on and playing with plymouth-manager messed it up
[/I]
Not knowing what "playing" exactly means ,it might be hard to undo something.

```
[    21.082] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, [COLOR="Lime"]945GME[/COLOR], Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    21.087] (II) VESA: driver for VESA chipsets: vesa
[    21.087] (II) FBDEV: driver for framebuffer: fbdev
[    21.087] (++) using VT number 7

[    21.094] (II) [COLOR="Red"]Loading[/COLOR] /usr/lib/xorg/modules/drivers/[COLOR="Red"][COLOR="Red"]vesa_drv.so[/COLOR]

```

So for some reason kernel chooses the vesa driver instead of intel.

---

### Post by tarun86 on 2011-08-12
By playing I mean I installed couple of themes & tried to set them as splash screens using plymouth-manager. Since these new splash screens werent running &  I could only see a black screen. Then I came across the above mentioned script "fixplymouth-natty" & executed it w/o paying too much attention to it because all it was doing was installing couple of things. It is when I executed this script, things went upside down

> **realzippy said:**
> ```
sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution
```

what did you edit here when GUI asked?

Have you edited some *modeset* somewhere?

I entered **1024x768-24**. And it installed hwinfo & v86d. Than reboot to check the boot screen - it came all black but some how came to gdm but my resolution was f*cked. once that, 

I tried xrandr to set new resolution.  It dint work. 

Tried installing ubuntu-desktop to see if it has better resolution, it dint. 

removed xubuntu & all its apps to solve the issue. It dint work either

Removed ubuntu-desktop completely & reinstalled xubuntu using apt. Dint work

That is when I decided to ask for help

Dont know about modeset is, but before me fiddling with plymouth-manager & later executing this script, everything was going fine. I just had to ruin it.

---

### Post by realzippy on 2011-08-12
please show what script has done to:
/etc/default/grub
```
gedit /etc/default/grub
```

---

### Post by tarun86 on 2011-08-12
I ran the above script again with 800x600-24 option with the hope that this will solve the issue. So here's the script as of now.


> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset video=uvesafb:mode_option=800x600-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by realzippy on 2011-08-12
Run
```
gksudo gedit /etc/default/grub
```

change 
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset video=uvesafb:mode_option=800x600-24,mtrr=3,scroll=ywrap"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then run

```
sudo update-grub
```

Reboot..

---

### Post by tarun86 on 2011-08-12
Done that man, but the resolution is still an issue. How do I remove vesa or force kernel choose "intel" ? just give me few pointers as of what to do briefly. Dont want to waste your time. 

And I really really appreciate your help man. I have tried everything in my knowledge of linux to sort it by myself before I turned to your help.

---

### Post by realzippy on 2011-08-12
what does
```
gedit /etc/initramfs-tools/modules
```
show?

---

### Post by tarun86 on 2011-08-12
> # List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap

There you go. Look like some problem here.

---

### Post by realzippy on 2011-08-12
```
gksudo gedit /etc/default/grub
```
change 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash i915.modeset=1&#8243;

then

```
gksudo gedit /etc/initramfs-tools/modules

```
delete last line:
uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap
 
then

```
sudo update-initramfs -u
```
```
sudo update-grub
```
reboot fingers crossed.

---

### Post by tarun86 on 2011-08-12
dude I cant tell you how grateful do I feel now. It worked awesomely. Just one last bother : what did I do wrong ? 

Thanks a lot for your patience & time man, really really appreciated.

---

### Post by realzippy on 2011-08-12
Guess the script did something wrong...be careful when using such stuff from the net.

btw,
when using the script you had to use 1024x600-16    ;-) 
,now knowing how to undo changes script does to your system,you might
try again...*but* I am out (nearly midnight)....have fun!

---

### Post by tarun86 on 2011-08-12
I will man cheers :)

---

### Post by realzippy on 2011-08-13
...can you mark thread as solved (Threadtools)?
Thanks..

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

