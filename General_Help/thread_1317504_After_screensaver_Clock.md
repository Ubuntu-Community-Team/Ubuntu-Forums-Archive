---
title: "After screensaver Clock"
date: 2009-11-06
forum: General Help
---

### Post by loseby on 2009-11-06
Am after a easy to install screensaver Clock ie. the screensave displays a clock

---

### Post by 5BallJuggler on 2009-11-06
> **losbey said:**
> Am after a easy to install screensaver Clock ie. the screensave displays a clock

have you tried the GLtext screensaver, you may be able to change the data in it by altering usr/share.xscreensavers/config/GLText,xml

there is an option line, the 1st being "uname" and the second being "clock"

i've not figured it out yet, but it may be a place to start.

Phil

---

### Post by PetteriP on 2009-12-05
Hi,

I found this somewhere, it is the gltext screensaver modification:
Go to your /usr/share/applications/screensavers/ directory and just in case make a copy of the gltext.desktop
Print out the screensaver file:
more /usr/share/applications/screensavers/gltext.desktop
See the row with text:
Exec=gltext -root
Use some editor to change that line to:
Exec=gltext -root -front -text '%l:%M:%S %p'
I used VI:
sudo vi gltext.desktop
[http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html) 

That should do it.

The instruction was in fact from this same forum...
[http://ubuntuforums.org/showthread.php?t=266124](http://ubuntuforums.org/showthread.php?t=266124)

I have one question though:
How to make the clock show 24 hour time? With above parameters the clock shows 12 hour time. I know it is the first parameter "%l" but what to put there? "%L", "%ll" or "%LL" didn't work.

---

### Post by 5BallJuggler on 2009-12-06
> **PetteriP said:**
> Hi,

I have one question though:
How to make the clock show 24 hour time? With above parameters the clock shows 12 hour time. I know it is the first parameter "%l" but what to put there? "%L", "%ll" or "%LL" didn't work.

Use the %H instead of %I 

that'll work.

---

### Post by PetteriP on 2009-12-06
Thanks!

Next to find nice analog clock screensaver...

---

