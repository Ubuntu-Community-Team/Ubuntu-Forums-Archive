---
title: "No sound on local machine when using RDP"
date: 2009-11-14
forum: General Help
---

### Post by srhoades on 2009-11-14
I'm using 9.10 and using RDP to my Windows box. I get no audio. If I go to the Windows control panel to test the sounds it complains that the it can't playback the audio file and to check to make sure it is a valid audio file. If I open iTunes it complains there is a problem with your audio playback devices. The driver being used when I RDP in with Ubuntu is the Microsoft RDP audio driver. Otherwise I have an Intel HD audio controller which works fine when I use the Windows RDP client.

---

### Post by srhoades on 2009-11-14
Ok so I found another thread on a different forum that said to redirect another local device. So I chose to redirect my local disk. It no longer complains about the audio stuff however if I test the sound it sounds like a choir of bullfrogs.

---

### Post by srhoades on 2009-11-15
Solved: 

[http://blog.jayway.com/2008/11/10/getting-sound-to-work-on-ubuntu-810ut/](http://blog.jayway.com/2008/11/10/getting-sound-to-work-on-ubuntu-810ut/)

Confirmed that works in 9.10 as well.

---

