---
title: "No sound in flash  64 bit"
date: 2010-05-15
forum: General Help
---

### Post by praveesh on 2010-05-15
In KUbuntu lucid 64bit there is no sound in flash , I mean in youtube videos and swf files . I tried in firefox, chromium, and opera . 
I first downloaded  tar.gz file of version 10 , extracted the .so file and copied to /usr/lib/mozilla/plugins , /usr/lib/opera/plugins , /usr/lib/chromium-browser/plugins  folders . When no sound was found , I replaced the .so files by downloading the 10.1 release candidate version of flash player .so file . Still no sound 
All other applications like amarok utilizing phonon works well 

vlc also doesn't produce sound . I don't know whether this can be related . 
Please help .

---

### Post by praveesh on 2010-05-15
please help

---

### Post by jeshuabratman on 2010-05-15
I was having this problem too after installing kubuntu 64. Try turning up the volume on PCM channel in alsamixer.

---

### Post by praveesh on 2010-05-16
> **jeshuabratman said:**
> I was having this problem too after installing kubuntu 64. Try turning up the volume on PCM channel in alsamixer.
Thanks.

Can It be done with kmix ?

---

### Post by gnik1 on 2010-05-16
Is your sound device showing up ok in hardware? Maybe it's a driver update that's needed?

---

### Post by praveesh on 2010-05-17
> **jeshuabratman said:**
> I was having this problem too after installing kubuntu 64. Try turning up the volume on PCM channel in alsamixer.

That helped. Thanks.

---

