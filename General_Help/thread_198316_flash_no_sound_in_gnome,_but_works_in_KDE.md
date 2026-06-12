---
title: "flash no sound in gnome, but works in KDE"
date: 2006-06-17
forum: General Help
---

### Post by newpants2003 on 2006-06-17
i tried many ways cant solve the problem.
i installed kde-destop, find out the sound works fine in kde, but stil not working in gnome. 
any ideas??

---

### Post by BitTorrentBuddha on 2006-06-17
Does flash pipe audio through arts instead of oss in KDE. Try downloading alsa-oss and preceding your browsers command with aoss to get sound piping through alsa in Gnome.```
sudo aptitude install alsa-oss
aoss firefox
```
(*replace firefox with your browser of choice*)

---

### Post by newpants2003 on 2006-06-17
i tried this before,  and tried again, still not working....

---

