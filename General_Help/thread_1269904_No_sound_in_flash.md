---
title: "No sound in flash"
date: 2009-09-18
forum: General Help
---

### Post by iskaar22 on 2009-09-18
Hey guys I am new to linux. I have read quite a few threads over fixing no sound in flash but nothing seems to work. I got flash from the repository. I have a creative x-fi xtreme gamer sound card and got the drivers from their site. But when I watch a flash video I have no sound, yet system sounds and application sounds work fine.

I am using wubi.
I am using ubuntu 9.04.

Here are my current settings:
[http://img508.imageshack.us/img508/1548/screenshotsoundpreferen.png](http://img508.imageshack.us/img508/1548/screenshotsoundpreferen.png)

I have a lot of other options but the OSS is the only one that seems to work:
[http://img193.imageshack.us/i/soundpref.png/](http://img193.imageshack.us/i/soundpref.png/)

my volume control:
[http://img41.imageshack.us/i/screenshotvolumecontrol.png/](http://img41.imageshack.us/i/screenshotvolumecontrol.png/)

when i sound test it is fine

when i change the settings to alsa instead of OSS:
[http://img170.imageshack.us/i/screenshotsoundpreferen.png/](http://img170.imageshack.us/i/screenshotsoundpreferen.png/)

Then try to test I get:
[http://img35.imageshack.us/img35/3725/12026357.png](http://img35.imageshack.us/img35/3725/12026357.png)

---

### Post by iskaar22 on 2009-09-19
bump

---

### Post by iskaar22 on 2009-09-19
bump

---

### Post by iskaar22 on 2009-09-19
bumpbump

---

### Post by iskaar22 on 2009-09-19
fixed went in to pulseaudio device chooser and under playback right clicked and moved stream to my creative x-fi card.

---

