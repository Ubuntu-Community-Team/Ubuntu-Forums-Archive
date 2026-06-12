---
title: "Fixing overscan on an HDTV, or Custom resolutions in Ubuntu w/nVidia"
date: 2009-08-02
forum: General Help
---

### Post by djbon2112 on 2009-08-02
Hello everyone. I just built myself an HTPC for use with XBMC and Ubuntu. Everything is configured fine, except my display. Output is to a 720p 32-inch HDTV, however when I use the default settings with the nVidia control panel, I have an overscan problem: the computer is outputting 1280x720 but the screen needs to take 1330x768 (or whatever the bigger 720p is). The problem is that resolution isn't listed as an option when setting the resolution settings in the control panel: it detects the TV as a TV, and gives me options for 1920x1080, 1280x720, and a bunch of random lower resolutions with various ratios, but not the one I need.

How would I configure this resolution? I've messed around with xorg.conf a bit in the past, but every time I have my graphics have become completely mesed up.

---

### Post by realzippy on 2009-08-02
Have a look at your xorg.conf again,especially the modlines.
E.g.:

Section "Screen"
   Identifier "Default Screen"
   Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
   Monitor "SAMSUNG"
   DefaultDepth 24
   SubSection "Display"
      Modes "1280x1024" **"1330x768"** "1024x768" "832x624" "800x600" "720x400" "640x480"
   EndSubSection

If your resolution isn`t in the modline,edit it.

---

### Post by djbon2112 on 2009-08-04
Just tried messing with xorg.conf again, and I have nothing. Manually entering the resolution doesn't work, I still have overscan. Oh well, I guess I have to fix it on the TV, unless someone knows of a mod to compensate for overscan.

---

### Post by djbon2112 on 2009-08-04
I found a guide elsewhere on these forums as to how to manually set your ModeLines, and it did about jack. I'm seriously at a loss here. Why is this such a freaking problem!? (/rage)

On a related noted, does anyone know how to get the Optical audio out working on a Zotac ION board?

---

### Post by doas777 on 2009-08-04
exactly what type of nvidia card is it?
I have had a few problems, that seemed to be non-compatible cards (geforce 8500 for instance), and didn't support certain driver features, whether configured via tools, or directly in xorg.  

some things to try, would be checking nvidia for a newer driver, or downgrading to a previous one (via the hardware drivers applet).
[http://ubuntuforums.org/showthread.php?t=851626](http://ubuntuforums.org/showthread.php?t=851626)

---

### Post by djbon2112 on 2009-08-04
It's the nVidia ION chipset (which is technically a 9400M). I'm using the latest driver from the site (185.18.31). Also, hardware drivers doesn't display anything: I had to manually install the nVidia driver.

---

### Post by mr_roy on 2009-08-12
> **djbon2112 said:**
> It's the nVidia ION chipset (which is technically a 9400M). I'm using the latest driver from the site (185.18.31). Also, hardware drivers doesn't display anything: I had to manually install the nVidia driver.

I am having the same problems. I am using a Toshiba 32WLT66 TV with an Asrock Ion running Ubuntu 9.04 with the bleeding edge 190 drivers from Nvidida. The HTPC connects to the TV via HDMI. Via HDMI I get EDID resolutions but not the native resolution 1366x768. This is a bit odd but I dont think Toshiba will lift a finger to issue a new f/w for this TV.
If I use 1280x720 I get loads of overscan and I cant see the Gnome menus at the top of the screen. If I manually configure the 1280x720 resolution its lost on restart of the system. 

I have also manually edited the xorg.conf and added the modeline info from this thread:
[http://forums.entechtaiwan.com/index.php?topic=4255.0](http://forums.entechtaiwan.com/index.php?topic=4255.0)

But no go. 

I have also tried adding parameters for ignoring the EDID response from the TV. Info from here: [https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299](https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299)

But then I got no picture on the telly. 

I have also tried VGA but I can only see 640x480/320x240. I assume this something I have to fix via xorg.conf aswell?

I suppose the good news is that XBMC seems to run, shows video, plays sound etc. 

Any ideas? :)

Cheers

First post yay!

---

### Post by udude on 2009-08-15
I've just about given up on this overscan problem. The fact it existed two years ago and has not been fixed indicates it is not easy. 

My setup:
[INDENT]9.04
NV-7950GT
Samsung LN-S4051D (720p)
[/INDENT]
I run my setup on 1366x768 thru the VGA D-sub connector. Quality is not breathtaking, but hey at least it works.

I'm curious: has anyone seen the overscan problem on a 1080p? 
I'm considering to replace mt TV (maybe to the cool LED-backlight ones). It would be nice to know what to expect...

Also - has anyone tried to push 1080p over the d-sub(vga) connector? knowing I have a reasonably working fallback would also be relieving

---

### Post by mijung on 2009-09-27
I recently bought an Acer Revo 3600 with NVIDIA ION chipset and hooked it up to a LG 26LC3R LCD television via HDMI. Installed Ubuntu 9.04 and the latest NVIDIA binary drivers. This was giving me the same overscan problems as are reported at various forums all over the place.

I spent the better part of two days trying to figure out a solution and what eventually helped (somewhat) was to reduce the screen size in xorg.conf.

I had to put:

    ModeLine       "1157x685" 74.25 1157 1658 1698 1980 685 707 712 750 +hsync +vsync

in the "Monitor" section.

Furthermore, to allow for successfull Mode validation I had to put 

Option         "ExactModeTimingsDVI" "TRUE"

in the "Device" section of the NVIDIA ION device.

Of course this means running at 1157x685, which is not the native screen resolution. However, at least the complete desktop fits on the screen this way.

Hope this is of any help. Regards, Michael

---

### Post by Sean22 on 2011-01-07
Not sure if you still need this info, but for anyone else looking I just got the Zotac Zbox HD-ID40 hooked up to a 1080p Sony KDS-R70XBR over HDMI through a Denon receiver and am having the overscan problem (which is how I found this post).  Connected via HDMI directly to a newer LG 47LE8500 flat panel, though, does not have the overscan problem.

---

