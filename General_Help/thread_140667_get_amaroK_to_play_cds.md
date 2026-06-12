---
title: "get amaroK to play cds"
date: 2006-03-06
forum: General Help
---

### Post by HokeyFry on 2006-03-06
Hi. I really like amaroK for music, but I can't get it to play cds. Not that the default Ubuntu CD player doesn't work fine, but I prefer to use applications that do several things at once, like play cds, and manage an mp3 player and a collection of music, all at one time. However, when I try to play a cd in amaroK, i get this error:

```

Could not start process Unable to create io-slave:

klauncher said: Unknown protocol 'audiocd'.

```

I realize that amaroK is a KDE application, so if that is the problem, then I guess I need to know how to run this in a gnome desktop.

---

### Post by welsh_spud on 2006-03-06
Thats weird. I thought CD support was installed by default. Meh. You will need to install the package 'kdemultimedia-kio-plugins'.

There are two ways to install it.

1) Go to *System > Admin > Synaptic Package Manager* and search for kdemultimedia-kio-plugins

2)**(easiest)**:In a terminal window type in:
```
sudo apt-get install kdemultimedia-kio-plugins
```

---

