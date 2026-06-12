---
title: "Problem fixed: slow Firefox with Jaunty on old Dell D600"
date: 2009-08-21
forum: General Help
---

### Post by ujecrh on 2009-08-21
After upgrading my old Dell 600 everything felt a bit sluggish with the worst application being Firefox. Display, scrolling, clicks response, were so slow it made Firefox barely usable. Disabling visual effects did not help much either.

After some research and tests it turns out the old ATI card on this box does not like the EXA acceleration which now default in Jaunty. Adding:
	Option "AccelMethod" "XAA"
to the Device section of  /etc/X11/xorg.conf resolved the issue and things are snappy again now.

Also, for the Wacom tablet users, I had problem with the Wacom mouse not registering clicks, forcing me to click multiple times (or click slower/longer) which gets old very fast... Solved that problem too by installing wacom tools (from Synaptic) and making sure the following command is run every time Gnome starts:
	xsetwacom set "Wacom Graphire3 6x8 cursor" suppress 15

Hopefully the above will help other people save some time.

---

### Post by pawhtiobo on 2009-08-21
Hi :)

I also got a D600, your ATI does the 1440X1050 screen resolution?

---

### Post by zcacogp on 2009-08-21
Thanks for this. 

It's seemed to make Firefox snappier on this ATI-carded machine (desktop.) 

Let's see how long this lasts. 


Oli.

---

### Post by ujecrh on 2009-08-23
> **pawhtiobo said:**
> Hi :)

I also got a D600, your ATI does the 1440X1050 screen resolution?

Yes and that resolution works fine with Jaunty. Most of the time I have a monitor plugged-in and use 1600x1200 though.

---

### Post by pawhtiobo on 2009-08-24
Hi :)

Are you able to swich resolution? by defult mine starts at 1440X1050 and if try to change to a lower resolution the screen goes black... as it happens to a lot of users who have that "cursed" Radeon 9000 (RV250)...


see ya...

---

### Post by ujecrh on 2009-09-03
> **pawhtiobo said:**
> Hi :)

Are you able to swich resolution? by defult mine starts at 1440X1050 and if try to change to a lower resolution the screen goes black... as it happens to a lot of users who have that "cursed" Radeon 9000 (RV250)...


see ya...

Yes I can switch resolutions fine (on the external screen, I never use the laptop screen).

---

