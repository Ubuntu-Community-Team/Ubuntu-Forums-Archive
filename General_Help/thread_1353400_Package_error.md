---
title: "Package error"
date: 2009-12-12
forum: General Help
---

### Post by DarkTxS on 2009-12-12
Hey all (:

I installed the adobe-flashplugin package (Adobe Flash Player) and then the system started to show an error (I downloaded the latest package directly from Adobe website). Error says: (when trying to fix or remove it via the console or synaptic)
```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```
so I downloaded the latest version again, but it says that the package may be corrupted and cannot be reinstalled.

The system is UNR.
Got any idea?

---

### Post by spiderbatdad on 2009-12-12
Have you tried removing adobe like this:
```
sudo apt-get purge adobe-flashplugin && sudo apt-get autoremove
sudo apt-get autoclean
```Then try to reinstall adobe-flashpluign.

---

### Post by DarkTxS on 2009-12-13
Yep, and still it gives the same error...

---

### Post by spiderbatdad on 2009-12-13
I believe the error is due to the fact that the package you installed was not a .deb...I assume you built it from source downloaded from abobe. In Ubuntu I believe the package you should have installed is flashplugin-nonfree, or ubuntu-restricted-extras.
Anyway maybe search libflashplayer.so and remove it. Then install the package you want.
```
sudo updatedb
locate libflashplayer.so
```

---

