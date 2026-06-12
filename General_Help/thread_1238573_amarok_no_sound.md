---
title: "amarok no sound"
date: 2009-08-12
forum: General Help
---

### Post by franar on 2009-08-12
hi, i used Rhythmbox as default mp3 player but reading i noticed that Amarok is the best to use with an ipod, use lyrics and more features. the problem is when i doubled click on the mp3 files, i have no sound, even the progress bar goes from the beginnin until the end...
other software yes give me sounds but not with Amarok.

some idea of resolving the issue?

thanks in advance
:guitar:

---

### Post by SlugSlug on 2009-08-12
> **franar said:**
> hi, i used Rhythmbox as default mp3 player but reading i noticed that Amarok is the best to use with an ipod, use lyrics and more features. the problem is when i doubled click on the mp3 files, i have no sound, even the progress bar goes from the beginnin until the end...
other software yes give me sounds but not with Amarok.

some idea of resolving the issue?

thanks in advance
:guitar:


sudo apt-get install libxine1-ffmpeg , but amarok2 sucks IMO exaile is much better apart from loading times... and its harder to spell


:guitar:

---

### Post by CatKiller on 2009-08-12
Did you install phonon-backend-xine?

---

### Post by franar on 2009-08-12
what is it?

---

### Post by Yellow Pasque on 2009-08-12
phonon can use multiple backends. The two most popular are xine and gstreamer (Rhythmbox also uses gstreamer). Search in SYnaptic for the appropriate packages and configure phonon using this command:
```
qtconfig
```

---

### Post by djowtlawz on 2009-08-23
Hey guys I have a similar problem but the error when I start amarok is > HDA Intel (CONEXANT Analog) does not work. Falling back to default.

apparently I have the latest libxine1-ffmpeg installed. Not sure what to do

---

### Post by DEMWilson on 2009-10-31
> **djowtlawz said:**
> Hey guys I have a similar problem but the error when I start amarok is 

apparently I have the latest libxine1-ffmpeg installed. Not sure what to do

I had the same error, this fixed it for me:
sudo apt-get install phonon-backend-xine

---

