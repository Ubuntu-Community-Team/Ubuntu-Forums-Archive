---
title: "how to delete a lock file"
date: 2012-01-08
forum: General Help
---

### Post by cold37 on 2012-01-08
hi i have Ubuntu Desktop 11.10 32bit and i when to [http://www.webupd8.org](http://www.webupd8.org) and download - sudo add-apt-repository ppa:webupd8team/themes - and now my Synaptic Package Manager keep saying error occurred -> E: Type 'bupd8team/themes/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/webupd8team-themes-oneiric.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
this webupd8team-themes-oneiric.list is locked i when to it i can not delete it how do i do it please help

---

### Post by mikewhatever on 2012-01-08
Something must have gone wrong with adding the PPA. 
Remove it:
```
sudo rm /etc/apt/sources.list.d/webupd8team-themes-oneiric.list
```

then run the following to re-add:
```
sudo add-apt-repository ppa:webupd8team/themes
```

Don't download anything while at it. :~)

---

### Post by cold37 on 2012-01-08
thank you

---

