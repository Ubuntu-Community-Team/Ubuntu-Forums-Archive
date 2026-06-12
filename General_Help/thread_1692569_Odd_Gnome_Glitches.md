---
title: "Odd Gnome Glitches"
date: 2011-02-21
forum: General Help
---

### Post by Raindance on 2011-02-21
Hey guys,

I have a few issues with Ubuntu that are small and hardly performance problems, but are **severely annoying!** Here's a little list, if anyone can help with any of them that'd be great!

-**Clock stops updating randomly**: It will just happen with no cause; the little clock app on my taskbar gets stuck on a time and will not change until the computer is completely turned off then on again. 
-**Taskbars switch places on reset: **I have 2 bars, both on the bottom; one is my taskbar with Applications, Places, System, etc and the other one holds my workspaces and running applications. They randomly switch places when I reset, sometimes on top sometimes on bottom(of eachother, but they always stay at the bottom of the screen).
-**Taskbar icons change places**: Again, not really end of the world stuff, but my application shortcuts on my taskbar will reorder themselves on a reset. Pretty annoying, I like to keep my bars and desktop organized and clean.
-**Evolution mail fails to show up on the mail icon on the taskbar:** When I first installed, the taskbar's mail icon held chat and evolution mail client. Now, the mail client is gone and does not start up when I boot up. Even if I run the client, it will not place itself in the taskbar mail icon.
-**Volume gets stuck on mute and does not change EVER!: **Even though I am able to adjust the volume normally, the icon in my tray is muted and does not change, even with a reset!
-**Battery and Wifi connectivity icons in taskbar has swapped!?!:** Another weird one...my Wifi and network center is located in my battery control and power options button and my Battery and Power Options is located in the Wifi connectivity icon on the system tray. They do not change back with a reset.

I'm not sure which Gnome version I'm running, it's the regular one included with Ubuntu 10.10 iso. These little bugs are hardly system breaking, but they really disturb my calm and I get ready to beat my roommate with my keyboard whenever I boot up.

Some other details;
-ACER Aspire 5532 Laptop
-3gb Ram
-1.6 ghz Processor
-ATI Radeon hd3200 GFX Card
-Ubuntu 10.10

Have not had any other problems with the system, am really enjoying the freedom of Linux over my damn Windows 7. I love it, but maybe I need to downgrade to an earlier, sturdier version of Gnome? I'd even be willing to migrate to KDE.

Thanks!

---

### Post by gerowen on 2011-02-21
I've had "very" occasional problems with a panel applet not starting, but none of these.  Sometimes if you play a full screen game that changes your resolution, it can jumble up your panel icons and move them around on you.  As far as the time not updating and things, I'm not sure what to tell you.  You could try running:
```
sudo killall gnome-panel
```
and see if that fixes some of the issues when they occur without completely restarting.

---

### Post by Raindance on 2011-02-21
Hey thanks, that sorted some of the problems(for now anyways -.-)

Doing a killall fixed the battery/wifi problem and the clock updating, but I still have the remaining problems. I also wonder how long this will last, I figure it's temporary. 

Anyways, thanks that will make it less annoying when my taskbars decide to screw up!

---

### Post by Raindance on 2011-02-22
Nvm Fixed it....migrated to KDE no glitches yay!

---

