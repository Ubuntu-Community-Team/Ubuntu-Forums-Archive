---
title: "Linux not streaming vids in any browsers"
date: 2011-09-16
forum: General Help
---

### Post by HappyLinux on 2011-09-16
Every time I go to watch something online, no matter which website (YouTube, crunchyroll, etc.) through any and all of the 3 main browsers under Linux (chrome, FF and Opera(most recent versions)), it never seems to stream/buffer.

Sometimes it just doesn't load the clip, sometimes it'll buffer a minute of the clip and then nothing. Most times, in YouTube for example, it'll buffer so far, and then the buffer progress bar will jump to 100% and then the clip will freeze as if paused. Another variation of this, is buffering so far, and then doesn't buffer any-more as if the buffering had just froze.

I've got the most recent browser versions, and the most recent flash versions possible, but it still happens. FF has been doing it since 3.x, I don't know what version Chrome and Opera started it, but it was round the same time as FF3.x.

I've checked the Flash settings, but that hasn't help. It has to be a Linux problem, because it doesn't do it in Win7 which I dual-boot with. In Win7, it'll buffer a 30min YouTube clip smoothly, yet under Linux, it'll do like the first few minutes and then the above happens.

This is completely driving me up the wall. Every-time I want to watch something, I have to keep reloading the webpage, or changing the resolution back and forth (YouTube) and then clicking on the time frame that I got up too.

Can anyone help?

---

### Post by drmrgd on 2011-09-16
I would recommend installing [Flash Aid]("http://www.webgapps.org/add-ons/flash-aid") to see if that fixes the problem.  Seems to work magic on most flash player problems like you describe.  Definitely worked for me!

---

### Post by HappyLinux on 2011-09-16
I've already been using FlashAid. The problem is not just with Flash players on websites. The problem is also with other players, like VLC.

---

### Post by HappyLinux on 2011-09-24
Any takers???

---

### Post by reezaane on 2011-10-01
I use the latest version of Ubuntu 11.04 and i did get the problem you mention with all video playback with browsers/vlc.

After installing all update and since i have an Nvidia 9500Gt by reinstalling latest driver fixed the problem.

Is the issue still there?

---

### Post by HappyLinux on 2011-10-04
Yes, my problem still remains. I'm currently using Ubuntu 11.04, but will be switching to Xubuntu 11.10 as soon as it's released.

I'm using the latest official versions of everything possible. browsers, codecs, media players, flash, nvidia drivers, etc.

I have a hunch what might be the cause and which will be rectified by the end of the week. that's my ISP. My current ISP is unreliable so I'm switching to one that's more reliable and will allow higher speeds.

---

### Post by philinux on 2011-10-04
> **HappyLinux said:**
> Yes, my problem still remains. I'm currently using Ubuntu 11.04, but will be switching to Xubuntu 11.10 as soon as it's released.

I'm using the latest official versions of everything possible. browsers, codecs, media players, flash, nvidia drivers, etc.

I have a hunch what might be the cause and which will be rectified by the end of the week. that's my ISP. My current ISP is unreliable so I'm switching to one that's more reliable and will allow higher speeds.

Mmm. That may be it. In the meantime try this.
1. On the flash video right click and choose settings. Untick enable Hardware Acceleration. If no change reverse that.

2. Close firefox and open a terminal and use this to start firefox.
```
firefox -safe-mode
```

Post back with results.

---

### Post by HappyLinux on 2011-10-05
> **philinux said:**
> Mmm. That may be it. In the meantime try this.
1. On the flash video right click and choose settings. Untick enable Hardware Acceleration. If no change reverse that.

2. Close firefox and open a terminal and use this to start firefox.
```
firefox -safe-mode
```

Post back with results.

The Hardware Acceleration thingy has no bearing as the problem remains whether it's ticked or not.

---

### Post by HappyLinux on 2011-10-10
I was right. The problem with buffering was due to my ISP. My new ISP is more stable. So far, I've had no problems buffering. Still have the problem with flash player not always showing, requiring the refresh of the webpage, but no buffering problems.

---

### Post by HappyLinux on 2011-10-25
I have returned this thread to the position of unsolved because the problem has returned. It's probably down to Xubuntu 11.10, or I'm missing a program/driver or something, even though I've installed everything I had back on Ubuntu 11.04.

---

