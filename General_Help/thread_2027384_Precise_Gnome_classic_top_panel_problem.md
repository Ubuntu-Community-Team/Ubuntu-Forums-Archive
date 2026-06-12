---
title: "Precise Gnome classic top panel problem"
date: 2012-07-16
forum: General Help
---

### Post by Cavsfan on 2012-07-16
The problem is that when in Gnome Classic I open any window, the top of that window is under the top panel and in order to do anything 
with it I have to first press ALT and click on it to bring it down.
I have heard this was an initial bug that was corrected before Precise was released
Also in Gnome Classic it forces me to press ALT+Super+right click on the top panel to do anything with it. 
I have been told I should just have to press ALT+Right click.


Not sure what to do to fix this and if anyone has any idea I would much appreciate it!

---

### Post by Cavsfan on 2012-07-16
The bottom of windows like Firefox also go below the bottom panel too. I don't think that is supposed to work that way either.
So, it is both the top and bottom panels that allow my windows to go behind them.

---

### Post by CharlesA on 2012-07-16
Title changed per OP.

---

### Post by Cavsfan on 2012-07-16
Thank you! :)

---

### Post by OM55 on 2012-07-16
> **Cavsfan said:**
> The problem is that when in Gnome Classic I open any window, the top of that window is under the top panel and in order to do anything 
with it I have to first press ALT and click on it to bring it down.
I have heard this was an initial bug that was corrected before Precise was released
Also in Gnome Classic it forces me to press ALT+Super+right click on the top panel to do anything with it. 
I have been told I should just have to press ALT+Right click.


Not sure what to do to fix this and if anyone has any idea I would much appreciate it!

Regarding the ALT+Super key+Right click on the top/bottom panel - that's how Gnome Classic menu works in Ubuntu 12.04. So it is not a bug but a feature. We can argue if the addition of the Super key to the key sequence it was really needed... but regardless, that's how it works now.

As for the window being hidden below the panels - I assume you selected to auto-hide your panels, right? As a resuls the size of the viewable screen is the entire visible area, including the panels. Since the panels are "always on top", if a window is occupying the same area as the panel when the panel is visible, the panel will cover it until a key-press or mouse click outside the panel wilk hide the panel.
However, it could also be a video driver issue. Make sure that your video driver is working properly. You can also try to instal CompizConfig and adjust the settings. If there is no effect it is very likely that your video driver is not working and you are in basic video mode - hense the display issue.

---

### Post by Cavsfan on 2012-07-16
> **OM55 said:**
> Regarding the ALT+Super key+Right click on the top/bottom panel - that's how Gnome Classic menu works in Ubuntu 12.04. So it is not a bug but a feature. We can argue if the addition of the Super key to the key sequence it was really needed... but regardless, that's how it works now.

As for the window being hidden below the panels - I assume you selected to auto-hide your panels, right? As a resuls the size of the viewable screen is the entire visible area, including the panels. Since the panels are "always on top", if a window is occupying the same area as the panel when the panel is visible, the panel will cover it until a key-press or mouse click outside the panel wilk hide the panel.
However, it could also be a video driver issue. Make sure that your video driver is working properly. You can also try to instal CompizConfig and adjust the settings. If there is no effect it is very likely that your video driver is not working and you are in basic video mode - hense the display issue.

I was told that ALT+Right Click is supposed to work and that ALT+Super+Right Click was changed to ALT+Right Click before RC. 

See this:

[http://ubuntuforums.org/showpost.php?p=12102683&postcount=105](http://ubuntuforums.org/showpost.php?p=12102683&postcount=105)

Also, the problem I am having is not normal. I posted this on the Precise known bugs and workarounds thread and 
was told to open my own thread as this is none of that.

See this:

[http://ubuntuforums.org/showpost.php?p=12099986&postcount=101](http://ubuntuforums.org/showpost.php?p=12099986&postcount=101)

I have Lucid still installed and it never let windows go behind the panels.
This setup will allow the windows (any) to go behind both the top and the bottom panels.

---

### Post by Cavsfan on 2012-07-16
I have Nvidia driver 295.49 installed from installation and have not messed with it. I also have CCSM installed,
Cairo Dock with open gl and all the niceties and it all runs fine.
I don't think the driver is the problem. I have seen no problems related to it.

---

### Post by Cavsfan on 2012-07-17
I'm on Lucid now and no windows e.g Firefox will go behind the top panel but, they will slip below the bottom panel.
But, once it is set to open in between the two panels, it will do so when subsequently opened and closed to the exact same place.
In Precise, any window e.g. Firefox will open flush against the top of the screen behind the top panel.
And every close and open after that will open in the exact same place requiring pressing ALT+ right mouse click to pull it down. 
One would think it would act like Lucid in that once it is set to a certain spot, it would open in that spot.

---

### Post by Cavsfan on 2012-07-17
Received some updates today and one was gnome-panel. Installed and rebooted.
Now, a window will open under the top panel but, once brought below it, it will not go behind it.
Some improvement.

---

### Post by Cavsfan on 2012-07-19
I think I have it corrected. I did a fresh DL of a 12.04 64 bit ISO and did a clean install. (sigh)
Then after *much* time trying to get it back like it was, I just happened to see in CCSM Window Rules.
I enabled it and beside **Below** I entered **top_panel** and that seems to prevent windows from opening underneath the top panel in gnome class.
I just took a wild guess at top_panel but, it seems to work after restarting.

I will give it a few days and if all stays fixed, I will resolve this thread.

:popcorn:

Using Ubuntu is easy, administering it is sometimes pure heck! There are so many possibilities and places things can be hidden. 
The simplest thing can cause major head aches. But, it is still better than any other system I have found yet.

---

### Post by Cavsfan on 2012-07-23
Almost as soon as I marked this thread solved the problem re-appeared.
It acts like the top panel is not there. Everything opens flush with the top of the screen instead of flush with the bottom of the top panel. :evil:

It is probably a CCSM issue as it reset all the options when it started happening again.

---

### Post by Cavsfan on 2012-07-23
It fixed itself again but, something is very finicky.

---

