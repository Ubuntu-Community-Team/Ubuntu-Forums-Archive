---
title: "Problems with mplayer in 9.10"
date: 2009-11-01
forum: General Help
---

### Post by diskmaster23 on 2009-11-01
I just recently upgraded to 9.10 and suddenly I am having trouble playing videos on Mplayer. I've tried the straight mplayer, smplayer, and gnome player. Nothing seems to work.

I can get the video to come up, but it doesn't continue on playing. Some videos such as AVIs or WMVs, they will play for a few seconds or not at all.

I've uninstalled and reinstalled the packages, but nothing seems to work.

I am using a Lenovo T61 on 9.10 upgraded from 9.04.

---

### Post by JayD2 on 2009-11-01
Trying different video drivers worked for me when I first installed Mplayer. In Mplayer it is preferences --> video tab and there should be a list of drivers to try.

---

### Post by diskmaster23 on 2009-11-01
I seem to have much better luck in SMplayer. But Mplayer just refuses 'stream' the video no matter which video mode I use. However, I get much better response with SMplayer, but I get the same problem every once in awhile with the video stopping.

---

### Post by ikacer on 2009-11-01
I think it has something to do with ALSA, try changing the audio driver to pulse and see if that fixes it.

---

### Post by diskmaster23 on 2009-11-01
That worked! Thanks!

---

