---
title: "Unable to boot Ubuntu following installation of ATI drivers"
date: 2009-07-23
forum: General Help
---

### Post by robocombot on 2009-07-23
Hello!

Please help I may have to reinstall Ubuntu!

Quick version: How do I boot Ubuntu using the default video driver?

Long version: I had a working copy of Ubuntu Jaunty running - however I tried to install drivers for my ATI Radeon Xpress 1150 video card.

Searching the repository (all available programs) for "ATI Driver" gave me  ATI Radeon X - or something similiar.... Installed this with no issues and rebooted.

No whenever I boot Ubuntu from Grub it shows the Ubuntu progress bar but before it gets to the Login screen the I get an image that can only be described as the what random horizontal lines of colour (you can actually make our the Windows XP shutdown screen in there if I have just shut down XP before). This screen then flickers as it changes resolution a few times (zooms into top left corner) before giving up and just showing the same screen at smallest resolution....

Booting in safemode (any of the options) results in the same. 

Thanks for any responses.

James

System specs:
Dell Inspiron 1501 Laptop
Ubuntu Jaunty dual booting with Windows XP SP2
Mobile AMD Athlon 64 CPU

---

### Post by druhboruch on 2009-07-23
Look for /etc/X11/xorg.conf.

There is probably a backup of the original xorg.conf file in this folder.
If there is no backup, then look for device section

```
Section "Device"
    Identifier     "Device0"
    Driver         "ati"
    VendorName     "ATI"
EndSection
```

Comment out driver line.

---

### Post by robocombot on 2009-07-24
Thanks,

Ill try and mount the hard drive via the Live CD as I cannot access that partition from Windows XP.

---

### Post by realzippy on 2009-07-24
Did you try:

CTRL+ALT+F2

before it comes to that "random horizontal lines of colour" ?

If you can access to the terminal you could try:

sudo apt-get purge fglrx

or:

sudo apt-get purge radeon

depending on which driver you have installed.Default video driver is used
then.

---

### Post by brwheeler on 2009-07-25
I am having the same problem.  Tried to update the ATI drivers by creating the Ubuntu/Jaunty .deb packages from the .run file.  Installed packages, rebooted and now the desktop screen is just a mess of color.  I tried both above suggested options and they didn't work... trying to purge fglrx resukted in "Couldn't find package", and the xorg file just lists "configured video device" in the "Device" section.

Any other suggestions would be much appreciated
Thanks!

---

### Post by MarkTX on 2009-07-26
Same problem here! couldn't find package, colored lines, everything.

All i did was try and fix the poor graphics by 'reinstalling' the drivers through synaptic.


I need the laptop working today and i don't want to reinstall everything again!

---

### Post by jocko on 2009-07-26
> **robocombot said:**
> 
Quick version: How do I boot Ubuntu using the default video driver?

Long version: I had a working copy of Ubuntu Jaunty running - however I tried to install [COLOR=Red]drivers for my ATI Radeon Xpress 1150 video card.[/COLOR]

Which driver did you try to install? Ati's proprietary driver (fglrx) does not support your card (they dropped support for everything older than radeon hd2000 a few months ago).
The open source driver (ati or radeon) which probably was what you had working before you messed up, is the only driver that supports your card.
You need to:
1. Reboot into recovery mode. Press Esc when grub loads to see the boot menu (if you don't see it automatically), pick one of the boot lines that ends with "(Recovery mode)". Once the recovery mode is fully loaded you will get a menu where you can choose what you want to do. Select the "root terminal" option.
2. Remove any trace of fglrx:
```
apt-get purge xorg-driver-fglrx
```
3. Reset any changes you have done to the xorg configuration:
```
dpkg-reconfigure --phigh xserver-xorg
```

---

