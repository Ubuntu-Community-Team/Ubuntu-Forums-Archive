---
title: "Sound problems"
date: 2006-03-28
forum: General Help
---

### Post by kipman725 on 2006-03-28
my sound is oboard my ABIT NF-7 motherboard.  Which I think is nvida six channel audio.  When I installed ubntu I had sound but it was very low quality and crackley so I attempted to install the latest nforce driver (only the audio component).  After getting all the things off apt get the installer asked for I was able to install it but there was no change to my audio after installing.  I presume that I have missed some step out.  So I looked in the multimedia systems selector and selected oss which works better than the ALSA that was selected before and works with XMMS fine.  But I am still unable to get audio in nexuiz working and kaffine stutters.  Anyone help me here?

---

### Post by benvdh on 2006-03-28
Hey,

For Kaffeine you can also change the audio driver to oss. Try this :

1. Open Kaffeine
2. In the settings menu click on Gstreamer Engine parameters
3. Now you are able to change the audio driver kaffeine is using

Regards,

Ben

---

### Post by izmaelis on 2006-03-28
I have just the same type of motherboard with onboard sound as you have. Sound works fine after I followed [this]("http://ubuntuforums.org/showthread.php?t=116737&highlight=aoss+skype") nice how to.

---

### Post by kipman725 on 2006-03-28
I followed that guide exactly and the only differance is that it stutters constantly now on all aplications.  Nexuiz still dosen't have sound.

---

