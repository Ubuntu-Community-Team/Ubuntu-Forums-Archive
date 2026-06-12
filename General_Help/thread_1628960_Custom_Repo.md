---
title: "Custom Repo"
date: 2010-11-23
forum: General Help
---

### Post by gobba on 2010-11-23
Hi!
Ive setup my own repo for my custom packages that ive built from source to replace some packages in an actual repo.

How do i make the client systems only to update the packages from my repo and not from the original repo?

Is it to add the source at the top of sources.list?

-gob

---

### Post by Hippytaff on 2010-11-23
> 
Is it to add the source at the top of sources.list?

That's the most common way, but the user might then have trouble with authentication keys if your using authentication key's :-)

---

### Post by gobba on 2010-11-23
and how would i make sure the clients dont update to a new version if the main repo package is updated?

---

### Post by Hippytaff on 2010-11-23
do you mean when the user does
```

sudo apt-update && sudo apt-upgrade

```
 
you don't want them to have their packages installed from your ppa to get upgraded?
If so I don't know, not sure you can :-s

---

### Post by gobba on 2010-11-23
> **Hippytaff said:**
> do you mean when the user does
```

sudo apt-update && sudo apt-upgrade

```
 
you don't want them to have their packages installed from your ppa to get upgraded?
If so I don't know, not sure you can :-s

I want them to install the packages that ive customized from my repo and not from the original repo. 

When the original repo updates a package it will be a version above my custom made one until ive recompiled it again. which will make it so that when the client runs update/upgrade it will install from main repo and not keep my custom package.

-gob

---

### Post by Hippytaff on 2010-11-23
They'd have to remove the original repo from sources.list.
 
Sounds awful dodgy :-)

---

### Post by gobba on 2010-11-23
> **Hippytaff said:**
> They'd have to remove the original repo from sources.list.
 
Sounds awful dodgy :-)

hehe yeah! 

maybe a mirror of the orig than switch the package?

-gob

---

### Post by QLee on 2010-11-23
[QUOTE=gobba]I want them to install the packages that ive customized from my repo and not from the original repo. 

When the original repo updates a package it will be a version above my custom made one until ive recompiled it again. which will make it so that when the client runs update/upgrade it will install from main repo and not keep my custom package.[/QUOTE]

Yes, you obviously understand how the package manager sets priority.

The topic you want to investigate is apt pinning, it is an advanced topic, can't be explained in a few simple sentences and not really appropriate for a beginner forum (even a "General", beginner forum, likely that too many beginners would get confused and foul up their install). Basically, pin your version at a higher priority, take the time to read, understand, and learn about pinning, it won't be hard after that. Good luck! Of course you can work around it by editing sources list manually and updating manually and never letting the system do it automagically. If it ever does, downgrading might turn out to be problematic and/or impossible. Be careful!

---

### Post by gobba on 2010-11-23
> **QLee said:**
> Yes, you obviously understand how the package manager sets priority.

The topic you want to investigate is apt pinning, it is an advanced topic, can't be explained in a few simple sentences and not really appropriate for a beginner forum (even a "General", beginner forum, likely that too many beginners would get confused and foul up their install). Basically, pin your version at a higher priority, take the time to read, understand, and learn about pinning, it won't be hard after that. Good luck! Of course you can work around it by editing sources list manually and updating manually and never letting the system do it automagically. If it ever does, downgrading might turn out to be problematic and/or impossible. Be careful!

awesome! Thnx!

-gob

---

