---
title: "help with enabling repositories"
date: 2010-04-04
forum: General Help
---

### Post by DrScum on 2010-04-04
I installed ubuntu 9.10 on a Vostro 1520 a couple days ago and am kind of lost with getting the system up and running the way I want it.
I managed to get the medibuntu repositories activated but can't find a way for universe and mulitverse. 
I seems that a lot of software which was available in 9.04 isn't anymore in 9.10 or am I just missing the repositories?

---

### Post by sisco311 on 2010-04-04
System -> Administration -> Software Sources

---

### Post by howefield on 2010-04-04
You don't mention it but, I expect you have already tried Synaptic Package Manager > Settings > Repositories > Ubuntu Software & Other Software tabs...

---

### Post by DrScum on 2010-04-05
well, sorry for being not precise.

I do now technically how to enable repositories but what I am looking for are the repositories which are not part of the distibution like for example medibuntu. 

What I am looking for is the apt line. 

E.g. I would like to enable a 3D desktop but can't find the necessary software in the available repos.

Another issue would be wine. I seem to have solved the media issue myself.

---

### Post by plucky on 2010-04-05
> **DrScum said:**
> well, sorry for being not precise.

I do now technically how to enable repositories but what I am looking for are the repositories which are not part of the distibution like for example medibuntu. 

What I am looking for is the apt line. 

E.g. I would like to enable a 3D desktop but can't find the necessary software in the available repos.

Another issue would be wine. I seem to have solved the media issue myself.

[Medibuntu Documentation](https://help.ubuntu.com/community/Medibuntu)

Good Luck

---

### Post by oldos2er on 2010-04-05
Compiz is installed by default; to enable it go to menus System, Preferences, Appearance, Visual Effects tab. If you were looking for the settings manager, it's in the universe repository: ```
sudo apt-get install compizconfig-settings-manager
```

Wine is also in the universe repository.

---

