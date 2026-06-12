---
title: "Alternative desktop managers and dual monitors"
date: 2006-03-07
forum: General Help
---

### Post by mrogers on 2006-03-07
I've got an Ubuntu install that I'm pretty happy with. However, I always like to play around, and there are some aspects of Metacity and the Gnome panel that I don't care for (the ugliness of the panel, for one -- half the crap on there won't obey background settings for the rest of the panel). I'm experienced with KDE but hate it, so that leaves it out. Last night I tried a couple of alternatives -- FluxBox and then XFCE (in the form of xubuntu-desktop). I'd never used anything other than Gnome or KDE before, so it was a new experience for me. I liked a lot of things about XFCE, but there were several things I couldn't stand and I wanted to ask if it's possible to change XFCE to do what I want. I did spend some time with it, but was unable to figure this stuff out.

I have dual monitors. The one big, huge thing that I like about Gnome panel is the ability to have ONLY the task bar items for monitor 1 be displayed on the task bar on monitor 1, and ONLY the task bar items for monitor 2 be displayed on the task bar on monitor 2. So far, I haven't figured out how to make another taskbar in XFCE, let alone specify which monitor they show tasks from.

The other issue I have is windows appearing across the span of the two monitors. Metacity seems to be smart enough to avoid this; I never get a window that appears straddling the two screens. But XFCE doesn't seem to know or care about TwinView and just sticks windows to the right of whatever ones are already open, regardless if it's across the screen split or not.

I hope someone knows how to address these issues. I'm tired of being stuck with the major DMs just because I have two monitors. I can't use XGL/Compiz, and now I can't use FluxBox or XFCE, apparently, because they both have usability issues if you have more than one monitor. Does anyone use any of these other window/desktop managers and have more than one monitor? Any advice? Thanks.

---

### Post by bodhi.zazen on 2006-07-11
mrogers;

I just installed a nvidia card and have the same issues. Did you ever slove this issue?

For myself I can only run xfce. I have not tried KDE. Gnome streatches the badkground image across both of my monitors.

I am interested in Fluxbox as this has been my primary WM prior to this.

If it would help, I can post my xorg.conf so you may have the configuration for xfce at least.

Also check out this file:

