---
title: "Don't all repos worldwide offer same software?"
date: 2012-05-20
forum: General Help
---

### Post by arcull on 2012-05-20
Hi there. Right today I did a fresh install of lubuntu 12.04 64bit and wanted to add some more software available via Synaptic. I was quite surprised when I found out that not all servers have same software available, or at least so it seems, maybe I did something wrong... I searched for Blender (3d modeling app) and I couldn't find it on Slovenian server so I tried switching to main server, restarted Synaptic and afterwards it did appear under search results. But when I proceeded with installation it took cca. half an hour to complete,  since main server seems so busy. So the question is: do respos worldwide offer different software packages, and if so, which do you recommend? Thanks for suggestions, bye.

---

### Post by wilee-nilee on 2012-05-20
All the servers listed in software sources should be the same, you have to run a update when changing, as they all do not get updated at the same time. You also want to be sure that you have the repo open in the /etc/apt/sources.list that a package is in. Software sources also can open and close repos at your choice.

Any changes are followed with a update.

---

### Post by arcull on 2012-05-20
> , you have to run a update when changing, yep your are right executing ```
sudo apt-get update
``` did resfresh package list, sorry my fault :(, everything ok now.

---

### Post by dcstar on 2012-05-21
> **arcull said:**
> 
........
So the question is: do repos worldwide offer different software packages, and if so, which do you recommend? Thanks for suggestions, bye.

Mirror repositories take time to download and make available changes to the package libraries. People have to be patient - especially when new releases appear - and not expect instantaneous update around the whole planet.

Hammering the main repository only makes the situation worse, because where do people think the mirrors go to get their updates?

---

