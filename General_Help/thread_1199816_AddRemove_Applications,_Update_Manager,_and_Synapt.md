---
title: "Add/Remove Applications, Update Manager, and Synaptic won't open"
date: 2009-06-29
forum: General Help
---

### Post by TheTechFan on 2009-06-29
I did a clean install of the x64 version of Ubuntu 9.04, installed all the updates as of last week, and then installed everything mentioned in Help to enable the playback of proprietary DVDs. Then I wanted to install VLC media player. I found it in add/remove, clicked install, but instead of installing, Add/Remove closed. I tried opening it, and it opened and then immediately closed again. I tried opening synaptic, and it opened and then immediatly closed. Same with update manager. As far as I know all the other apps work. Did I do something wrong? Is this a bug? Thanks in advance for any help.

---

### Post by LowSky on 2009-06-29
hmm seems odd,

here the command line way to install vlc in the mean time
open a temrinal form Applications>Accessories> Terminal then type

```
 sudo apt-get install vlc
```

---

### Post by TheTechFan on 2009-06-29
I tried that and it said

> Reading package lists... Done
Segmentation faulty tree... 0%

What now?

---

### Post by TheTechFan on 2009-06-29
I also tried downloading a .deb file. When I double-clicked it to install it, something popped up on the screen and then disappeared again before I could even see what it was. Something's not right...

---

### Post by jmszr on 2009-06-29
TheTechFan,

I had something very similar happen to me a while back. 
The fix was:```
sudo rm /var/cache/apt/*.bin
```

Hope this helps.

---

### Post by TheTechFan on 2009-06-29
> **jmszr said:**
> TheTechFan,

I had something very similar happen to me a while back. 
The fix was:```
sudo rm /var/cache/apt/*.bin
```Hope this helps.

Thanks so much, everything is now working great, VLC is installed, DVDs are playing,... perfection!
Just out of curiosity, do you know what caused this to happen in the first place?

---

### Post by jmszr on 2009-06-29
TheTechFan,

I don't remember exactly, but as I recall, the problem was caused by piece of info that was supposed to clear out but got hung up. The code I gave you cleared it out. As an aside, always be careful with "rm" commands: [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54) .They can be useful but should be used with caution.
Glad to hear everything is working.

---

