---
title: "xfix in recovery doesn't let me choose driver"
date: 2010-01-22
forum: General Help
---

### Post by amsterdamharu on 2010-01-22
The first time I ran Hardy ubuntu I didn't know what card I had so choose vesa to be on the save side. Now I when booting in recovery and choosing xfix it does not give me a choice anymore to choose what card I have, it automatically chooses something.

Using Intel Mobile 945gme it had 3d effects in Fedora but now it won't work.

This is my xorg.conf
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```Is there a tool other than gedit that will let me choose my videocard from a list? In system -> administration -> hardware drivers there is nothing to choose.

---

### Post by adam814 on 2010-01-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I believe that should "auto-detect" the driver for you and take care of it.

---

### Post by amsterdamharu on 2010-01-22
Thank you for you quick reply, that gives me the same as xfix. No choice for a videocard and xorg.conf stays unchanged. Desktop effects/compiz and Avant not working and not able to go into a higher resolution.

Funny thing is that the first time I ran xfix there was a choice for videocards. Now it automatically chooses something.

I am thinking of just leaving it since I've spent too much time on it allready and the effects aren't that importaint. This is a mini laptop though and the height of the screen cannot fit many windows (ok button doesn't show) which is irritating.

---

### Post by adam814 on 2010-01-22
Hmm...try moving your xorg.conf somewhere else and see what X comes up with in the absence of a config file.  I've seen that work before.

You could always use X -configure from the command line, but it's a pain and I think you have to specify refresh rates and modelines manually.

---

### Post by amsterdamharu on 2010-01-22
I stopped gdm, removed all the xorg.conf files in /etc/X11 and rebooted (init 1) the xfix came up with the same automatically configured xorg.conf.

Will try x-configure later, I don't think the resolution can be set higher anyway because in windows it only goes as high as 1024 by 600 and it has the intel 945 driver installed.

It seems that even if the correct driver is used it will only activate desktop effects and that is not too important for me.

Thank you all for your help and if I will ever fix this I will let you know.

---

### Post by amsterdamharu on 2010-01-23
Used tty1 to log in as root and issued the following commands:

```

mv /etc/X11/xorg.* /tmp
/etc/init.d/gdm stop
X -configure

```

Got some Intel stuff in my xorg.conf now but no 3d/desktop effects, when starting conpiz from console I get:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

```

---

### Post by adam814 on 2010-01-23
Make sure you have "libgl1-mesa-glx" installed.  I think it's needed for Compiz effects.

---

### Post by amsterdamharu on 2010-01-23
Thank you Adam for your reply, it is installed and the latest version (for Hardy).

I even tried to install the latest driver from Intel but can't compile it because my xorg-server is not of version 1.6 or higher.

This is taking me much more time than I planned and will now try to use the computer for what I intended it to; browsing, chatting, watching video. That all works so to hell with the 3d effects. 

The low res is due to my monitor being too small and I think installing the (newer) drivers will not fix that anyway.

Thanks again for all the help and if this ever is fixed I'll post the solution.

---

