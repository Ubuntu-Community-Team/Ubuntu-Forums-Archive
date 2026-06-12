---
title: "make external monitor as main display"
date: 2009-11-17
forum: General Help
---

### Post by firsttimeuser on 2009-11-17
I use ubuntu 9.10 and i have an external LCD monitor hooked up on my laptop at office, each display shows different windows.

The only problem right now is ubuntu always use my laptop display as main display, which is very cumbersome at times, can I somehow make the external LCD monitor as main display whenever it is hooked up to my laptop? thanks!

---

### Post by audiomick on 2009-11-17
May be someone can help, but I think that might be awfully complicated

---

### Post by firsttimeuser on 2009-11-17
not possible at all?

---

### Post by audiomick on 2009-11-17
Maybe. I looked into that a  couple of years ago, and couldn't figure it out, ended up giving up. But, as I said, that was a couple of years ago. The whole topic of external monitors and laptops has come a long way since then.

---

### Post by wobb on 2009-11-17
What graphic card you have? If it is ATI, you should have Catalyst Control Center installed and I believe that there is an option to set that you primary monitor will be external LCD monitor.
Cheers,

---

### Post by firsttimeuser on 2009-11-17
mine is an Intel Graphics Media Accelerator 4500MHD

---

### Post by twm3 on 2009-12-02
Hey First Time,

I have either the same or similar problem though I don't recall having the problem with Jaunty (9.04). The problem with Jaunty was that the X-server was miserably slow. GLXGears (I use it as a VERY rough benchmark) was putting out around 50 FPS in 9.04 which was miserable even for non-gaming programs even with the eye candy turned off.

The good news is that Karmic 9.10 is putting out around 150 FPS which is quite nice. The bad news is that the dual monitors aren't being handled that well.

I'm fairly sure that in 9.04, Jaunty put the primary/main screen on the external display and the secondary display on my desktop if I chose to have both monitors on at the same time. If I only had one monitor on at the same time, there was no problem.

Some other "features" I've found in Karmic is that in extended display, X apparently believes that I have one great big 1920 x 2000 display - never mind that my monitors are 1900 x 1200 (external) and the 1280 x 800 (notebook). If you do the arithmetic, there is a 640 x 800 portion of my desktop that I can't see. :-(

Another feature is that I have found that I have to put the notebook display under and to the extreme left of the external display (that is there is one continuous left hand edge)  to show all the icons on my desktop. If I have my notebook configured to be at the middle bottom of the external display, the folders fall into the black hole of the desktop that isn't shown by the notebook.

Lastly, when I launch an application, the top part of the window (don't know what that portion of the window is called but it has the menu options on the left, window name in the middle, and minimize, restore, and maximize on the right) hides underneath the panel. Yes, I can move the window around to get to the top part of the window but that becomes a royal pain in the a**.

It got all the more interesting when I put the panel on autohide. It would no longer be visible on the notebook (main/primary monitor despite my wishes) but would then be visible but not touchable on the external monitor that is configured to just above it. Ugh.

My current work around is to put the notebook display to the left of the external display. All the icons line up nicely on the external display. When I launch an application, all of the window is visible as the panel is on autohide. Not very elegant :-( but it works.

Hope this helps. Also hopes that this provides a bump so an X expert might see it and give words of wisdom.

BTW, like you I'm running an integrated Intel graphic chipset but am on a Dell D630.

~Tom

---

### Post by Cicer on 2009-12-09
I've found that whichever monitor I drag to the left side of the other in the Display preferences window becomes the main display. That is, all the desktop items line up at the upper left corner of the monitor that's on the left.

You can also move your top, bottom, and side panels from one monitor to another. To do that you click on a panel, choose properties, and then uncheck the box next to Expand. Then you can drag the panel from one monitor to the other. Once it's on the monitor you want, check the box next to Expand again.

I'm using an Intel X4500HD graphics chip.

---

### Post by lofarkas on 2009-12-13
> **Cicer said:**
> I've found that whichever monitor I drag to the left side of the other in the Display preferences window becomes the main display. That is, all the desktop items line up at the upper left corner of the monitor that's on the left.

You can also move your top, bottom, and side panels from one monitor to another. To do that you click on a panel, choose properties, and then uncheck the box next to Expand. Then you can drag the panel from one monitor to the other. Once it's on the monitor you want, check the box next to Expand again.

I'm using an Intel X4500HD graphics chip.
Thanks a lot for that one, man. I was looking for a way to move my system tray back to the external monitor after the 9.10 upgrade moved it to the laptop's display. This worked, now all is well again. (Hopefully the settings will be saved when I reboot and transitions to a single-monitor setup will be handled well.)

Edit: I mean the second tip. I tried switching the displays right to left before I found your post... all I got was a nasty bug where the mouse pointer was on the right screen but my clicks were registered as being on the left screen. Windows hanging off the side of the monitor, parts of the desktop not displayed etc. I.e. it the system mixed up the location and resolution of the monitors. Ouch.

---

### Post by kghastie on 2010-03-15
I was able to get my external to be the primary display (on the left) using this:

> ```
xrandr --output LVDS1 --off;
xrandr --output VGA1 --off;
xrandr --output VGA1 --auto --primary;
xrandr --output LVDS1 --auto --right-of VGA1;
```

From: [http://ubuntuforums.org/showthread.php?t=1308711&page=2](http://ubuntuforums.org/showthread.php?t=1308711&page=2)

Haven't tried restarting yet.

---

### Post by scouser73 on 2010-03-15
> **firsttimeuser said:**
> I use ubuntu 9.10 and i have an external LCD monitor hooked up on my laptop at office, each display shows different windows.

The only problem right now is ubuntu always use my laptop display as main display, which is very cumbersome at times, can I somehow make the external LCD monitor as main display whenever it is hooked up to my laptop? thanks!

**[COLOR="Red"]This assumes that you are using an Nvidia graphics card.[/COLOR]**

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by matthew4295 on 2011-01-30
I know this is an old topic here, but it still is a problem for some. I made this in literally 2 minutes. Just follow these really simple instructions.

1) Open Gedit
2) Input this:

xrandr --prop | grep "{^dis}connected" | cut --delimiter=" " -f1
xrandr --output HDMI1 --primary
#Make the HDMI1 your connection type.

3) Save as monitor-switcher.sh
4) Open terminal
5) chmod +x /path/to/monitor-switcher.sh
6) Make it start on boot.
7) System>Preferences>Startup Applications
8 ) Add
9) In the Command text box, Input this:

./monitor-switcher.sh

10) Restart and make sure it works.

Questions?

Email Me: [email]mhremis@yahoo.com[/email]

Title it: "External Monitor as Main Display Questions"

Good luck!!!

---

### Post by spaceporker on 2011-04-30
matthew4295, that script you wrote is awesome! I've been trying to figure this out all morning! The only thing that would make it better would be if not only would it make the external monitor the primary display at start up, but it would also automatically do it after the HDMI cable is plugged in.

But I have no idea how to do that...

---

