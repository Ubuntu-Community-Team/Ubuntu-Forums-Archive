---
title: "Realplayer 10, libdvdcss, win32codecs gone from additional apt repos."
date: 2006-03-01
forum: General Help
---

### Post by apsalyers on 2006-03-01
Though you can still do a manual install of the necessary files and codecs, Realplayer 10, libdvdcss2, and w32codecs were formerly available, until yesterday through the unoffical repos such as PLF and Multiverse.  As of yesterday this is not the case.  While manual install is pretty simple, it may daunt newer users.  Does anyone have any alternative apt repositories where these video tools can still be found?  The sources I use are below.

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 



Thanks.

---

### Post by MacV on 2006-03-01
What do you mean they are no longer available? When and why were they removed?

---

### Post by manicka on 2006-03-01
PLF is working just fine for me.  Looks like they had a problem with their main mirror yesterday. You can always use one of the other mirrors available at their website when this happens

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by MacV on 2006-03-01
I just re-loaded my package list and everything seems to be ok. Try manicka's suggestion and tell us how everything went.

---

### Post by Bachstelze on 2006-03-01
It didn't work for me today either, so I just browsed the repos, downloaded the .debs and installed them manually :D

---

### Post by lado2mx on 2006-03-02
Hi, i have this problem, any mp3 file its invalidated, i dont understand, i have download an reinstalled all codecs (i guess) and nothing :-# tnks...

---

### Post by manicka on 2006-03-02
sudo apt-get install gstreamer0.8-plugins

---

