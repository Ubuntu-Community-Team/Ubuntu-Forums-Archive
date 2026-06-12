---
title: "How to completely remove dockbarX"
date: 2010-06-14
forum: General Help
---

### Post by chinmaya_n on 2010-06-14
Hi,

I 've encountered some problem  with dockbarX!
The main problem I'm encountering with it is, it is not showing the present working windows but it is just showing the launchers.
So I would like to install it again... but if I romove it by 'apt-get remove' it is not getting completely removed.
I mean if I install it after removing it is showing same behaviour... might be having same properties continued by some previous files...
So How should I completed remove It..

And also I 've another problem... dockbarX is not loading in AWN...

---

### Post by ThesaurusRex on 2010-06-14
```
sudo apt-get autoclean dockbarX
```

That should take out all of the other files that keep your old settings, etc.

---

### Post by chinmaya_n on 2010-06-14
```
sudo apt-get autoremove dockbarx
sudo apt-get autoclean dockbarx
```
worked like a charm!!
Thanks  ThesaurusRex.

After next installation it worked fine. bUt still it encounters problem and fails to load in AWN ! Does anyone know any reason :)
Thanx

---

### Post by chinmaya_n on 2010-06-14
Guys.... Properties window is not getting opened !! :(

---

### Post by chinmaya_n on 2010-06-14
Hey..... got it from here
[http://ubuntuforums.org/showthread.php?t=1485694](http://ubuntuforums.org/showthread.php?t=1485694)

Thanx...!

---

