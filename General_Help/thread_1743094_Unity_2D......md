---
title: "Unity 2D....."
date: 2011-04-29
forum: General Help
---

### Post by TivA on 2011-04-29
I have Ubuntu 11.04.The lap-top I've got has a  graphics card that isn't good enough for unity 3d, but definitely for unity 2d. I just don't know how to get it. I've tried downloading it from the software centre. I've downloaded all the packages you need to run (I believe so).
Is there anything I should do to get it?

---

### Post by dino99 on 2011-04-29
unity 2D is the fallback choice by default, but the package need to be installed

into a terminal, run, step by step:

sudo apt-get update
sudo apt-get install -f
sudo apt-get install unity-2d
sudo dpkg --configure -a

if that dont work, open synaptic and: remove/purge unity & ubuntu-desktop

---

### Post by r-senior on 2011-04-29
You also need to select Unity 2D from the drop-down box at the bottom of the login screen. This only appears after you enter/select your username.

---

### Post by TivA on 2011-04-29
> **r-senior said:**
> You also need to select Unity 2D from the drop-down box at the bottom of the login screen. This only appears after you enter/select your username.
I know that. But now it works, thanks

---

