---
title: "kernel update just killed fglrx"
date: 2010-07-24
forum: General Help
---

### Post by hawthornso23 on 2010-07-24
A kernel update just killed my ATI graphics driver. 

Trying to install proprietary graphics driver fails and points at /var/log/jockey.log

This ends with

```

2010-07-24 23:06:18,027 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:06:18,265 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:06:18,497 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:06:28,131 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:06:40,210 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
2010-07-24 23:06:40,210 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-07-24 23:06:40,210 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-07-24 23:07:26,807 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:07:26,977 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:20,233 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:20,391 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:20,598 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:20,771 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:20,982 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:21,135 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-07-24 23:08:22,341 DEBUG: Shutting down
```And yes indeed there is no /sys/modules/fglrx

If I can't sort this out I'll have to try rebooting into the old kernel to get the graphics driver back. The dreadfully slow scrolling in the browser is starting to drive me insane. 

Open to suggestions.

---

### Post by hawthornso23 on 2010-07-24
OK - fixed it.

Opened synaptic and searched for fglrx. Reinstalled everything already installed which showed up in this search.

fglrx
fglrx-amdccle
fglrx-modaliases
jockey-gtk
jockey-common
xserver-xorg-video-radeon

After that hardware drivers showed the proprietary driver as installed but not active. Rebooting finished the job. Suggest the next person to have this problem tries reinstalling these things one by one instead of all at once so that we can figure out which one did the trick.

---

### Post by darinlh on 2010-08-21
Just tried one at a time.
1. X.Org X server -- AMD/ATI Radeon display driver = no go
2. fglrx (Video driver for the ATI graphics accelerators) now states driver install but not active.

Rebooting now = crossing fingers

---

### Post by darinlh on 2010-08-21
It did reinstall missing pieces BUT

After rebooting I found compiz was not working, I also tried catalyst control center which failed.

ran "sudo aticonfig --initial --input=/etc/X11/xorg.conf"

now appears to be running fine.

Interesting note
On a Asus 1201T AMD netbook with an ATI on board card this update did not affect it.

The PC it did affect was AMD with a HD4770

Both running Ubuntu 10.4 ??

---

### Post by gabsik on 2011-09-13
i have 

<code>Linux bt 2.6.39.4 #1 SMP Thu Aug 18 13:38:02 NZST 2011 i686 GNU/Linux<!code>

why this ?
<code>
:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
</code>

how could i not have xorg.conf ??? o_O

---

### Post by gabsik on 2011-09-13
I have this in my /etc/X11/:

```

app-defaults/            fonts/                   X                        Xreset                   Xsession                 Xwrapper.config          
cursors/                 fvwm/                    xinit/                   Xreset.d/                Xsession.d/              
default-display-manager  rgb.txt                  xkb/                     Xresources/              Xsession.options

```

---

