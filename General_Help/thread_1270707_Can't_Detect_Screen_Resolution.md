---
title: "Can't Detect Screen Resolution"
date: 2009-09-19
forum: General Help
---

### Post by eosha on 2009-09-19
Hi all,

Just installed 9.04 on an older computer. I'm using a Sanyo DP19649 monitor, which can handle 1366x768. However, the computer can't detect it, and Preferences>Display has Monitor: Unknown. The resolution only shows 640x480 and 800x600. Clicking "Detect Monitors" does nothing. 

This is using onboard video (Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device). I've tried to play with my xorg.conf, but without success. 

Help?

---

### Post by CatKiller on 2009-09-20
You could try putting

```

                HorizSync       30-50
                VertRefresh     50-75

```

In the Monitor section of your xorg.conf. This provides the refresh rate ranges that X can use to calculate the modes that are available. X would normally get that information from the EDID output from a monitor, but it seems that your TV doesn't provide any of that.

---

### Post by eosha on 2009-09-20
Ok, that helped some. Now I've got 1024x768 available as well. Ideas on how to get the full 1366x768?

---

### Post by eosha on 2009-09-20
I looked in the owner's manual and found this: 

RESOLUTION  ASPECT RATIO REFRESH RATE HORIZONTAL    VERTICAL
                             (Hz)     FREQUENCY  FREQUENCY (Hz)

 1024 x 768      4:3          60         48.36        60.00
 1280 x 768     15:9          60         47.78        59.87
 1280 x 720     16:9          60         45.00        60.00
 1360 x 768     16:9          60         47.71        60.00

I tried plugging 47.71 and 60 into the HorizSync and VertRefresh, but it didn't do anything except take away the options of 640x480 and 800x600.

---

### Post by CatKiller on 2009-09-20
> **eosha said:**
> Ok, that helped some. Now I've got 1024x768 available as well. Ideas on how to get the full 1366x768?

That's a start.

You could try putting ```
        Option          "ModeDebug"                     "True"

``` in the Device section (which causes X to be more verbose in the log) and then check (or post here) X's log, which is at /var/log/Xorg.0.log, to see why the higher modes aren't being selected.

```
gedit /var/log/Xorg.0.log
``` should be sufficient to look through it, or copy-and-paste into a message here. If you do post the log here, putting the text in [code] tags will make it significantly easier to read.

---

### Post by eosha on 2009-09-20
This looks like the relevant bit...

```

(II) VESA(0): Total Memory: 125 64KB banks (8000kB)
(II) VESA(0): Configured Monitor: Using hsync range of 30.00-50.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-75.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 30.00-50.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-75.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"

```

---

### Post by CatKiller on 2009-09-21
> **eosha said:**
>  (II) VESA(0):

That's significant. I'm not sure the vesa driver does higher resolutions. Is that one of the changes that you made? If your integrated graphics are supported by the intel driver, that's probably the way to go.

---

### Post by eosha on 2009-09-21
That's done it!

I edited /etc/X11/xorg.conf, under section "Device" changed the driver from "vesa" to "intel", and rebooted. Now I have 1368x768 as an option in Preferences>Display.

Thanks a lot!

---

### Post by CatKiller on 2009-09-21
> **eosha said:**
>  Thanks a lot!

No worries. Glad it worked.

---

