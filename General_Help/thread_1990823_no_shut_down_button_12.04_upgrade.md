---
title: "no shut down button 12.04 upgrade"
date: 2012-05-29
forum: General Help
---

### Post by 3pinner on 2012-05-29
I have a whole host of issues with an upgrade to 12.04, with no shutdown button (the'cog').
How do I get it back?
I can only run Unity in 2D at the moment, but that's another thread.
Thanks

---

### Post by 3pinner on 2012-05-30
any suggestions please?

---

### Post by melrokz on 2012-05-30
You may try reinstalling unity-2d package.

sudo apt-get purge unity-2d
sudo apt-get install unity-2d

---

### Post by 3pinner on 2012-05-30
> **melrokz said:**
> You may try reinstalling unity-2d package.

sudo apt-get purge unity-2d
sudo apt-get install unity-2d

Thank you. I'll give it a try.

---

### Post by enterdavertex on 2012-05-30
maybe try using another user interface ans reinstalling the GUI of unity 2D, personnaly instead of using that one i suggest using Xubuntu 
sudo apt-get install xubuntu-desktop 

or if you want to shutdown the pc type CTRL+ALT+T and type in : 
sudo shutdown -f -t 1
that should tdo the trick if it isn't fixed.

---

### Post by James Heller on 2012-05-30
I have the same problem with my ubuntu 12.04 upgrade as well. I can't shutdown from the menu bar, the cog button is gone.

Had to use terminal to shutdown everytime and still found no fixes.

---

### Post by 3pinner on 2012-05-30
Thanks for the tips. I've decided to do a fresh install of 12.04 on another hard drive, then use Cinnamon instead of the Unity interface. I'm not even going to try to fix the problems with this upgrade. 
It's my fault really, I was due for a fresh install, but was too lazy to  deal with it.

---

