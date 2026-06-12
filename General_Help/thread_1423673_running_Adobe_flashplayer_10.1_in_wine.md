---
title: "running Adobe flashplayer 10.1 in wine"
date: 2010-03-06
forum: General Help
---

### Post by pytheas22 on 2010-03-06
Version 10.1 of Adobe's flashplayer supports offloading of video decoding to the GPU, meaning it should finally be possible to play fullscreen flash videos at high resolution on lower-end hardware.  Granted, this should have been done ten years ago, but it's nice that Adobe's addressing it now (I guess they're finally getting scared of html5 breaking their monopoly on embedded videos).

Unfortunately, like most other things Adobe does, the GPU offloading feature isn't supported on Linux (or Mac OS X, for that matter).

Given this, I was wondering if anyone had experience using the Windows build of flashplayer 10.1 in wine, with the Windows version of Firefox (or some other browser), and if you were able to get the GPU offloading feature running under that configuration.  I don't understand enough about how this feature works to know whether offloading could work with wine, or if DirectX needs to be installed as as prerequisite, etc.

I tried playing fullscreen Hulu videos using flashplayer 10.1 in Firefox in wine, but the results were not any better than they are normally.  But that could just be my hardware (not all graphics cards are supported), or the result of not having DirectX installed; I'm not sure.

Any thoughts would be much appreciated.  I'm dying to be able to watch Hulu without killing my CPU, and I can't find much information on the Internet on possible ways to take advantage of the offloading feature without using Windows.

---

