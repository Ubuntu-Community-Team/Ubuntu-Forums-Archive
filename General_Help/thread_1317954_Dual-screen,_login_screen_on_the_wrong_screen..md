---
title: "Dual-screen, login screen on the wrong screen."
date: 2009-11-07
forum: General Help
---

### Post by qualtch on 2009-11-07
Hello all,

I'm using Ubuntu Karmic 9.10 with dual-screen and I noticed an interesting problem: every time I boot the login screen appears to the secondary display. I tried switching the cables from the back of the computer but it still appears on the wrong screen! (That time it's the main screen so supposedly). I have two displays next to each other. The left one is the main display and the right one is the secondary. When the left one is set as main display, the login screen appears to the secondary monitor. When the right display is set as the main display, the login screen appears to the right display again!

Why the login screen continues to appear on the wrong display?

---

### Post by Leonivek on 2009-11-07
I'm having the exact same problem.

---

### Post by secular on 2009-11-08
Same problem here. 

I'm usually pretty good at troubleshooting dual monitor problems, but this one has me stumped.

---

### Post by secular on 2009-11-09
I solved my problem, but I can't fully explain how.

I opened my xorg.conf file and saw that my second monitor was not listed. I found my old xorg.conf file here on ubuntuforums, copied the monitor section for my second monitor, and pasted it into my current xorg.conf. 

Problem solved for me!

Edit: It's not really solved: I discovered that I quite accidentally moved the login to the right monitor. 

It turns out that my wiggling my mouse the the left during login will move the login to the primary monitor, which is on the left. 

I later found this behavior online somewhere after I noticed that the login had moved back to the right-side monitor, which is the secondary monitor.

I guess I'm still looking for an actual fix, rather than what I've found so far.

---

