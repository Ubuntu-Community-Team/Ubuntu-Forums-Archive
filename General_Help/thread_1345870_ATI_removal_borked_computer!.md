---
title: "ATI removal borked computer!"
date: 2009-12-04
forum: General Help
---

### Post by Docaltmed on 2009-12-04
I'm running Ubuntu 9.10, a clean install. I had briefly installed the fglrx driver, but didn't like it so went back to radeon, using the Hardware Manager. 

I then tried to remove the ATI driver as per the installation instructions. 

In Terminal, I went to /usr/share/ati

Then I ran the following command as root:

```
sh ./fglrx-uninstall.sh
```

Rebooting the computer, it just hangs up. I can boot it off of a Live USB, but that's it. Without the USB, I can't even get to GRUB.

I'm sure there's a fairly straightforward fix for this. I'm equally sure that I don't know what it is. Any help would be appreciated, as this is actually my office computer, and I'm rather useless without it.

---

### Post by ajgreeny on 2009-12-04
Rename the **/etc/X11/xorg.conf** file, if there is one and try again to restart x.  It may be that the xorg.conf file is not changed back to the ati/radeon open source driver after removing fglrx.

By default karmic has no xorg.conf file, so if that solves the problem, there is no need to worry about making a new file to replace the original.

---

### Post by Docaltmed on 2009-12-04
Well, got to the GRUB menu (hold SHIFT down with GRUB2). Tried:

```
dpkg-reconfigure -phigh xserver-xorg
```

and rebooted, same problem.

so I dropped back into recovery mode, typed:

```
nano /etc/X11/xorg.conf
```

and the file doesn't exist.

So it's a Karmic thing. Where do I go from here?

---

### Post by Docaltmed on 2009-12-04
OK. Found a file in the /etc/X11/ folder named "xorg.conf.failsafe."

I used nano to save a copy of that file as xorg.conf.

I booted up, and I got Gnome back! 

Resolution is messed up, though. Next step is to re-install the radeon drivers without borking the system again.

---

### Post by Docaltmed on 2009-12-04
Getting closer.

If I change the driver in the generic xorg.conf file from "vesa" to "ati" it recreates the initial problem. 

Changing back to "vesa" got me low-res Gnome again.

So, next step: how do I re-install the missing open source driver?

---

### Post by sdowney717 on 2009-12-04
if your running free driver you should not need xorg.conf 
see if the radeon driver is installed from synaptic

---

### Post by Docaltmed on 2009-12-04
> **sdowney717 said:**
> if your running free driver you should not need xorg.conf 
see if the radeon driver is installed from synaptic

Wow, what a pain! I finally pulled fglrx out by the roots and reinstalled radeon by following the instructions on this wiki page:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I had to modify xorg.conf to refer to "ati" again, and I'm back up to speed.

sdowney717: Yeah, this whole xorg.conf thing has me baffled. It seems that if it is there, Karmic will use it. I would prefer not to have an xorg.conf file if I don't need it, so my next step will be figuring out how to safely remove it.

But I actually have some work to do today, and I've already spent 3 hours of my life that I'll never get back on this thing, so that can be tomorrow's problem!

Thanks, everybody, for your suggestions!

---

