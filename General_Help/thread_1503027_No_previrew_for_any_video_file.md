---
title: "No previrew for any video file"
date: 2010-06-06
forum: General Help
---

### Post by dheerajkabra on 2010-06-06
Hi,

Today i installed lucid and its working fine. But I have tones of .flv and .mp4 videos (from youtube :)) which do not show a preview thumbnail when I have selected "Icon View" in Gnome. It shows the standard icon of a movie reel. Am I missing any settings? It used to work great in karmic.

-Dheeraj.

---

### Post by WorMzy on 2010-06-06
I don't know if this will help, as I don't have any files in that format, but try installing ffmpegthumbnailer and swfdec-gnome through synaptic or the following terminal command:
```
sudo apt-get install ffmpegthumbnailer swfdec-gnome
```

---

### Post by dheerajkabra on 2010-06-06
Thanks for the quick response Warmzy.
I installed those two packages but no improvement.

---

### Post by WorMzy on 2010-06-06
Okay, do you have totem installed? If not, installing it may help.
```
sudo apt-get install totem totem-common
```

---

### Post by Carthorse on 2010-06-06
Just a quick thought. When you go into Edit->Preferences->Preview, are the thumbnail options set as you had them previously, with regard to local files, all files, sizes etc??

---

