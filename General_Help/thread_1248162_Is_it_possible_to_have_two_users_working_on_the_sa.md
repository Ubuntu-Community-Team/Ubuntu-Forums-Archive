---
title: "Is it possible to have two users working on the same computer at the same time?"
date: 2009-08-23
forum: General Help
---

### Post by beattyml1 on 2009-08-23
Scenario:
User A is logged in and using xbmc  with a remote displayed on a tv connected to the computer, he is watching a movie

User B wants to use the computer but does not need the remote or the tv, he wants to use the mouse, keyboard, and monitor

is there any way that User B can do what he wants with out disturbing what User A is doing (interrupting playback or remote functionality)

---

### Post by Slim Odds on 2009-08-23
Yes, linux is a multiuser system.

---

### Post by beattyml1 on 2009-08-23
I guess I knew it was theoretically possible, but the question is it attainable using ubuntu without me having to write my own programs, and assuming it is:

HOW?

---

### Post by Slim Odds on 2009-08-23
Connect over a network with X, ssh, VNC, etc.

---

### Post by Baneblade on 2009-08-23
Yes it is even possible to have a single user running multiple sessions!
I like to do this when im working on my home machine remotely from my laptop using Freenx, as then i dont get compiz and my themes slowing things down over what is usually a poor, borrowed wireless signal.

---

### Post by hansdown on 2009-08-23
> **beattyml1 said:**
> I guess I knew it was theoretically possible, but the question is it attainable using ubuntu without me having to write my own programs, and assuming it is:

HOW?

Hi beattyml1.

In the bottom, right-hand corner of the screen, is the desktop switcher.

You can watch your movie, and your friend can switch desktops to do anything he/she wishes.

---

### Post by tgalati4 on 2009-08-23
You can plug in as many keyboards and mice as you have usb/ps2 ports for.  There are applications that allow splitting the desktop as well as multiple monitors (say 4 as a practical limit 2 x dual video cards).  

Only your imagination and clock speed limit what you can do.

First get xrandr working properly.  Search the forums.  Not sure what the xbox's capabilities are.

You want to set up two screens:  the TV and the monitor, each with its own desktop.

Start a movie on the TV, run it full screen.  Go to the monitor and bring up firefox and do some browsing.  See if you get any stutters or performance hits.  If you do, then you will need to do some tweaks to keep the movie playback smooth.

man nice

---

