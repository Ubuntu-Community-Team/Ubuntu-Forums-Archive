---
title: "Force monitor type"
date: 2011-07-17
forum: General Help
---

### Post by introiboad on 2011-07-17
Hi there,

I have a very simple question for a very simple use case. Just installed Natty (11.04) on an old computer for my disabled brother with:

* Video Card:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

* Monitor:

VGA Mitsubishi Diamond Pro 750SB (old CRT monitor)

The problem is that when I select System -> Preferences -> Monitors, the monitor is shown as unknown and it only allows me to set 1280x1024 (shows 0Hz as display refresh rate) which is way too high for my brother. I was wondering if there's a way to select the proper monitor from a list so all display resolutions are shown and I can select a lower one for him.

Thanks very much in advance!

---

### Post by CatKiller on 2011-07-17
You could try adding ```
        HorizSync       30-96
        VertRefresh     50-160
``` to the Monitor Section of your /etc/X11/xorg.conf. This will tell X how to calculate the available resolutions that it would get automatically from the monitor if the monitor supported EDID.

EDIT: If you don't have an xorg.conf (I can't remember if a default 11.04 install has one or not) you can create one with ```
gksudo gedit /etc/X11/xorg.conf
``` and put this in it:

```
Section "Device"
    Identifier    "Configured Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync      30-96
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Single Screen"
    Device        "Configured Device"
    Monitor       "Configured Monitor"
EndSection
```

---

### Post by introiboad on 2011-07-17
> **CatKiller said:**
> You could try adding ```
        HorizSync       30-96
        VertRefresh     50-160
``` to the Monitor Section of your /etc/X11/xorg.conf. This will tell X how to calculate the available resolutions that it would get automatically from the monitor if the monitor supported EDID.

Thanks for your help.

The problem is that there is no /etc/X11/xorg.conf, the file simply doesn't exist:

julia@julia-desktop:~$ ls -la  /etc/X11/
total 88
drwxr-xr-x  10 root root  4096 2011-07-17 13:57 .
drwxr-xr-x 133 root root 12288 2011-07-17 14:04 ..
drwxr-xr-x   2 root root  4096 2011-04-26 01:05 app-defaults
drwxr-xr-x   2 root root  4096 2011-04-26 01:05 cursors
-rw-r--r--   1 root root    14 2011-04-26 01:04 default-display-manager
drwxr-xr-x   4 root root  4096 2011-04-26 01:00 fonts
-rw-r--r--   1 root root 17394 2010-02-19 01:02 rgb.txt
lrwxrwxrwx   1 root root    13 2011-07-17 12:20 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2011-04-26 01:05 xinit
drwxr-xr-x   2 root root  4096 2011-02-08 14:27 xkb
-rwxr-xr-x   1 root root   709 2010-11-02 22:17 Xreset
drwxr-xr-x   2 root root  4096 2011-07-17 13:57 Xreset.d
drwxr-xr-x   2 root root  4096 2011-07-17 13:57 Xresources
-rwxr-xr-x   1 root root  3730 2010-12-02 04:34 Xsession
drwxr-xr-x   2 root root  4096 2011-07-17 13:57 Xsession.d
-rw-r--r--   1 root root   265 2010-02-19 01:02 Xsession.options
-rw-r--r--   1 root root   601 2011-04-26 00:54 Xwrapper.config

Thanks!

---

### Post by CatKiller on 2011-07-17
> **introiboad said:**
> The problem is that there is no /etc/X11/xorg.conf, the file simply doesn't exist:

It occurred to me that that might be the case, hence my edit that I was probably writing as you wrote this reply :)

---

### Post by introiboad on 2011-07-17
> **CatKiller said:**
> It occurred to me that that might be the case, hence my edit that I was probably writing as you wrote this reply :)

So, once without xorg.conf, there is no easy way to provide information about the display when it is not correctly autodetected?

EDIT: Damn, I missed your edit! Trying it now!

Thanks anyway for your help!

---

### Post by introiboad on 2011-07-17
> **CatKiller said:**
> You could try adding ```
        HorizSync       30-96
        VertRefresh     50-160
``` to the Monitor Section of your /etc/X11/xorg.conf. This will tell X how to calculate the available resolutions that it would get automatically from the monitor if the monitor supported EDID.

EDIT: If you don't have an xorg.conf (I can't remember if a default 11.04 install has one or not) you can create one with ```
gksudo gedit /etc/X11/xorg.conf
``` and put this in it:

```
Section "Device"
    Identifier    "Configured Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync      30-96
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Single Screen"
    Device        "Configured Device"
    Monitor       "Configured Monitor"
EndSection
```

Hi again,

Just tried exactly what you wrote. Added an xorg.conf (using vi instead of gedit but there should be no difference) and my xorg.conf contains what you pasted above. Still after a logout-login cycle, no luck, only one (very high) resolution supported.

Any ideas?

Thanks!

---

### Post by rickytikki on 2011-07-17
> **introiboad said:**
> Hi there,

I have a very simple question for a very simple use case. Just installed Natty (11.04) on an old computer for my disabled brother with:

* Video Card:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

* Monitor:

VGA Mitsubishi Diamond Pro 750SB (old CRT monitor)

The problem is that when I select System -> Preferences -> Monitors, the monitor is shown as unknown and it only allows me to set 1280x1024 (shows 0Hz as display refresh rate) which is way too high for my brother. I was wondering if there's a way to select the proper monitor from a list so all display resolutions are shown and I can select a lower one for him.

Thanks very much in advance!

Do you know the specs of the crt monitor and what was the exact resolution for the last os before you install natty??

---

### Post by introiboad on 2011-07-17
> **rickytikki said:**
> Do you know the specs of the crt monitor and what was the exact resolution for the last os before you install natty??

Although I do not have the exact specs, I am 100% sure that the monitor supports 800x600 and 1024x768 as well as 1280x1024. Both the former options would be better than the latter which is the only one I can currently select. It is a relatively high end CRT monitor I used to run with Windows and I am certain I used 1024x768 with it.

I have the suspicion that adding xorg.conf made no difference at all. Does anything else need to be tweaked for Natty to pickup /etc/X11/xorg.conf if present?

Thanks again!

Carles

---

### Post by CatKiller on 2011-07-17
> **introiboad said:**
> I have the suspicion that adding xorg.conf made no difference at all. Does anything else need to be tweaked for Natty to pickup /etc/X11/xorg.conf if present?

No, if it's there it will be used.

X's log is at /var/log/Xorg.0.log. If you look through that it will tell you which modes it has decided are available from which source, and why it has rejected the ones that it has. There is an option to tell it to log even more stuff, although I can't remember exactly what it is at the moment. (EDIT:     ```
     Option        "ModeDebug"            "True"
``` in the Device Section)

With my old monitor it wasn't that it didn't provide EDID values, it was that the values it provided were incorrect. So I had to put ```
    Option        "UseEDID"            "False"
``` in the Device Section.

If you're trying to get things to be larger on screen, picking a lower resolution is a horrible way to do it. Increasing the size of things (fonts, icons, interface elements) at a better resolution is a much saner approach. Low-resolution text is blocky and horrible to read no matter how large you make it.

---

