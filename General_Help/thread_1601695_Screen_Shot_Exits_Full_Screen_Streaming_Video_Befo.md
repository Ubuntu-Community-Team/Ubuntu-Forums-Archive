---
title: "Screen Shot Exits Full Screen Streaming Video Before Capture"
date: 2010-10-20
forum: General Help
---

### Post by IceDoE on 2010-10-20
In Ubuntu 10.04, when playing a video in full screen from Vimeo, if I hit "Prnt Scrn" to get a screen shot, the application first exists the full screen view and then captures the screen, making it impossible to take a screen shot of just the full screen video. I found that if I pause the video before taking the screen shot, it will properly capture first before exiting. On youtube, however, pausing did not help either. 

I've found that on Ubuntu Netbook Edition 10.04 pausing the video in Vimeo does not work, it still exits before capturing the shot. 

Capturing while playing video in Movie Player or VLC full screen works properly, while the video plays or while paused. I have not had a chance to test this in UNE, however.

Is this a bug, or is there a delay setting I can change?

---

### Post by 3Miro on 2010-10-20
I have seen similar thing. When I am watching YouTube videos in full screen and I press the multimedia keys on my keyboard to lower/raise the volume, I am forced out of full screen.

This happens in Ubuntu, Arch and Gentoo, Gnome and XFCE, 32-bit and 64-bit, using compiz, xfwm4, openBox or matacity, browsing with firefox or chromium. Basically, this is an issue with closed source, proprietary software from Adobe that they don't think is important enough to fix and they will not let us fix.

You can run YouTube videos in Totem (the Movie Player) either streaming or by downloading them form YouTube first. Full screen will work from there.

---

### Post by IceDoE on 2010-10-21
Thats a good workaround. Though now I have to tell some people I do support for that they need to add in a few steps, which is never ideal. 

That flash is the problem makes some sense, however this doesn't explain why I could capture Vimeo when Vimeo is paused on one machine and not the other. All I can think of is speed of capture: the machine that could do it is more powerful, and paused uses less resources than video, so capture was able to work faster (while exit was not?). I don't know, seems a bit odd there.

---

