---
title: "GUI won't show up"
date: 2011-07-17
forum: General Help
---

### Post by eatinpaper on 2011-07-17
After installing some updates and restarting my computer, the GUI will not load. Instead of the GUI, I see a stream of text that I'm pretty sure relates to the GUI. I'm able to go to the other six terminal tabs normally. From there, I've tried to use startx to get my GUI working, but to no avail-I get more error messages. I also tried some of the suggestions in this forum thread: [http://ubuntuforums.org/showthread.php?t=1594480](http://ubuntuforums.org/showthread.php?t=1594480) (I believe that this person and I have similar problems hence why I sought help from this thread.)
When trying to edit my xorg.conf file, I discovered that, unless I was reading the screen wrong, there is no xorg.conf file. However, there is one normal xorg.conf-backup file and another xorg.conf-backup file with a long string of numbers after it. The first file is only 6 lines long and the other file is over 50 lines long. 
I would try to play around with these files and fix this on my own, but I've only been using Linux for all of two days, so I don't really trust myself to completely destroy my Linux install (as I seem to have done so already). So any help with this is greatly appreciated!

Edit: Here's an image of the text that pops up when I try executing startx. 
[http://i52.tinypic.com/339n0p3.jpg](http://i52.tinypic.com/339n0p3.jpg)

---

### Post by oldos2er on 2011-07-17
Which version of Ubuntu are you using, and which model Nvidia card? Can you boot into recovery mode? If so, drop to a root shell with networking, and run **apt-get update && apt-get install nvidia-current**

It's normal not to have an /etc/X11/xorg.conf file; newer versions of X don't require it.

---

### Post by eatinpaper on 2011-07-17
Thank you! That at least got my GUI to boot, but now there's a new problem. It says something along the lines of "you do not have the hardware to boot unity," which is probably why I'm in a low graphics mode at the moment. 

> Which version of Ubuntu are you using, and which model Nvidia card?I'm using 11.04 and I have an 8800 GTS Nvidia graphics card.

Edit: Woah, something new and REALLY weird is that now that I have a working GUI, I can't access a terminal via alt+tab+any of the first six number keys. My monitor just reads: Input signal out of range.

Edit 2: Everything is fine now (I think). So for anyone who reads this and has the same problem as I did: I went to System-> Additional Hardware -> From there, I changed my active driver from Nvidia Accelerated Graphics Driver (version 173) to Nvidia Accelerated Graphics Driver (version current).

---

### Post by oldos2er on 2011-07-17
Glad you got it going.

---

