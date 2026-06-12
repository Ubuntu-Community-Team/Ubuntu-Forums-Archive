---
title: "Can't Download Flash On Ubuntu"
date: 2009-11-14
forum: General Help
---

### Post by TheNerdAL on 2009-11-14
I downloaded Ubuntu but I can't use Flash, it says I already have the package. Please Help.

---

### Post by TheNerdAL on 2009-11-14
Anyone?

---

### Post by Dr. Oddbio on 2009-11-14
If you are in Ubuntu 9.10 Karmic, go to applications, and the last option should be "software center" open that up and search for flash, install it for firefox or whatever you use.


If that doesn't work then try typing this in terminal:
**sudo apt-get install flashplugin-nonfree**

---

### Post by hal10000 on 2009-11-15
Enable your restricted, universe, multiverse and medibuntu repositories with your package manager (synaptic).
Then open a terminal window and perform the commands below (you can mark them here with your mouse and paste them with the middle mouse button).
```

sudo apt-get update
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer

```

Then restart firefox and have fun

---

