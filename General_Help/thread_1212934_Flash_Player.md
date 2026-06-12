---
title: "Flash Player"
date: 2009-07-14
forum: General Help
---

### Post by darthtony on 2009-07-14
Hi again! I am having a problem with youtube videos in ubuntu 9.04
I have installe a plugin named shockwave plus. it works, but sometimes, the video's sound stops working at half of the video, and there are some other playback problems, that are a bit difficult to describe.
I have tried downloading the official flash player from adobe, (the .deb package) and installed it but nothing changed. what should i do?

---

### Post by frt975 on 2009-07-14
Is shockwave plus a firefox addon?

---

### Post by masux594 on 2009-07-14
If u are in jaunty [9.04] run this command```
sudo apt-get install flashplugin-installer flashplugin-nonfree
```.. and then restart FF!

Sysc, A

---

### Post by ghostborg on 2009-07-14
I was having flash problems with Firefox 3.011 on Ubuntu 9.04 64bit.
I did a complete uninstall, backup your bookmarks.
My problems went away with Firefox 3.5 .

---

### Post by darthtony on 2009-07-15
i tried reinstalling the new one, it somewhat improved, but still for eg i cant watch vids on youtube on high quality

---

### Post by bjdodo on 2009-07-15
AFAIK adobe flash and pulseaudio do not cooperate too well, probably that is the reason for your problems as well. Pulseaudio is the default sound system from ubuntu 9.04, previously the default sound system was ALSA. You could try to use ALSA instead of pulseaudio. Some people even uninstall pulseaudio using the package management tool e.g. for skype.

---

### Post by darthtony on 2009-07-15
never mind after installing the new firfox, the sound problem seems to dissapear.
But i have just noticed another problem. i tried playing poker online, but it wouldn't load. (blank page) the page was a  ".asp"

---

### Post by t0p on 2009-07-15
> **darthtony said:**
> never mind after installing the new firfox, the sound problem seems to dissapear.
But i have just noticed another problem. i tried playing poker online, but it wouldn't load. (blank page) the page was a  ".asp"

I reckon you ought to start a new thread, with a descriptive title, so folk who can help will see it.

---

### Post by darthtony on 2009-07-15
How should i name it?
Doesnt't it have top do with flash player?

---

### Post by eival on 2009-07-15
> **ghostborg said:**
> I was having flash problems with Firefox 3.011 on Ubuntu 9.04 64bit.
I did a complete uninstall, backup your bookmarks.
My problems went away with Firefox 3.5 .

that was the complete opposite for me on 8.04, after i installed 3.5 all the youtube videos displayed a black background with "sorry an error has occurred..."

also Java apps caused the browser to become unresponsive

i went back to using FF 3.11 again till they sort out those issues.

---

