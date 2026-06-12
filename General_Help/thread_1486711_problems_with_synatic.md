---
title: "problems with synatic"
date: 2010-05-18
forum: General Help
---

### Post by manji_kun on 2010-05-18
As the Title says, I've been having some troubles with my package manager, this might be why.

I downloaded and "upgraded" to 10.4, it didn't work out (crashed my hard drive) and i had to reformat and reinstall 9.04, and immediately upgraded to 9.10 without updating the packages, I'm not sure if that's the issue, I tried downloading and installing wine so i can play some games, and the error i get is 


```

                                 E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list 
 E: The list of sources could not be read. 
 Go to the repository dialog to correct the problem. 
 E: _cache->open() failed, please report.
 
```after the first time i got this error, i deleted wine and deleted it from the software sources list as well, but i still get the error, and i can't update anything until i get this fixed.

---

### Post by manji_kun on 2010-05-18
Synaptic^

---

### Post by oldos2er on 2010-05-18
```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
``` will remove the wine ppa, after which run ```
sudo apt-get update
```

---

