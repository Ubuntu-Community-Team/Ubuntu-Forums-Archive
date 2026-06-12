---
title: "problem vith graphics and playing videos"
date: 2011-08-16
forum: General Help
---

### Post by Marko90 on 2011-08-16
i have problems playing videos  ..i got all codecs from. ubuntu restricted software package. and i CAN play videos but with very bad quality. i cant even think of playing hd 1080p videos ..so lagy and out of sync.maybe the problem is with drivers for my ati mobility radeon hd 4250 ..i tried ati/amd proprientary fglrx graphic driver but everything gets worse .. when i move windows or drag and drop something everything is so slow, and video playback quality does not get any better ..maybe i need to install this :
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

but i have no idea how to do that


 any ideas?

---

### Post by Keypel on 2011-08-16
Personal, I use the linux version of xbmc because it uses my gpu's video  acceleration rather than using the cpu like vlc, movie player,etc does.

```
sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update
```

---

