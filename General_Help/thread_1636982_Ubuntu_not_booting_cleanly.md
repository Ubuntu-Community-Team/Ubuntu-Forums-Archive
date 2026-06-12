---
title: "Ubuntu not booting cleanly"
date: 2010-12-03
forum: General Help
---

### Post by megahost on 2010-12-03
After I had upgraded from Ubuntu 10.04 to 10.10, I have issues with Ubuntu booting cleanly. First, I have UI errors where screen colors will act like a prism on top and on bottom of my screen. Then things load, but they are immensely misplaced. While worrying about this clean load, I also am worried about the prompt on boot. I now get a prompt basically saying that it found the drive to boot ubuntu from, and it takes 10 seconds to do so. So after I have that, I don't have a nicely designed boot screen like i did in 10.04. Instead, I have a purple background with white text saying "ubuntu." 
Any advice on how to fix these problems would be appreciated. 
Thanks, MegaHost

---

### Post by drs305 on 2010-12-03
You aren't seeing the Grub menu most likely because you have (or Grub2 thinks you have) only one OS. If this is the cause, you can fix it by editing /etc/default/grub as root and changing one line:

Open for editing:
```
gksu gedit /etc/default/grub
```

Make sure GRUB_TIMEOUT has a positive value and add a comment to this line:
> **[COLOR="DarkRed"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0
Save the file, then update Grub:
```
sudo update-grub
```
Hopefully your menu will appear on the next boot.

The multicolors may be your video card driver (or lack thereof). You can try a 'safe graphics' boot from the recovery mode, or try to add a video driver after booting via System, Administration, Additional Drivers.

If you can't see the desktop at all, and still don't have the Grub menu display, hold down the SHIFT key early in the boot. The menu should display. Press "e" to edit the menu entry and see if adding "nomodeset" after "quiet splash" in the linux line helps. After typing nomodeset, CTRL-x to boot. That entry will not be present the next time you boot (it isn't persistent). Try adding a driver after the boot.

---

### Post by Frogs Hair on 2010-12-03
Hardware and driver information may helpful for solving your problem . there are some fixes for the splash screen available if you are using proprietary drivers for your graphics card.

---

### Post by megahost on 2010-12-03
I have an NVIDIA accelerated graphics driver.

---

### Post by megahost on 2010-12-03
> **drs305 said:**
> You aren't seeing the Grub menu most likely because you have (or Grub2 thinks you have) only one OS. If this is the cause, you can fix it by editing /etc/default/grub as root and changing one line:

Open for editing:
```
gksu gedit /etc/default/grub
```

Make sure GRUB_TIMEOUT has a positive value and add a comment to this line:

Save the file, then update Grub:
```
sudo update-grub
```
Hopefully your menu will appear on the next boot.

The multicolors may be your video card driver (or lack thereof). You can try a 'safe graphics' boot from the recovery mode, or try to add a video driver after booting via System, Administration, Additional Drivers.

If you can't see the desktop at all, and still don't have the Grub menu display, hold down the SHIFT key early in the boot. The menu should display. Press "e" to edit the menu entry and see if adding "nomodeset" after "quiet splash" in the linux line helps. After typing nomodeset, CTRL-x to boot. That entry will not be present the next time you boot (it isn't persistent). Try adding a driver after the boot.
 I checked my Grub and here's what I get 
> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


---

### Post by Frogs Hair on 2010-12-03
This is use at your own risk. [http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)

---

### Post by drs305 on 2010-12-03
> **megahost said:**
> I checked my Grub and here's what I get

This is how you want to make it look. Add the # symbol at the start of the line. Edit /etc/default/grub as I indicated in my previous post.


> GRUB_DEFAULT=0
**[COLOR="Red"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="" 
Save the file, then run:
```
sudo update-grub
```

The "nomodeset" option often helps until nvidia drivers are installed. If you can get to editing the grub menu, make the linux line ending look like this (how to get there explained previously):
> linux	/boot/vmlinuz-<some-number> root=UUID=<some-number> ro   quiet splash [COLOR="Red"]nomodeset[/COLOR]

---

