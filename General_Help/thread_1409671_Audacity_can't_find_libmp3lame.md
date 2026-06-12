---
title: "Audacity can't find libmp3lame"
date: 2010-02-17
forum: General Help
---

### Post by mynot on 2010-02-17
OK. Can't export an mp3 file from Audacity because it can't find libmp3lame.so. I have:
- clicked the Audacity Download button on the error window
- installed lame using Synaptic
- installed lame, liblame0, liblame-dev and libmp3lame0 using apt-get
all as per various forum suggestions. 
Still can't find anything like libmp3lame.so or .so.0 on my (8.04) system.
Thanks
Tony

---

### Post by jpeddicord on 2010-02-18
> **mynot said:**
> OK. Can't export an mp3 file from Audacity because it can't find libmp3lame.so. I have:
- clicked the Audacity Download button on the error window
- installed lame using Synaptic
- installed lame, liblame0, liblame-dev and libmp3lame0 using apt-get
all as per various forum suggestions. 
Still can't find anything like libmp3lame.so or .so.0 on my (8.04) system.
Thanks
Tony

Moved to General Help.

---

### Post by alphaniner on 2010-02-18
According to packages.ubuntu.com, libmp3lame.so is in the liblame-dev package and libmp3lame.so.0 is in the liblame0 package.  I'm running 8.04 and I installed these packages.  The libmp3lame files were then found in /usr/lib.  Are you absolutely sure you have the packages installed?

---

### Post by mynot on 2010-02-19
Thanks. Don't know why but it now works.
Tony

---

