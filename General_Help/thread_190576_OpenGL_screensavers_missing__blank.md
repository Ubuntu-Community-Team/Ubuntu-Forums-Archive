---
title: "OpenGL screensavers missing / blank??"
date: 2006-06-06
forum: General Help
---

### Post by msak007 on 2006-06-06
Sometime last night my OpenGL screensavers disappeared / stopped working. The entries for them are still there when I go to change the screensaver, but the preview window is blank (black background). When I click on "Test" or lock my session, the screensaver doesn't come on - it's just a static image of my Desktop. When I move the mouse, I'm prompted for my password to unlock the session. I think it may have been due to an update or something I installed, so my question is if Adept / Adept Updater has a log of what it installed. I ask because when I got the prompt to update my software, I recall seeing something that had "OpenGL" in there somewhere. After that update is when I noticed that it stopped working. I made some other display adjustments (through the Display module / xorg.conf) around the same time so I want to eliminate the possibility of it being display settings, and all my other screensavers are unaffected. I've restarted X and the whole comp, same result. Anybody else experience this issue?

---

### Post by msak007 on 2006-06-06
Well, in case anyone cares or has the same problem I did, I fixed my problem. After trying to remove / reinstall kscreensaver and having that not work, I checked for the screensavers and found they were still there. Then I ran glxgears to see the output. Sure enough, my 3D acceleration was broken and I got the following output:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

First thing I did was to check xorg.conf, but the "glx" module was still listed and loaded. I thought it might be due to some changes I made to my display configuration using the System Settings Display Module. I initially had some problems with it being broken (refer to my posts in [this]("http://www.ubuntuforums.org/showthread.php?t=189373") thread) and after I fixed it, decided to change the name of my generic hardware to something more specific. I changed my monitor to "Dell 2005FPW" rather than the generic "Plug n Play", and modified the aspect to widescreen. I did this for my secondary display as well. After applying the settings and restarting X, that's about the time that the screensavers broke. I did get a warning that the configuration hadn't been tested, but clicked OK anyway. So I restored the default xorg.conf, modified the driver from "vesa" to "fglrx" manually (rather than running aticonfig --initial), and restarted X. Now both my Display Module and OpenGL screensavers work. So I guess changing the hardware listed in the Display Module messes things up, even if it is the hardware you have.

---

### Post by malathia on 2006-12-30
Did you check your /var/log/Xorg.0.log to see if there were errors that kept the appropriate GL modules from loading when x was started? 

I know that, though I have a 1400x1050 LCD on my t22, and that this is fine under WindowsXP vis a vis direct3D enablement, under Linux, with the savage drivers appropriate for my Video card, I noticed that, at 1400x1050, DRI says I have too little vram to load 3D by about 800Kb. 

The point of this is that perhaps when you switched to widescreen, though you do have a widescreen, it pushed the vram required to run 3D under linux beyond what your video card has to offer?

A possible avenue to explore.

---

