---
title: "Amarok won't play mp3 on Xubuntu 9.10"
date: 2010-04-03
forum: General Help
---

### Post by erufu987 on 2010-04-03
Hello, I have a problem when trying to listen mp3 files in Amarok. Amarok won't play them even though i installed mp3 decoder (i think libmad) and gstream through Synaptic Package Manager.

The program for music listening which came with Xubuntu is playing mp3 files with no problems.

Please help me, I've set up Xubuntu on my PC just recently and I don't know what to do.

Thanks for replying in advance!

---

### Post by ajgreeny on 2010-04-03
Activate the medibuntu repos and then install the w32codecs (or w64codecs) and also the xubuntu-restricted-extras, and you should have just about every codec you could ever need.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by lidex on 2010-04-04
Try this command;
```
sudo apt-get install phonon-backend-xine
```

In a terminal: "Applications>Accessories>Terminal"
Restart Amarok.

---

