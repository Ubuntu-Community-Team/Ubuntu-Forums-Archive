---
title: "Ubuntu Software Center and every other file manager software won't open"
date: 2011-09-24
forum: General Help
---

### Post by Ideaworks on 2011-09-24
Hello
I'm a new user of Ubuntu and I need help because for some reason Ubuntu Software centre is slow and Synaptic Package Manager won't open saying 
> E: Type ‘n’ is not known on line 1 in source list /etc/apt/sources.list.d/ogre-team-ogre-natty.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.I'm pretty sure this is because of my attempt to install ogre, so I've been removing every single package I installed but it still hasn't been fixed

---

### Post by plucky on 2011-09-25
> **Ideaworks said:**
> Hello
I'm a new user of Ubuntu and I need help because for some reason Ubuntu Software centre is slow and Synaptic Package Manager won't open saying 
I'm pretty sure this is because of my attempt to install ogre, so I've been removing every single package I installed but it still hasn't been fixed
Welcome to the Forum


Open a terminal and post output of ```
cat /etc/apt/sources.list.d/ogre-team-ogre-natty.list
```

Or open Software Sources and disable the **ogre** repository.

Good Luck

---

