---
title: "Strange issue"
date: 2010-08-14
forum: General Help
---

### Post by dmbraley on 2010-08-14
Hey all, pretty new Ubuntu user and I like what I have seen of it so far, its a nice bridge between harder to use releases and Windows, which is really for idiots like me....

Anyway my issue:

I had been having random crashes/reboots/hang on POST, so I replaced the RAM and it seemed at first to have fixed my problem. A few hours ago I left the computer idle and I noticed that when the screensaver came on the screen went from the image to immediately black, the power light stayed on on my tower but the computer was completely non responsive to the mouse, keyboard etc. The only think I could do was a hard reset, when I did this the Ubuntu screen(the one that says Ubuntu and has the red dots) came up right before the computer turned off. My first thought was hmm thats odd, let me go change the screen saver and/or the time before it comes on. Now any time I access the System>Preferences>Screensaver menu the same crash happens within seconds of the window opening. The screen saver Im using is ant flashlight if it makes a difference. I cant change it because I don't have enough time before the crash, any ideas? Thanks guys!

---

### Post by dmbraley on 2010-08-15
actually I found a solution I had to access the terminal and run gconf-editor and then go to the gnome-screensaver folder and disable the ant spotlight screen saver, now when I access the screen saver menu it doesn't crash. Thanks guys!

---

