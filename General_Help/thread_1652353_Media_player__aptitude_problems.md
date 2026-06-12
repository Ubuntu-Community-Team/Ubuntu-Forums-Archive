---
title: "Media player / aptitude problems"
date: 2010-12-24
forum: General Help
---

### Post by Toliot on 2010-12-24
Hey, I recently switched back to ubuntu after a year of gaming on w7, however I think that this time I'm going to stick to ubuntu, if she doesnt screw me like she has the previous times... :?

Anyways, I was just wondering what media players you guys favor, and why? (maybe there doesn't have to be a reason xD), and I tried to install beep media player with:

sudo aptitude install beep-media-player

and the return is: sudo: aptitude: command not found

does anyone know what I'm doing wrong?
any feedback would be great
It feels good to be back in the ubuntu community, windows just doesn't have the same community :)

---

### Post by garvinrick4 on 2010-12-24
> **Toliot said:**
> Hey, I recently switched back to ubuntu after a year of gaming on w7, however I think that this time I'm going to stick to ubuntu, if she doesnt screw me like she has the previous times... :?

Anyways, I was just wondering what media players you guys favor, and why? (maybe there doesn't have to be a reason xD), and I tried to install beep media player with:

sudo aptitude install beep-media-player

and the return is: sudo: aptitude: command not found

does anyone know what I'm doing wrong?
any feedback would be great
It feels good to be back in the ubuntu community, windows just doesn't have the same community :) ```
sudo apt-get install aptitude
```#I like vlc plays anything I throw at it.
```
sudo apt-get install vlc
``````
sudo apt-get install libdvdcss2
``````
sudo apt-get install ubuntu-restricted-extras
```#ubuntu-restricted-extras gives you a lot of codec's to play audio and video, dvd is libdvdcss2
###aptitude great for safe-upgrade
```
sudo aptitude update && sudo aptitude safe-upgrade
```##vlc looks like a little small player but huge inside:

---

