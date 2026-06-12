---
title: "WOnt play any sounds on some websites"
date: 2006-06-14
forum: General Help
---

### Post by eighthate on 2006-06-14
Seams like my sound card isnt completely installed cause i cant hear any sounds form [www.youtube.com](www.youtube.com). 

any1 has an idea about what i should do?
my sound card is a cmedia

---

### Post by BitTorrentBuddha on 2006-06-14
It's because flash pipes sound through OSS. The simplest fix would be to download alsa-oss ```
sudo apt-get install alsa-oss
``` And then run firefox each time with ```
aoss firefox
``` Instead of just ```
firefox
``` And don't forget to change the panel launcher (if you use it) by right clicking the icon and choosing properties.

---

