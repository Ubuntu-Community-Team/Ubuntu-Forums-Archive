---
title: "Clearing disk space"
date: 2009-12-09
forum: General Help
---

### Post by Hawk666 on 2009-12-09
I am running a little low on disk space. and was just wondering if there was anyway to get rid of unneeded files easily, i have already run apt-get autoremove and that only cleared 100MB or so, I have found using 'disk usage analyzer' that /var/cache/apt/ contains about 1.3GB, the reason i'm asking about this in particular is because my understanding of a "cache" is that it is only temporary and no permanent damage will be done if it is removed.

---

### Post by fancypiper on 2009-12-09
You can safely delete the .deb files in /var/cache/apt/archives.

If you use Synaptic, there is an option to delete upon installation that will automatically remove them.

---

### Post by oaxacamatt1 on 2009-12-09
Don't forget to load and run'localepurge' when you use Synaptic.  I do that as the second or third thing after a fresh install.  It gets all the foreign stuff ;o} off your machine.
M

---

### Post by Hawk666 on 2009-12-09
thanks a lot, appreciate the quick answer, and i will remember to auto delete in synaptic in the future.

Also how do i run 'localepurge', is that just a terminal command?

---

### Post by Hawk666 on 2009-12-09
alright localepurge installed and ran, removed all but the en-** locales and freed another 44000KB, thanks alot guys

---

### Post by llamabr on 2009-12-09
apt will rm those .deb's for you by:

```
sudo apt-get clean
```

Then install:

deborphan - program that can find unused packages, e.g. libraries

---

### Post by Steve834 on 2009-12-10
When I run low on disk space I fire up KDirStat program.  It shows disk usage in a nice graphical way and you can find out what's taking up all the space.

---

