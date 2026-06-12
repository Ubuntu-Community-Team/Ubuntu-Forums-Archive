---
title: "VNC into second monitor. Possible?"
date: 2012-02-28
forum: General Help
---

### Post by thehighpander on 2012-02-28
I am running Lubuntu 10.10. I have dual monitors set up on my nvidia 9800gt, via th seperate X server method. I have my primary monitor at my workstation in my bedroom, and the other is my flatscreen in my living room, via a 20 ft component cable. 

I would like some way to view the secondary screen in a window on my main monitor.  I thought perhaps, seeing as it is a seperate x-session, it might be possible to vnc into it, but when I try, 

```
DISPLAY=:0.1 x11vnc
```
```
directvnc localhost:0.1
```

All I get is a massively distorted screen, which may or may not be my other monitor.

Any thoughts/other possible solutions to this?

I have been using Linux(mostly Debian/Ubuntu variants) on and off for about 8 years. I don't know a huge amount about the inner workings, but I am fairly comfortaable with the terminal, and am not HUGELY against a re-install if I frak up too bad. 

Thanks

---

### Post by SteveDee on 2012-02-28
> **thehighpander said:**
> ...Any thoughts/other possible solutions to this?...

There may be something here: [http://ubuntuforums.org/showthread.php?t=1013366](http://ubuntuforums.org/showthread.php?t=1013366)

---

### Post by thehighpander on 2012-02-28
Ok. I gave that a read(or 3), and after much fiddling, I determined that directvnc was the culprit. Now I am using xvnc4viewer, and It allows me to view the screen, but when I try to move the mouse onto It, it sends the mouse to 0,0 on my main screen. If I try to full screen it, then the mouse just jiggles furiously in the corner.

Also, I use mostly Hulu+ and netflix, so the ability to both click, and see what I'm clicking is imperative.

---

### Post by krunge on 2012-03-02
Not sure what is going on... but try "-xwarppointer" on the x11vnc cmdline. 

The x11vnc 0.9.14 dev version applies this option automatically if it detects multiple screens:

[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=43101](https://bugs.freedesktop.org/show_bug.cgi?id=43101)[/INDENT]

---

