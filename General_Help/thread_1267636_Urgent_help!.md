---
title: "Urgent help!"
date: 2009-09-16
forum: General Help
---

### Post by HardcoreSSG on 2009-09-16
I'm having serious graphical errors. For example if I run Alien Arena - it has a serious graphic error and crashes my computer. :( Here's an example of me "running" Google Earth. 

[IMG]http://i238.photobucket.com/albums/ff267/couzinitt/Screenshot-1.png[/IMG]Any idea on how to fix this?

---

### Post by QIII on 2009-09-16
Machine specs and version of Ubuntu?

32/64 bit?

---

### Post by HardcoreSSG on 2009-09-16
Intel Pentium III Processor 
933 MHZ

128 Memory (Computer is kinda old)

60.0 GB Hard Drive

Ubuntu 9.04 - Jaunty Jackalope

---

### Post by QIII on 2009-09-16
Do you have any idea what graphics chipset you are using?

---

### Post by HardcoreSSG on 2009-09-16
I'm pretty sure it's a NVIDIA chip.

The computer was given to me so I'm not completely sure. :confused:

---

### Post by QIII on 2009-09-16
Type the following in the terminal and post the results:

```
lspci -m
```

(That's a small Lima, not a 1)

We should be able to figure out the exact graphics.

I suspect you have two problems:  an OLD graphics chipset and not much memory left out of the little you are starting out with after a lot of it is reserved by other hardware.

---

### Post by HardcoreSSG on 2009-09-16
00:00.0 "Host bridge" "Intel Corporation" "82810E DC-133 (GMCH) Graphics Memory Controller Hub" -r03 "" ""
00:01.0 "VGA compatible controller" "Intel Corporation" "82810E DC-133 (CGC) Chipset Graphics Controller" -r03 "Compaq Computer Corporation" "Device b165"
00:1e.0 "PCI bridge" "Intel Corporation" "82801AA PCI Bridge" -r02 "" ""
00:1f.0 "ISA bridge" "Intel Corporation" "82801AA ISA Bridge (LPC)" -r02 "" ""
00:1f.1 "IDE interface" "Intel Corporation" "82801AA IDE Controller" -r02 -p80 "Intel Corporation" "82801AA IDE Controller"
00:1f.2 "USB Controller" "Intel Corporation" "82801AA USB Controller" -r02 "Intel Corporation" "82801AA USB Controller"
00:1f.3 "SMBus" "Intel Corporation" "82801AA SMBus Controller" -r02 "Intel Corporation" "82801AA SMBus Controller"
01:05.0 "Multimedia audio controller" "ESS Technology" "ES1988 Allegro-1" -r12 "Compaq Computer Corporation" "Device b19d"
01:09.0 "Ethernet controller" "National Semiconductor Corporation" "DP83815 (MacPhyter) Ethernet Controller" "Netgear" "Device f311"
01:0a.0 "Network controller" "Broadcom Corporation" "BCM4303 802.11b Wireless LAN Controller" -r02 "Linksys" "Device 4301"

---

### Post by QIII on 2009-09-16
OK.  A couple of things.

You have an Intel graphics chipset.  There are known regressions in Jaunty with regard to Intel chipsets.

Please read this:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

and look for the section about Intel regressions.  There are a couple of ideas there.

It looks like you are running Gnome or KDE with a custom theme, but I can't really tell with the way the window is messed up.  That is probably killing your performance all around and adding to your grief.

I would recommend dumping the theme and using XFCE or LXDE as your desktop environment.

---

### Post by HardcoreSSG on 2009-09-16
That would be the Ubuntu Studio theme. I will change it all and see what happens.

---

### Post by QIII on 2009-09-16
> **HardcoreSSG said:**
> That would be the Ubuntu Studio theme. I will change it all and see what happens.

OK.  The "theme" or the desktop environment?

With your specs you need to go as light as you can go on the UI.

Gnome and KDE are probably too heavy.  Don't use Compiz or any enhanced desktop effects.

---

### Post by HardcoreSSG on 2009-09-16
The theme is ubuntu studio. The enviorment is just an image of a beach- completely custom. Changed the theme to Wind and the enviorment to none. 

Followed the intel error instructions 

Section "Device"
    Identifier    "Configured Video Device"
        "MigrationHeuristic" "greedy"

No luck:(:confused:

---

### Post by QIII on 2009-09-16
Theme is Studio.  Check.

The "environment" is not the desktop wallpaper.

Are you using Ubuntu or Kubuntu?

---

### Post by HardcoreSSG on 2009-09-16
Ubuntu

How do you change the Enviorment?

I disabled Compiz - and desktop effects is none. 
still nothing.

---

### Post by HardcoreSSG on 2009-09-16
My bad the theme is now ClearLooks was Studio.

---

### Post by QIII on 2009-09-16
Edit:  Sorry, lost this bit somehow, I guess:  GNOME and KDE are (this is a simplification) Graphical User Interfaces used by Ubuntu and Kubuntu, respectively.  They are desktop environments.

Here is something from the archives about switching to XFCE.  It is pre-Jaunty, but should essentially be the same.

[http://ubuntuforums.org/archive/index.php/t-785135.html](http://ubuntuforums.org/archive/index.php/t-785135.html)

Having GNOME installed is not the issue.  RUNNING it, however, is.

After you install XFCE, you should be presented with the option to run one or the other desktop environments.  Just chose XFCE.

This may not solve your problems entirely.

If your game requires graphics acceleration, you will likely be out of luck.  And GoogleEarth is a hog, so you still may have trouble.

Have you been to the two-way live fire range, or is the nickname a lark?

---

### Post by HardcoreSSG on 2009-09-16
Currently installing Xfce.
Will tell you how it goes
Oh and the nickname is just my Socom II name - and a band stage name. :lolflag:
HardcoreSilverSkullGuitarist

---

### Post by QIII on 2009-09-16
My nickname was Major A...ole before the fused cervical vertebrae and the steel in my ankle.

But that was long ago ... in another life ... in a land far away ...

---

### Post by HardcoreSSG on 2009-09-16
Well currently got XFCE up and running. I like this one better. BUT, still the graphics aren't working. I know its not just Google or Alien Arena because the screensavers still aren't working. (They didn't work before either) However, the few that did work still work.

---

### Post by HardcoreSSG on 2009-09-16
Ran a double check to make sure if I had something in compiz running -thought maybe that would fix it.

Well I still had compiz running. Disabled it- but I still had no luck. So Compiz is out of the question.


Tried to watch youtube (which I could watch on GNOME) 

On XFCE - youtube is EXTREMELY LAGGY!

On GNOME - A flash game runs horribly.

On XFCE - They run actually a lot better. 

Not sure what happened.

---

### Post by HardcoreSSG on 2009-09-18
Anybody got an answer to my problem?

---

### Post by HardcoreSSG on 2009-10-27
*bump*:(

---

### Post by Vaphell on 2009-10-27
think about trying Karmic out, maybe intel drivers got straightened up and will behave correctly.

---

### Post by HardcoreSSG on 2009-10-27
Will my programs (ubuntu-studio) transfer over?

Or do I have to reinstall everything. Send me some links! :D
BTW - I have tried every single intel graphics fix on jaunty that I could find. NONE OF THEM seemed to work!

---

### Post by HardcoreSSG on 2009-10-29
PROBLEM SOLVED! 

Anybody else that has this problem follow these steps!

Upgrade to Karmic (if you haven't already) :D
Follow these steps to install the "X Kernel"
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)
Then shut down your computer and reboot.
When the GRUB menu pops up hit ESC 
Boot into your newest kernel and ENJOY! 
Your intel graphics card will now work!

---

### Post by HardcoreSSG on 2009-10-29
Sorry guys but I just realized that the intel DOES work...but it's kinda laggy, for example the SkyRocket screensaver lags horribly so if anybody would like to figure out how to fix this lag. Be my guest.

---

