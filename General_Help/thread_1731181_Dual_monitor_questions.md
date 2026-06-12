---
title: "Dual monitor questions"
date: 2011-04-16
forum: General Help
---

### Post by Zeikcied on 2011-04-16
I've been curious about using my television as a second monitor.  Mostly for games.  But I have no idea about dual monitor setups, and I have some questions.

1. My graphics card, an NVIDIA GeForce GT 240, is currently connected to my monitor via DVI, and it has an HDMI port that I can use to connect to my television.  Can I do a dual monitor setup with a single graphics card?

2. I see in nvidia-settings there are two modes for multiple monitors, Separate X Screen and TwinView.  I assume TwinView is a single desktop split across the two monitors.  But if I go with separate X screens, how would I switch between them?

3. How would I go about taking a program, like MAME or another game emulator, and making it full screen on my television only?  Is one of the aforementioned modes better for this than the other?

---

### Post by Blasphemist on 2011-04-16
> **Zeikcied said:**
> I've been curious about using my television as a second monitor.  Mostly for games.  But I have no idea about dual monitor setups, and I have some questions.

1. My graphics card, an NVIDIA GeForce GT 240, is currently connected to my monitor via DVI, and it has an HDMI port that I can use to connect to my television.  Can I do a dual monitor setup with a single graphics card?

2. I see in nvidia-settings there are two modes for multiple monitors, Separate X Screen and TwinView.  I assume TwinView is a single desktop split across the two monitors.  But if I go with separate X screens, how would I switch between them?

3. How would I go about taking a program, like MAME or another game emulator, and making it full screen on my television only?  Is one of the aforementioned modes better for this than the other?

Q1 answer, yes you can use 2 monitors off one card.
Q2 answer, I don't have an nvidia card but you'll want to choose the setting that extends your desktop and it sounds like that is separate X screens. You'll move the mouse off the side of one screen and on to the other.
Q3 answer, applications don't run across both monitors but rather whichever one you choose to have it on. You can drag it from one to the other.

If you have further questions, it will help to know which Ubuntu version you are running.

---

### Post by camper365 on 2011-04-16
Q1: Blasphmesit answered it perfectly
Q2: I use TwinView for my configuration (I use 2 monitors). The only problem with this is that I have a laptop that, when away from the second monitor, a second screen is still "there" but not functional (I can't see it because it's not plugged in).  Separate X screen is very subtly different from TwinView in that a separate X screen has its own top, bottom, right, and left while TwinView has one giant resolution that spreads across both monitors (my resolution is something like 2440x900 of both monitors together). What this means is that dragging the mouse to the bottom of the shorter monitor (1280x768) means dragging it below the area of the screen so the mouse is invisible.  This doesn't mean much, but it is probably the basis of your choice. 
A separate X screen is actually a separately defined screen in the X configuration file while TwinView allows for one screen to spread across two monitors. The man page for xorg.conf is incredibly helpful.
Q3: As far as maximizing a window on the TV only goes, all you need to do is drag the window onto the TV and click maximize.  It doesn't maximize over both screens, it's only on both screens in the transition from one screen to another.

---

### Post by Zeikcied on 2011-04-16
So, even with the Separate X Screens option, I can move my mouse and windows from one screen to the other?

I sort of thought it meant a wholly separate X session or something.

So if I want to have MAME fullscreen on my TV, I would start it from a frontend or a terminal window that's on my television?

Any program (like MAME or other emulator or game) would lose input if I clicked on something on the other screen, right?  Or does something being fullscreen on one monitor prevent the mouse or keyboard from accessing anything on the other?

---

### Post by Blasphemist on 2011-04-16
> **Zeikcied said:**
> So, even with the Separate X Screens option, I can move my mouse and windows from one screen to the other?

I sort of thought it meant a wholly separate X session or something.

So if I want to have MAME fullscreen on my TV, I would start it from a frontend or a terminal window that's on my television?

Any program (like MAME or other emulator or game) would lose input if I clicked on something on the other screen, right?  Or does something being fullscreen on one monitor prevent the mouse or keyboard from accessing anything on the other?

Again I can't speak to the nvidia drivers specifics but I'm sure it will allow yours to work as mine does, with the possible difference in resolutions that my monitor allows as opposed to your TV. Functinally they will work the same. 

My launcher (Unity in my case or maybe Docky if you're not on 11.04 natty) is on the left monitor, the laptop monitor. I have a top panel on both monitors that is much the standard gnome panel. I'll include a screen shot but basically they work as if you had app windows tiled on one monitor. Window focus still works the same, the window with focus still gets the keyboard input. The mouse is a little different but this isn't affected by 2 monitors, I can have focus in the terminal but if the mouse is over the browser my scroll wheel can move the page. 

My resolution is different on the two monitors as you can see by the black area at the bottom of the left screen in my screenshot. I had to install the multiple display application to get the displays just right.

---

### Post by Zeikcied on 2011-04-16
Well, like the thread tag says, I'm in Kubuntu.  Currently version 10.10 (though I'll likely do a software upgrade to 11.4 when it's released).  But since the dual monitor thing seems to be an X feature rather than a desktop manager feature, I assume that KDE will work the same as GNOME in this case.

Thanks for answering my questions. :)

---

