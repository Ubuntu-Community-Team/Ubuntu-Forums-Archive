---
title: "Windows automatically jumping between workspaces"
date: 2012-04-19
forum: General Help
---

### Post by josephellengar on 2012-04-19
I'm currently running Ubuntu 12.04, Gnome Fallback and I have this weird problem. Whenever I move a window around from the titlebar, it will jerk to a different place on the screen, or sometimes switch workspaces altogether. Sometimes I spend a while just trying to hunt down where the window went. I feel like it might be an overzealous Compiz setting, but I can't quite figure out what the problem is. Any suggestions?

Thanks!

---

### Post by Gunnersrock on 2012-05-03
It seems that I have the exact same issue.  In addition for me, whenever I move a window off a screen (for example, half of the window is in one desktop, half in another) it snaps back to the side of the desktop I'm currently working on, so I can't switch windows between desktops using that method anymore.  The only thing I have turned on in compiz other than the default is wobbly windows, which turns off snapping windows, and the water/raindrops effects.

---

### Post by josephellengar on 2012-05-10
Bump. The problem is still around. Just moving a window partway off of a workspace (for example to get it out of the way) will cause it to either jump all the way to the next workspace or to return to its original position. Window management is really a pita in 12.04. Anybody know of a solution?

---

### Post by hansdown on 2012-05-10
This is interesting.

I wouldn't blame compiz, just yet.

I was working with linux mint moments ago, and had a very similar problem.

I had switched windows, and was no longer able to go back to the first window.

Not enough data to find any commonality, yet.

Anyone else experiencing odd window switcher problems?

---

### Post by Gunnersrock on 2012-05-12
So I spent some time looking into this, since the problem did not seem to exist in the "Gnome Classic (without effects)" option in the login menu.  Because I'm fairly sure this option is just gnome-fallback without Compiz, I started trying out each of the Compiz settings I had activated.  Turns out that switching off the "Pull Windows" option in Window Management fixed the problem for me.  I don't know if this option will work for everyone, but it fixed it for me.  Hope this helps.

---

### Post by josephellengar on 2012-05-12
> **Gunnersrock said:**
> So I spent some time looking into this, since the problem did not seem to exist in the "Gnome Classic (without effects)" option in the login menu.  Because I'm fairly sure this option is just gnome-fallback without Compiz, I started trying out each of the Compiz settings I had activated.  Turns out that switching off the "Pull Windows" option in Window Management fixed the problem for me.  I don't know if this option will work for everyone, but it fixed it for me.  Hope this helps.

Where is this option? I don't have any plugin named pull windows and all of the plugins that have options named pull windows are disabled. Was this in CCSM?

---

### Post by josephellengar on 2012-05-12
> **josephellengar said:**
> Where is this option? I don't have any plugin named pull windows and all of the plugins that have options named pull windows are disabled. Was this in CCSM?

It's place windows, not pull windows. But without place windows, windows get placed under the gnome bar and in other very inconvenient places. Do you know of a workaround for that?

---

### Post by Gunnersrock on 2012-05-12
> **josephellengar said:**
> It's place windows, not pull windows. But without place windows, windows get placed under the gnome bar and in other very inconvenient places. Do you know of a workaround for that?

That's correct, it's place windows, sorry about that.  As to a workaround, I don't know of one.  When I launch a window, the top bar (with the close, resize, and minimize options) is usually about halfway under my panel at the top of the screen.  I can move the window down without any trouble, but it is an inconvenience.

---

### Post by pmawhorter on 2012-05-15
Just jumping on to add more confirmation. Found this thread via Google after experiencing the same problem (also for me sometimes moving a window from one workspace to another with ctrl-alt-left/right would mysteriously move an unrelated window in a completely different workspace as well). I'm also using gnome-fallback with compiz enabled. After unsetting "place windows" in CCSM, the poltergeist has stopped moving my windows, but just like Gunnersrock windows wind up submerged in the top bar when launched.

Thanks for spending the time to track down that setting! Here's hoping that this gets fixed...

---

### Post by robbied on 2012-05-17
First off, thanks for making this post and getting the "trouble shooting" started but this was SO easy to fix... after reading here. :)


The setting is in place windows.  Leave it on so you don't get the annoying behavior mentioned above.  What you change is the "Multiple Output Mode".  Set it to "Place across all outputs."

This worked for me, hope it works for you too!

---

### Post by nathan726 on 2012-05-24
Unchecking "Workarounds" in the Place Windows options seems to have fixed it for me.

---

### Post by roselina366 on 2012-05-24
Sorry I have no suggestion for your problem.Because i don't use ubuntu 12.0 software.Would any body tell me what ubuntu 12.0 software n what its uses?

---

### Post by billthehill on 2012-06-09
Unfortunately neither "trick" (selecting multiple outputs or disabling workarounds in window placement settings) worked for me. 
Any help on this issue would be very welcome since this window snapping back to workspace is really really annoying...

---

### Post by Fevrin on 2012-09-01
I suffer from the same issue in Ubuntu 12.04 using the Gnome 3 emulation of Gnome 2 (I'm guessing that's the gnome-fallback).  I have two displays, one 1680x1050 and the other 1366x768Any, and any time I open a new window and attempt to move it across displays or even to a different position on the same display, it seems compiz has a favorite spot and is too stubborn to allow me to permanently move the window.  I can technically move the window, but within a second or two of me doing so, the window jumps back to compiz's favorite position, even if I'm still in the process of dragging the window.  The favorite spot can also change from being located on the display in which I opened the window to the other display.  This sometimes happens when I attempt to move the window to the second display and back to the original display, at which point the window may stick around on the second display.

I've tried all of the proposed CCSM solutions in this thread, and none of them worked.  I tried unchecking the workaround checkbox and tested the various options for the placement mode and multi output mode, and none of them corrected the issue for me.  I ended up just disabling the Place Windows plugin, and now the issue is gone.  So it seems that the issue is directly tied to the Place Windows plugin, at least in my case.  I do not have the issue that others have described in which opening windows can place them inconveniently without the Place Windows plugin enabled, so I think I'm all good (for now).

---

### Post by pqwoerituytrueiwoq on 2012-09-01
unticking lazy positioning in move helps but not perfect

---

