---
title: "Natty external (dual) monitor - major problems"
date: 2011-04-28
forum: General Help
---

### Post by andrei_1 on 2011-04-28
Anyone else pained by the multiple monitor support in Natty?

It seems to me so buggy that I reckon a bug report should only include "just plug it in and see". Not trying to be ironic or something, just very annoyed and disappointed.

Is this tracked somewhere? A bug report already opened in Launchpad?

---

### Post by Blasphemist on 2011-04-28
I'm using dual monitors on natty, my laptop internal and an external, and I did have some issues. What is/are your issue or issues? I had to install compiz settings manager and multiple displays from the software manager but it is up and working now.

---

### Post by dale11 on 2011-04-28
Blasphemist,

What is that little app your running on the very right that shows like your system info?

---

### Post by Blasphemist on 2011-04-28
SysmonitorScreenlet v0.1.4

---

### Post by dale11 on 2011-04-28
> **Blasphemist said:**
> SysmonitorScreenlet v0.1.4


Thanks!

---

### Post by andrei_1 on 2011-04-28
> **Blasphemist said:**
> I'm using dual monitors on natty, my laptop internal and an external, and I did have some issues. What is/are your issue or issues? I had to install compiz settings manager and multiple displays from the software manager but it is up and working now.

Well, I don't even know where to begin. A summary:

* Most of the time, it will ignore the default-monitor setting and will keep the Unity Bar on the laptop's screen instead of the default external monitor

* After restart, the login window is on the laptop's screen (which is usually closed down); sometimes pressing enter brings the window to the default external monitor sometimes not

* Sometimes after a restart the external monitor will contain garbage / random noise

I can't even get a consistent behaviour out of the system, because apparently there are so many bugs at so many different levels that you don't even know what caused the latest strange / inconsistent behaviour.

The system is a fairly recent i3 powered laptop clocked at 2.53 GHz. The video card is Intel GMA HD. It generally worked fine in Maverick - it had some minor quirks, but at least the behaviour was very consistent.

---

### Post by Blasphemist on 2011-04-28
I worked with someone a good while back on using the external as the default and somehow it was solved but I don't remember how. Both of us used both monitors and neither of us had garbage on either monitor. My issues were with different resolutions and the other person it was mainly the default monitor issue and nvidia drivers I think. You can search for that thread.

---

### Post by geometrikal on 2011-04-28
I'm having the same problem -  the unity launcher is on the wrong monitor and I cannot work out how to change it..... grrrrr... is there some setting to chang evia gconf-editor or the like?

---

### Post by geometrikal on 2011-04-28
ahhhhh i have the solution

open terminal and type xrandr

should see something like this:
```

Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

which ever one you want to be primary monitor type something like this, changing DVI1 to whatever monitor you have:

xrandr --output DVI1 --primary

---

### Post by andrei_1 on 2011-04-28
> **geometrikal said:**
> ahhhhh i have the solution

open terminal and type xrandr

should see something like this:
```

Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

which ever one you want to be primary monitor type something like this, changing DVI1 to whatever monitor you have:

xrandr --output DVI1 --primary

OK, things have now somewhat stabilized to a state I can live with.

First of all I fixed the garbage on the external monitor by emptying the contents of .config/monitors.xml which for some reason got corrupted (Ubuntu bugs coupled with my many attempts at fixing this in the "Monitors" settings window).

Second of all, your xrandr command successfully moves the Unity Bar to the external monitor (probably by successfully setting it as the primary display). The caveat is that I have to run this command after every restart / log-in. For this reason, I have created some Gnome keyboard shortcuts for the two monitors (internal & external): Ctrl-Super-v and Ctrl-Super-b (yes, I changed the Unity activator key(s) first from Super to Alt-Super).

Also, when logging in, the log-in window is on the internal (closed down) monitor. I can move it to the external monitor by first moving the cursor to the external monitor, and then pressing enter (which selects the first user and moves the window to the external monitor).

