---
title: "Dual Monitor help"
date: 2011-06-03
forum: General Help
---

### Post by programmer47 on 2011-06-03
Hi! All: I am having some issues with my dual monitor setup. It's a desktop with two monitors connected. the main monitor works fine. The 2nd monitor shows the background color, I can move my mouse into it, but somehow I can't move any application window to the 2nd monitor. My keyboard doesn't seem to work on the 2nd monitor. What did I do wrong?

---

### Post by CoolJohnB on 2011-06-03
I think if you go to >System Settings>Monitors and put a tick in the box to show the same in both, you will find that will work.

Hope it does for you.

---

### Post by wolfgangmcq on 2011-06-03
"Show same in both" will make the same thing appear in both monitors, won't it? That kind of defeats the point of dual monitors. Besides, the keyboard should have nothing to do with the monitor.

---

### Post by programmer47 on 2011-06-04
I opened the system setting -> Monitor, it shows only one monitor. Although in NVDIA X Server Settings there are two monitors identified. The 2nd monitor is set to "Seperate X screen". The position of the monitor is also correct. I tried to change it to TwinView, but got an error message, however I suspect "Seperate X Screen" is the correct setting.

Anyway, I can move my mouse into the 2nd screen, but can't move any window into it, I tried to create a launcher on the desktop, but found my keyboard focus would not go to the 2nd screen, whatever I type it appears in the main screen, again let me emphasize I AM able to move my mouse to the 2nd screen.

Anyone has any idea what's going on here?

---

### Post by glisstech on 2011-06-04
I have dual monitors set up and working on an Nvidia GT430 using a Samsung 40" LCD as the second monitor

First, you have to change the Nvidia Xserver settings as root
Open a Terminal and enter
gksudo nvidia-settings
You will be prompted for your password
Move to - X Server Display configuration
You should see a graphic representation of your monitors with current resolution
Ex  Samsung    Viewsonic
   1920X1080   1920X1080

If they are both enabled, click on the configure button and choose TwinView

This will give you the functionality of being able to drag windows between the monitors like in Windows. Other settings will use the Snap Window feature and you won't be able to drag your windows between screens.

Click on the check box while the desired moniter is highlighted to pick the primary dispay.

Also, only 1 display should be set to Absolute position, the other should be changed to right of, left of, whatever is going to work for your physical setup.

Click apply, and Save to X Configuration file and Quit Nvidia Xserver Settings.

Reboot, and all should be what you are looking for.

The Monitors applet in System Settings doesn't seem to support multiple displays, at least on mine, it still only shows 1 unknown display at 3840X1080. Maybe this is because I am using the Nvidia current accelerated drivers.

---

### Post by programmer47 on 2011-06-06
Thanks for the reply.

I did the nvidia-settings, but after I switched to TwinView and clicked the Apply button, it gave me an error msg says:
Failed to set MetaMode(1) 'CRT-0: 1920x1200
@1920x1200+0+0, CRT1: 1920x1200
@1920x1200+1920+1'(Mode 3840x1200, id:51)
on X sreeen 0


1920x1200 is the current setting for both my monitors.

---

### Post by sectshun8 on 2011-06-06
Are both monitors physically the same size?

I only ask because when I was doing a dual monitor setup with my netbook, putting both the netbook and the ext monitor at the same resolution resulted in what you are having now.  The main desktop is fine, the second one just the background color, can move mouse but no windows.

However, when I changed the resultion ont he 2nd monitor to something a little less, BAM, the desktop wallpaper showed up and I was able to move windows over.  Try playing with that?

---

### Post by programmer47 on 2011-06-07
No, the two monitors are not the same physical size, although their resolution are the same.

I tried to reduce the resolution of the 2nd monitor, but somehow the 2nd monitor won't take it.

I am giving this up, even if I somehow make it work with lower resolution, it is still not a good solution anyway.:(

---

