---
title: "Trouble with Ubuntu Splash Screen"
date: 2009-09-14
forum: General Help
---

### Post by JugglinPhil on 2009-09-14
Hi guys, once more I need some help. Thing is I am using the whole Mac4Lin thing to make my Ubuntu look like a Mac, and I really like it. Everything works fine, except the usplash theme. I tried activating it with the install script and Startup Manager, neither of which worked. Then I read somewhere that usplash never really does what it is supposed to, removed it and installed splashy using this tutorial: 
[http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/](http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/). However when I test it (using "splashy test") I get following error: 
Splashy ERROR: libsplashy: Framebuffer is not configured properly please see [http://tinyurl.com/339h67](http://tinyurl.com/339h67)
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
Following the URL it says I have to add 'vga=791' at some point in the menu.lst, but I already did so following the instructions. When I boot up now, I get the error:
Splashy ERROR: Connection Refused
No idea how to fix it, so I removed splashy again. Problem  now: I probably could live with no Splash, but now it always boots with the verbose option and tells me everything it is doing, which I really don't like. 
So can anyone help me to stop my system booting in verbose mode and/or fix my Splash problems? Greetings, JP

---

### Post by JugglinPhil on 2009-09-19
Okay never mind, reinstalled Ubuntu...

---

### Post by pickarooney on 2009-09-20
Pity... I have the same issue. Splashy didn't work very well, so I Tried to go back to usplash, but the boot sequence keeps insisting on trying to load the now missing splashy and then goes into verbose mode.

---

### Post by JugglinPhil on 2009-09-20
Hey glad to hear I wasn't the only one having trouble with it. It can get pretty annoying, I know, but after a while I got another problem: [http://ubuntuforums.org/showthread.php?t=1266977](http://ubuntuforums.org/showthread.php?t=1266977) which I wasn't able to solve, so I dedided to go for a new install. I hope somebody's gonna help you out because I haven't got a clue, good luck.

---

### Post by trungd_t on 2009-11-09
I haven't tried this yet, but you may want to try to see if it helps.

[http://ubuntuforums.org/archive/index.php/t-1054382.html](http://ubuntuforums.org/archive/index.php/t-1054382.html)

Good luck and let us know how it goes.

---

