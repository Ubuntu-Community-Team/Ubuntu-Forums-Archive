---
title: "Can't enable Compiz after upgrading to 9.10"
date: 2009-10-29
forum: General Help
---

### Post by M@s on 2009-10-29
Hey!

I've now been upgading to 9.10, but after the reboot Compiz was disabled. When I try to enable it in the settings, error message "Desktop effects could not be activated" appears. 

I run compiz-check, which tells me this:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 
```

So what's this all about?

The installation was not made smoothly, some errors popped up and then I was told that a recovery was being made. But after a reboot, 9.10 booted up anyways!

Thanks.

---

### Post by camper365 on 2009-10-29
Compiz won't prevent a boot. Check to see if the package is broken. If it isn't check for any dependencies.
It looks like your problem might be in this bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122) which contains a fix.

---

### Post by M@s on 2009-10-30
Thanks, seems like that bug was the problem. I removed the nvidia drivers, reinstalled the intel drivers and rebooted, then it worked!

---

### Post by flipper9 on 2009-11-01
My Karmic system doesn't seem to have "compiz-check"...where does one get it?

Nevermind...got off my duff and used the Google and found...

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by flipper9 on 2009-11-01
The script worked great, told me what chip I had, and offered to skip checks since my chip is blacklisted.  Did that, rebooted, and got a black screen.  Had to load up LIVE CD-ROM and re-enable blacklist checks.  Oh well.  

Any updates or tweaks I can make to get the following to work???

Distribution: Ubuntu 9.10 (Karmic) Release with all updates installed via update-manager
Desktop: GNOME
Graphics Chip: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
Driver in use: intel
Rendering method: AIGLX

texture_from_pixmap: OK
non power of two support: OK
composite extension: OK
FBConfig: OK
hardware/setup problems: WARN=blacklisted

Warning: PCI ID 8086:2562 detected

---

### Post by flipper9 on 2009-11-01
Tried the xorg-edgers drivers, ran the script again, ignored the blacklist, rebooted, and could boot in again.  Tried enabling desktop effects through the Preferences/Appearance dialog using the "Normal" effects (2nd option), the panel disappeared, and the system hard-locked.

---

