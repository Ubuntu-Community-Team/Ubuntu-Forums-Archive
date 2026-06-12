---
title: "Help! undo bad command... ln -f -s"
date: 2009-10-20
forum: General Help
---

### Post by AlphaLexman on 2009-10-20
I was trying to fix my xorg and nvidia problems when I accidentally typed my symbolic link in backwards. Ugh!

Files I HAD in /usr/lib/xorg/modules/extensions/

> libglx.so.190.36
libglx.so.173.14.20
libglx.soI tried an upgrade of nvidia drivers from 173... to 190(beta), well X crashed and I was trying to rollback to 173...

I noticed libglx.so was a symbolic link to libglx.so.190.36.  So I thought just change the symbolic link back to libglx.so.173.14.20, reboot and I'll be good. But,
Here's what I did: (backwards from what I wanted, Ugh.)

```
sudo ls -f -s libglx.so libglx.so.173.14.20
```Now,

> libglx.so.173.14.20 -> libglx.so
libglx.so -> libglx.so.190.36Then in my haste, I sudo rm'd all 3 files, the two links and the 190 driver.  Can I recover the libglx.so.173.14.20 file and how? :confused:

The video card is a nvidia GeForce FX 5500 (old) and this box is not my production machine (I was just trying some new things)

---

### Post by sisco311 on 2009-10-20
try to reinstall the driver:
```
sudo apt-get install --reinstall nvidia-glx-173
```

---

### Post by AlphaLexman on 2009-10-20
I thought of that, but I can't get online without the X server and networkmanager.

---

### Post by sisco311 on 2009-10-20
> **AlphaLexman said:**
> I thought of that, but I can't get online without the X server and networkmanager.

If you didn't clear the cache the package should be still in /var/cache/apt/archives:
```
sudo dpkg -i /var/cache/apt/archives/nvidia-glx-173*.deb
```

---

### Post by AlphaLexman on 2009-10-20
It wasn't there, just the nvidia-glx-190... deb

Edit: Although I do have nvidia-173-modaliases*.deb

---

### Post by sisco311 on 2009-10-20
Did you try to select *xfix  Try to fix X server* from the Reovery Mode menu?

Also try to edit the xorg.conf file:
```
nano /etc/X11/xorg.conf
```
and replace *Driver "nvidia"* with *Driver "nv"*
save the file and exit(Ctrl+x, y, Enter)
```
exit
```
select *boot  Resume normal boot*.

You should be able to boot in xfce.

Reinstall the nvidia driver.

---

### Post by AlphaLexman on 2009-10-20
I did try xfix from the recovery menu.  That was my first attempt before sudo'ing where I shouldn't be. :( 

Here is my /etc/X11/xorg.conf

```
Section "Device"
     Identifier     "Configured Video Device"
EndSection

Section "Monitor"
     Identifier     "Configured Monitor"
EndSection

Section "Screen"
     Identifier     "Default Screen"
     Monitor        "Configured Monitor"
     Device         "Configured Video Device"
EndSection

```

---

### Post by sisco311 on 2009-10-20
Add the driver line to the *Device* section:
```
Section "Device"
   Identifier     "Configured Video Device"
   **Driver         "nv"**
EndSection

Section "Monitor"
     Identifier     "Configured Monitor"
EndSection

Section "Screen"
     Identifier     "Default Screen"
     Monitor        "Configured Monitor"
     Device         "Configured Video Device"
EndSection
```

---

### Post by AlphaLexman on 2009-10-20
Added "nv" to the xorg.conf
I got a graphical login screen and tried normal, failsafe login and xfix again.
I still see nvidia 190 go by on the screen during startup.

Is there somewhere I can get the nvidia-glx-173*.deb file you referred to in your second post, and install it from a floppy or USB?

I'll take a look at [http://packages.ubuntu.com](http://packages.ubuntu.com)

BTW, Thank you for your time and help

---

### Post by AlphaLexman on 2009-10-20
Solved.

Got the .deb and a usb along with the dpkg -i

---

