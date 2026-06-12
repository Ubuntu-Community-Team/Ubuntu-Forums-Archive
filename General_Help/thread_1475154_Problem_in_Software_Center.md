---
title: "Problem in Software Center"
date: 2010-05-06
forum: General Help
---

### Post by Drop D on 2010-05-06
As I have been using Lucid Lynx, I have encountered very view minor problems, until I get to the 
Software Center.  I try to install a game, or anything like tab writing, music players, DVD burners and I get
[IMG]http://i647.photobucket.com/albums/uu192/JoshDefibaugh/Screenshot.png[/IMG]This image tells me I can't install anything.  Anyone can help me, I just want to install some stuff.

---

### Post by darolu on 2010-05-06
The most probable problem are broken packages, it can be fixed using Synaptic (System -> Administration -> Synaptic) read this link to learn how to fix them:

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by Chrissss on 2010-05-06
Open a terminal and fire up

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You should see error messages and hints what to do.

---

