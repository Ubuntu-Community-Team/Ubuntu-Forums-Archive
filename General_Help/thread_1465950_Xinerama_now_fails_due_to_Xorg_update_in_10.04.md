---
title: "Xinerama now fails due to Xorg update in 10.04"
date: 2010-04-29
forum: General Help
---

### Post by Samual on 2010-04-29
I have 3 monitors across 2 video cards, thusly I must use Xinerama (And xserver-xgl for compiz of course, but that's another story and regardless of this issue) in order to combine all three monitors into one large session.

The issue is that, on 10.04 due to an update to xorg which has a regression, moving my mouse across to the left monitor causes it to flicker back and forth between the left and center monitor (While also freezing the rest of the display), and it eventually crashes xorg shortly after. This bug has been reported ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/563100](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/563100)) and has been open since Ubuntu 10.04 alpha, but perhaps there is some workaround here as this is a make-or-break thing for me. If I can't get this working, it's back to Windows... Help me, please, help me. :P

I couldn't figure out a way to downgrade xorg for this to work, nor do I know if that's safe... I was wondering if anyone has a fix for this, thanks.

---

### Post by Samual on 2010-04-29
No one can help?...

---

### Post by Samual on 2010-04-30
After searching for quite a while, still all I can find is a workaround that doesn't even work! Anyone? Come on, no one has any ideas at all?

---

### Post by cerealthesecond on 2010-04-30
i have the same problem, would be cool to have a fix

---

### Post by transistor_fet on 2010-05-02
I also have the same problem.  The problem only occurs when a screen of a higher ID is left of a screen with a lower ID.  It is possible to set the left screen as screen 0 (which may require physically changing your monitor connections) and then set the other 2 screens as being right of the left screen.  It's a little annoying since the left screen will be the default screen but at least it kinda works. =P

---

### Post by shock32638 on 2010-05-03
It also affects if you have a higher numbered monitor above a lower one. I had to re-plug my 2x2 monitors from this:
[FONT=Fixedsys]2.0 | 2.1
---------
0.0  | 0.1[/FONT]

[FONT=Fixedsys]to this:
0.0 | 0.1
---------
2.0 | 2.1[/FONT]

where the first digit is the video card identifier, and the second number is the monitor identifier (my video card Identified as 1 is onboard, and not in use)

Also check out this thread for some additional suggestions
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/563100](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/563100)

---

### Post by johansson.seb on 2010-05-08
From [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100"):

> According to the Xorg people working with the bug, in Xinerama mode - event coordinates are relative to the primary secreen - Screen 0. But, in the version of Xorg that now is in use with Lucid (1.7.6) event coordinates are unsigned integers.

With unsigned integers, negative coordinates can not be represented, thus xorg can not function with screens above or to the left of Screen 0. So, if you can, let your upper-left screen be Screen 0.

The xorg people have a patch that seems to be working (simply changing back to signed ints). I hope that this will make it into an updated ubuntu Lucid package soon.

---

### Post by Samual on 2010-05-18
Alright everyone, I managed to get Xinerama working again just fine by setting my left monitor as screen0. Only problem now is trying to get xserver-xgl to work with gnome.

Also: Just so you know, you don't have to swap the monitors physically, you can do it by changing the port used on the video card in xorg.conf.

---

### Post by tuckerh on 2010-06-01
I got things working as described by switching the screen numbers, but I had issues getting my gnome panels on the righthand monitor.

I was able to accomplish this by changing the monitor value from 0 to 1 in gconf-editor under /appa/panel/toplevels/[bottom/top]_panel_screen0

---

