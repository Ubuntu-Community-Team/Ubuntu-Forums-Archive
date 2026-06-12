---
title: "Karmic - Cannot enable Compiz desktop effects (Intel 945GM)"
date: 2011-06-22
forum: General Help
---

### Post by cwrighta70 on 2011-06-22
Hey all,

I have a Dell Latitude D520 with an Intel 945GM Integrated Graphics Card.  I have been unable to get the desktop effects to work in either Jaunty or Karmic.  When selecting Normal/Extra/Custom, I get an error:

```
Desktop effects could not be enabled
```

Graphics card info:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 942/940GML Express Integrated Graphics Controller (rev 03)
```

Any help on this would be greatly appreciated.  I've looked at countless threads pertaining to this issue, but nothing I could find resolved my issue.

Thanks!
Chris

---

### Post by smurphy_it on 2011-06-22
You should launch from command line so you get specific errors.  Additionally, I believe you "might" require 3D rendering to be enabled on your video card.  Confirm like so (in a terminal window):

```
glxinfo | grep [Dd]irect
```

Also, you'll want these packages installed as a minimum:

```
sudo apt-get install compizconfig-settings-manager emerald
```

---

### Post by cwrighta70 on 2011-06-22
Thanks for the quick reply, smurphy.  Here is the result of the first command - glxinfo | grep [Dd]irect

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by cwrighta70 on 2011-06-22
Bumping this to hopefully get some help!

Thanks,
Chris

---

### Post by smurphy_it on 2011-06-23
Do you have the intel video installed ?

```
dpkg --get-selections | grep intel
```


You should see something similar to:

xserver-xorg-video-intel			install

If it's not there, you should install it.
```
sudo apt-cache search video
```

Presents the following information:

xserver-xorg-video-intel-dbg - X.Org X server -- Intel i8xx, i9xx display driver (debug symbols)
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver

So this would be the right driver according to your lspci output.  Hence, if it isn't already installed, you should install it.

```
sudo apt-get install xserver-xorg-video-intel
```

Then after it's installed, run the "glxinfo | grep [Dd]irect command.  If you have rendering you would get output such as:


direct rendering: Yes

---

### Post by cwrighta70 on 2011-06-23
smurphy, it looks as though I do have the intel video installed.  Running your first command (dpkg --get-selections | grep intel) outputs the following:

```
libdrm-intel1					install
xserver-xorg-video-intel			install

```

---

### Post by cwrighta70 on 2011-06-23
Also, I just ran the Compiz Check script, which gave the following output:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

---

### Post by cwrighta70 on 2011-06-23
Okay, fixed it!

Found a post with the following instructions:

> OK, found the solution.

The problem was with a previous install of nvidia drivers that was removed.
Although I am using the intel driver, the GLX extension from Nvidia was being picked up. This is because the alternatives tool is still linked to nvidia for glx lib.
Fixed it with following commands -

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

After I ran those commands, I had one final error which was "The Composite extension is not available."  So I edited the xorg.conf file - 

```
sudo gedit /etc/X11/xorg.conf
```

 - and found that - 

```
Section "Extensions"
	Option "Composite" "Disabled"
EndSection

```

 - Composite was disabled.  I simply changed "Disabled" to "1", and that fixed it.

Thanks,
Chris

---