[http://darkshed.net/files/rcs/misc/xorg.conf](http://darkshed.net/files/rcs/misc/xorg.conf)

READ the comments CAREFULLY. I have not yet tried it.

Also check this out:

[http://www.justlinux.com/forum/showthread.php?threadid=143803](http://www.justlinux.com/forum/showthread.php?threadid=143803)

or

[http://www.justlinux.com/forum/showthread.php?p=850062#post850062](http://www.justlinux.com/forum/showthread.php?p=850062#post850062)

Or post you solution.

Thank you

---

### Post by Devarien on 2006-07-17
> **mrogers said:**
> I've got an Ubuntu install that I'm pretty happy with. However, I always like to play around, and there are some aspects of Metacity and the Gnome panel that I don't care for (the ugliness of the panel, for one -- half the crap on there won't obey background settings for the rest of the panel). I'm experienced with KDE but hate it, so that leaves it out. Last night I tried a couple of alternatives -- FluxBox and then XFCE (in the form of xubuntu-desktop). I'd never used anything other than Gnome or KDE before, so it was a new experience for me. I liked a lot of things about XFCE, but there were several things I couldn't stand and I wanted to ask if it's possible to change XFCE to do what I want. I did spend some time with it, but was unable to figure this stuff out.

***I have dual monitors. The one big, huge thing that I like about Gnome panel is the ability to have ONLY the task bar items for monitor 1 be displayed on the task bar on monitor 1, and ONLY the task bar items for monitor 2 be displayed on the task bar on monitor 2.*** So far, I haven't figured out how to make another taskbar in XFCE, let alone specify which monitor they show tasks from.

The other issue I have is windows appearing across the span of the two monitors. Metacity seems to be smart enough to avoid this; I never get a window that appears straddling the two screens. But XFCE doesn't seem to know or care about TwinView and just sticks windows to the right of whatever ones are already open, regardless if it's across the screen split or not.

I hope someone knows how to address these issues. I'm tired of being stuck with the major DMs just because I have two monitors. I can't use XGL/Compiz, and now I can't use FluxBox or XFCE, apparently, because they both have usability issues if you have more than one monitor. Does anyone use any of these other window/desktop managers and have more than one monitor? Any advice? Thanks.

How did you set that up? I'd be very interested in getting that sort of setup on my current dual monitor config...

-Dev

---

### Post by bodhi.zazen on 2006-07-17
Devarien:

It is impossible to help without knowing more information. What is your hardware set-up.

I use a nvidia card with twin view, but there are so many variations on hardware including dual video cards. If it would help I can post the relevant parts of my xorg.conf.

FYI: XFCE supports twinview and each monitor can have it's own wallpaper and toolbar(s). With XFCE, the new nvidia driver and twinvew, new windows do not open across two windows (as described above).

I am having the above issues with Fluxbox, however.

---

### Post by Devarien on 2006-07-19
I am running a HP Pavilion zd7200 CTO (zd7000 class) notebook with a Geforce FX Go5700, connected to an external Sony Multiscan 17" CRT monitor through the VGA port.  The resolutions you can see in the xorg.conf file above (I'm not at home right now and therefore can't give you explicit specs).  It is a single video card which outputs to my laptop LCD and my CRT (it recognizes the CRT as the primary monitor - still looking into how to "fix" that)

If you could paste your xorg.conf, that would be great.  I just need to see the [Option    "Independent Taskbars" "On"] line.

-Dev

---

### Post by bodhi.zazen on 2006-07-19
Devarien:

If you have not done so, install the nvidia drivers.

I will try to post my xorg.conf later today.

---

### Post by bodhi.zazen on 2006-07-19
First configure your nvidia card and backup your current, working /etc/X11/xorg.conf.


Here are the relevant sections of my file:

This is not the entire /etc/X11/xorg.conf.

Note: I am now using arch linux but this should work.


Section "ServerLayout"
#    Identifier     "Layout0"
    Identifier     "Simple Layout"    
    Screen         "Videoconfig"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


# **********************************************************************
# # Module section -- this  section  is used to specify
# # which dynamically loadable modules to load.
# # **********************************************************************
# #
 Section "Module"
         Load "dbe"      # Double buffer extension
         SubSection "extmod"
         Option "omit xfree86-dga"   # don't initialise the DGA extension
         EndSubSection
         Load "type1"
         Load "freetype"
         #Load "speedo"
          Load "glx"
EndSection

# **********************************************************************
# Server flags section.
# ***********************************************************************
#
Section "ServerFlags"
#    Option     "NoTrapSignals"
#    Option     "DontVTSwitch"
#    Option     "DontZap"
#    Option     "DontZoom"
#    Option     "DisableVidModeExtension"
#    Option     "AllowNonLocalXvidtune"
#    Option     "DisableModInDev"
#    Option     "AllowNonLocalModInDev"
#    Option      "blank time"    "10"    # 10 minutes
#    Option      "standby time"  "20"
#    Option      "suspend time"  "30"
#    Option      "off time"      "60"

 # Option   "EstimateSizesAggresively" "0"

EndSection



# **********************************************************************
# Graphics device section
# **********************************************************************

Section "Device"

	Identifier     "Videocard1"
	VideoRam  256000
	VendorName  "nVidia Corporation"
	BoardName   "Video device"
	Driver     "nvidia"
	BusID       "PCI:1:0:0"
#       Screen      "Videoconfig"
	Screen 0
	Option "TwinView"
	Option "MetaModes" "1600x1200,1600x1200"
	Option "TwinViewOrientation" "LeftOf"
	Option "SecondMonitorHorizSync" "UseEdidFreqs"
	Option "SecondMonitorVertRefresh" "UseEdidFreqs"

EndSection






You will need to modify this somewhat, but you should be able to look at your current /etc/xorg.conf for settings.

Watch:

in Device section:

You may need to change the BusID

In MetaModes the format is resolution_screen_0,resolution_screen1

In the TwinViewOrientation your may need to change LeftOf to RightOf

Let me know if you need help.

---

### Post by bodhi.zazen on 2006-07-21
Now, assuming you are running twinview with two monitors:

1. Start gnome.

2. At the bottom of screen 1:
Right click your mouse over the bottom panel
Choose "New Panel"

This will make a new panel.

3. Drag the new panel to your desired location 
? Bottom of second screen possibly

4. Right click on your new panel.
Choose "Add to Panel"
This will bring up a box "Add to Panel"

5. Choose "Window Selector".

You should now have a (bottom) panel on both screens.
Each application will minimize to the bottom of their respective screens (when minimized).

Enjoy !

---

### Post by bodhi.zazen on 2006-08-08
I have been using dual monitors for a few weeks now. I am planning to write a how-to on configuring X.

In the interim I have found (with nVidia):

Dual monitor = 2 monitors, no twinview, separate sessions on each monitor.
Twinview= 1 large monitor.

Use the following settings

Twinview-> XFCE, IceWM, Openbox.

Dual Monitor -> fluxbox.

Brief hints:

When configuring X set up more then 1 server layout. You then select which server with the option;

startx -layout LAYOUT_NAME

Also you can run multiple, virtual X sessions.

Example (all one line):

startx /usr/bin/fluxbox -- :2 -layout DUALSCREEN will start a new X session on a second screen (CTr-Alt-<F8>).

Last, which panel to use?

I can not get pypanel to run with dual monitors.
xfce4-panel is a good, all purpose panel
perlpanel is also good.

Fluxbox is OK without an additional panel.

IceWM and openbox benefit from additional panels.

You can easily write a start script to open programs. Ex

in /home/user_name

Make a file icewm

Add this:
#! /bin/bash
exec pypanel &
exec fbsetbg -f /path/to/wallpaper.jpg
/usr/bin/icewm

Make file executable

Now startx /home/user_name/starticewm -layout TWINVIEW

This starts icewm, perlpanel, and sets a background image.

---

