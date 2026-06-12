---
title: "Sound not working when Java running - Ubuntu Maverick"
date: 2011-03-28
forum: General Help
---

### Post by apoorvumang on 2011-03-28
I have this problem that whenever java is running (eg. Runescape), sound works only in the Java window, and I don't get sound from flash, mp3s or anywhere else.
I found several similar threads but most of them were unsolved, and the few solutions didn't work.

Note: Earlier, I used to use IcedTea browser plugin for java, which didn't seem to give any sound problems, though was a bit glitchy otherwise. This problem started only after switching to the Java plugin found on [http://www.java.com/en/download/](http://www.java.com/en/download/)

---

### Post by apoorvumang on 2011-03-28
I tried a solution which said removing pulseaudio and installing alsa drivers. However, the problem still persists.

---

### Post by apoorvumang on 2011-03-29
Bump

---

### Post by apoorvumang on 2011-03-31
Finally solved the problem through the runescape forums. Adding padsp before the browser command(ie running firefox with padsp firefox) does the job, though I don't know why.

---