Hopefully, the Ubuntu team will fix this so that the xrandr workaround will not be required anymore.

---

### Post by geometrikal on 2011-04-30
> **andrei_1 said:**
> Also, when logging in, the log-in window is on the internal (closed down) monitor. I can move it to the external monitor by first moving the cursor to the external monitor, and then pressing enter (which selects the first user and moves the window to the external monitor).

Hopefully, the Ubuntu team will fix this so that the xrandr workaround will not be required anymore.

Yes I still have it on the other screen on login as well. Perhpas there is a better way to set the default monitor... I would like to see a few more options for configuring unity.

---

### Post by emont on 2011-05-04
Thank you Geometrikal!

Saved me a lot of angst looking for a non-existant xorg.conf.

---

### Post by geoffm on 2011-05-16
Anyone experienced display failures when switching from 2 monitors to 1?
It's all black with only the cursor showing. Doing [Fn] [CRT/LCD] doesn't do a thing, nor do [Ctrl] [Alt] [Del] nor [Ctrl] [Alt] [Backspace]

All I can do is a hard shutdown by holding the power button for several seconds. Of course I loose everything that is opened and have to wait for the whole thing to boot again. 

This is with gnome 2 ("classic" session).

It seems natty has some new way of detecting monitors because before, I had to do "Detect monitors" or [Fn] [CRT/LCD] to switch the system from 1 monitor to 2 monitors after I plug the external monitor in (or vice-versa when I unplug it). Now there's an update as soon as I plug it in. I don't know about a fix, though.

I just installed gnome3 and will see how it goes instead.

---

### Post by ziltoidto on 2011-05-26
I've also had a heap of problems with dual monitor. Reported a couple of the more obvious bugs, but some seem to just come and go (so it's hard to tell what lead to them).

Basically, dual monitor is just broken... You can just about (and I have) hack it together to make it work (almost) satisfactorily. Though there seems to be some major oversights in development in this area. - Before upgrade, my system was perfect. Best plan is to not upgrade until this is sorted (I may downgrade so I can start getting some work done again :) )

---

### Post by Blasphemist on 2011-05-26
> **ziltoidto said:**
> I've also had a heap of problems with dual monitor. Reported a couple of the more obvious bugs, but some seem to just come and go (so it's hard to tell what lead to them).

Basically, dual monitor is just broken... You can just about (and I have) hack it together to make it work (almost) satisfactorily. Though there seems to be some major oversights in development in this area. - Before upgrade, my system was perfect. Best plan is to not upgrade until this is sorted (I may downgrade so I can start getting some work done again :) )

I don't know what your issues are but there are a lot of us using 2 monitors. If you post your issues, help is likely available. You should start a new thread since this is marked solved.

---

### Post by dFlyer on 2011-05-26
> **andrei_1 said:**
> Anyone else pained by the multiple monitor support in Natty?

It seems to me so buggy that I reckon a bug report should only include "just plug it in and see". Not trying to be ironic or something, just very annoyed and disappointed.

Is this tracked somewhere? A bug report already opened in Launchpad?

PPA for sure. Sounds like a **** poor attitude. State your problems and someone will help. File a bug report. Learn to search and maybe you will learn something. Oh ya I have no problems here with dual monitors.

---

### Post by geoffm on 2011-06-05
> **ziltoidto said:**
> Best plan is to not upgrade until this is sorted

Sounds like a great plan, except for how do you know when this is sorted? It seems dual monitor works on some machines, doesn't work at all on some others, and others just have very specific bugs (like black screen when unpluging secondary monitor in my case). If someone waits before upgrading, how could they know the bugs have been fixed?

---

### Post by knowmad on 2011-06-23
I'm seeing the same behavior as geoffm with an all black external display. Just today, I'm seeing a black band about 150px high appearing on my laptop monitor. So far, best thing I've done is not plug in the monitor cable until after the laptop is booted/restored then turning on the ext. monitor. That seems to work. Oh, I also have to manually turn off the monitor when shutting down or leaving for the night.

---

