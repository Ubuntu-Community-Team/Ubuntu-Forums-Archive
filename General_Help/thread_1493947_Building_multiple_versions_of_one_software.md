---
title: "Building multiple versions of one software"
date: 2010-05-26
forum: General Help
---

### Post by linuxnovice on 2010-05-26
Hello,

I am not sure if this is the right section to ask this question (sorry if it isnt). Anyway, I want to build and install 3 different softwares:
OpenCV, Player, Stage. 

These are required for my school projects and research etc. Now, I need to install them in this manner:
Opencv-2.0.0, player-2.1.3 and stage-2.1.1

and 

Opencv-2.1.0, player-3.0.1 and stage-3.2.2

The reason for this is, these are the sets of versions that talk to each other without problems. And I need the older versions for a project that I'm currently working on and its always nice to have the newest version installed on the system. If its only a single version install, its pretty easy and I can do it. Since I want to install multiple versions of the same software I could use some help. I am not sure whether I can install all of the them in the default directory (/usr/local/). So, I can set up a separate directory on my home folder. But thats as far as I've gotten to. I am particularly concerned whether one version would break another. Is there anything that I can do to avoid this?

Thanks.

---

### Post by linuxnovice on 2010-05-29
Could use some help on this.

---

### Post by dino99 on 2010-05-29
programming forum should be more helpfull

---

### Post by jobix on 2010-05-29
I think you should be able to install multiple versions in the same directory. For example, if you look at /usr/lib, you will likely see multiple versions of the same library file but typically only one of them is being linked to the current application. So you might have to play around a bit to get the correct linkages.

---

