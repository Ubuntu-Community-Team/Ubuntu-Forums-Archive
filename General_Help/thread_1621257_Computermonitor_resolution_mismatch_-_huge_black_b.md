---
title: "Computer/monitor resolution mismatch - huge black border on screen?"
date: 2010-11-14
forum: General Help
---

### Post by dabbi2000 on 2010-11-14
Please can anyone at least get me along with debugging this problem..

On a 6-7 years old Compaq laptop, connected to a brand new HP monitor I am having a mismatch with computer/monitor resolution.

Before I had Ubuntu 10.04 which could only run in X's safe graphics mode - allowing for full screen resolution but with handicapped graphics - for example Youtube fullscreen would be quirky and run with CPU at 100%, something which was no problem before 10.04.

Then I tried Ubuntu 10.10 and later Lubuntu 10.10 (which had exactly the same problem); the monitor is running 1440x900 while the computer is rendering to only 1024x768 - leaving a huge black border on right and bottom of screen. The gfx is still crippled; Youtube fullscreen is quirky as before.



I have no idea where to start debugging this, searching the forums and Google leads me to lots of tries and tests which I've had no success with. Anyone?

---

### Post by wt8008 on 2010-11-17
Hello

Please describe the graphics card that is in your laptop.

Thanks

---

### Post by superzanti on 2010-11-17
Ah!

I can help you.

[http://ubuntuforums.org/showthread.php?t=1618573](http://ubuntuforums.org/showthread.php?t=1618573)

Check it out. It'll be a good fix, but it's not a solution.

---

### Post by dabbi2000 on 2010-11-29
thanx superzanti,
before I tried out your solution I did a 
 X -configure

from a "safe mode" boot up (command line, without X server running) and copied the newly created xorg.config.new file to /etc/X11/xorg.config

and voila!

---

