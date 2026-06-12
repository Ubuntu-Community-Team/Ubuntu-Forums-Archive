---
title: "sound and flashplayer"
date: 2009-12-29
forum: General Help
---

### Post by dino_nz on 2009-12-29
hi guys yes im new to ubntu and i love it,thing is i have just had to do a complete reinstall after good old windows did sumthing to mess things up,anyway i reinstalld 9.04 after completly removing windows yes i have had enough,i had a play for a day or two then upgraded to 9.10 now i have no flashplayer or no sound at all,i have spent 2 days reading serching and all trying to find the answer could sumone please point me in the right direction,and also as easy as u can im not to pc savey many thanks

 dino

---

### Post by zvacet on 2009-12-30
For flash plugin look in synaptic to see if flashplugin-nonfree is installed.if it is and you still can not use it edit your source list with from terminal with command 

```
gksudo gedit /etc/apt/sources.list
```

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

Maybe it is already there but it have # sign in front:If that is  a case remove # sign on that line and save and close file.

```
sudo apt-get update
```

Now in synaptic remove flashplugin-nonfree and install adobe-flashplugin.

---

