---
title: "xorg not detecting display properly"
date: 2010-08-10
forum: General Help
---

### Post by SquidProject on 2010-08-10
Greetings,
    I am new to Ubuntu.  I have used Gentoo Linux for about ten years, but got to a point in my life where fixing problems is not as much fun as it used to be.  I just need something that works, and so I switched to Ubuntu.
    So recently, I decided to hook up my desktop computer to my 40" LCD TV.  It's running an onboard Nvida geforce 7150 with 256 MB of RAM.  It's got an HDMI out put that I'm running directly to my TV.  The problem is, it's not detecting the size of the TV quite properly, and I lose the top and bottom of the screen, where my gnome menus and icons are.  I can't boot into recovery mode because it no longer shows me my grub menu.  I can't reconfigure X because I can't stop X from running.  Not sure that it would help anyway.  I do still have the LCD that it worked with before that I could hook up if need be, but I'd really prefer not to have to move it to where the TV is.
    I'm running the latest Ubuntu for AMD64, with a 1.6GHz Core 2 Duo and 2GB of RAM.   Any advice?

---

### Post by sandyd on 2010-08-10
> **SquidProject said:**
> Greetings,
    I am new to Ubuntu.  I have used Gentoo Linux for about ten years, but got to a point in my life where fixing problems is not as much fun as it used to be.  I just need something that works, and so I switched to Ubuntu.
    So recently, I decided to hook up my desktop computer to my 40" LCD TV.  It's running an onboard Nvida geforce 7150 with 256 MB of RAM.  It's got an HDMI out put that I'm running directly to my TV.  The problem is, it's not detecting the size of the TV quite properly, and I lose the top and bottom of the screen, where my gnome menus and icons are.  I can't boot into recovery mode because it no longer shows me my grub menu.  I can't reconfigure X because I can't stop X from running.  Not sure that it would help anyway.  I do still have the LCD that it worked with before that I could hook up if need be, but I'd really prefer not to have to move it to where the TV is.
    I'm running the latest Ubuntu for AMD64, with a 1.6GHz Core 2 Duo and 2GB of RAM.   Any advice?
use the escape key during the boot to boot into recovery mode.

---

### Post by SquidProject on 2010-08-11
It's not entering recover mode--I'm not seeing the BIOS or grub screen either.  I'm thinking it doesn't like console mode, though CTRL-ALT-F1 does get me a terminal, which is also bigger than the screen size (i can't see where i'm typing at the bottom).

---

### Post by robert shearer on 2010-08-11
> **carlee said:**
> use the escape key during the boot to boot into recovery mode.

On lucid and for grub2 hold down the **shift** key while booting

---

### Post by SquidProject on 2010-08-11
Still, the first thing I see is the Ubuntu splash screen and then the graphical login manager.  Can I tell it not to startx by default?

---

### Post by fyo on 2010-08-11
Do you see the BIOS POST and other boot information?

I have a problem (learned to live with it) with my graphics card and monitor where the card isn't detecting the EDID correctly. The result is that my display doesn't show anything until the drivers kick in. There is no good solution if that's your problem.

What I wound up doing was to download the EDID manually and basically point X to it. That fixes the issue once X kicks in, but I have no screen info until then. Yes, installing new versions of Ubuntu is a bit of a hassle ;)

---

### Post by SquidProject on 2010-08-11
Sounds like that is probably what the issue is--I can't see it POST or any BIOS information, or even the grub splash screen.  First thing it shows is the Ubuntu Splash screen and then the graphical login manager.  What do you mean by download the EDID manually and point X to it?  Is this a grub.conf kernel option or something?

---

### Post by fyo on 2010-08-11
> **SquidProject said:**
> What do you mean by download the EDID manually and point X to it?  Is this a grub.conf kernel option or something?

If you have an NVIDIA graphics adapter, you can run nvidia-settings and use the "Acquire EDID" function (it's in the window of the relevant monitor, e.g. DFP-0 under the GPU).

Once you have the EDID, you can "point X to it". Well, what I'm doing is actually using a feature of the "nvidia" driver (if you are using the "nv" driver, I don't know the syntax, or if it's even possible). In your xorg.conf file (not used so much anymore in Ubuntu, but creating it / adding lines to it will override the auto-configuration that otherwise takes place), add a CustomEDID option in the Screen section. A snippet from my xorg.conf:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 8500GT"
    Monitor        "Samsung 225BW"
    Option         "CustomEDID" "DFP-0:/root/225bw-rawedid.bin"
    Option         "ConnectedMonitor" "DFP"
    Option         "ExactModeTimingsDVI" "true"
    [...]

```

If the problem is that your EDID is corrupt or just plain wrong (some monitors will lie about their capabilities), you can just add a custom ModeLine / DisplaySize  instead. E.g. something along the lines of:

```
Section "Monitor"
    Identifier     "Samsung 225BW"
    DisplaySize     474    296
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
EndSection
```

You can find web-based ModeLine calculators to help you with the numbers...

---

