---
title: "Wine blackscreen in fullscreen after installing xorg-edgers drivers"
date: 2012-01-07
forum: General Help
---

### Post by fardin97 on 2012-01-07
Hi, I am using ubuntu 11.10 , wine 1.3.33,intel gma 4500mhd .recently i have installed the xorg-edgers fresh X crack . but after installation when i try to run a game in wine in full screen the whole screen goes black.but i can hear the sounds.but when i run the game in virtual desktop it runs perfectly.i purged the ppa too.but the problem does not solve.also after downloading mesa from intellinuxgraphics and installing it the driver does not change.glxinfo still shows 7.12 devel version mesa.but i installed 7.11.2.how can i solve this problem?

---

### Post by ajgreeny on 2012-01-07
You may need to drop to a command line, then remove xserver-xorg plus all its dependencies.  carefuuly note all packages removed then reinstal;l them all, making sure the xorg-edgers repo is disabled.  It may sound daunting, but it is relatively quick to do, and I think should solve your problem.

I had exactly the same problem several months ago with an ati driver, and this is the only way I could get back to the gnome desktop.

```
sudo apt-get remove xserver-xorg
sudo apt-get install xserver-xorg xorg xserver-xorg-core *#(plus all the other packages that xserver-xorg took with it)*
```

---

### Post by fardin97 on 2012-01-07
> **ajgreeny said:**
> You may need to drop to a command line, then remove xserver-xorg plus all its dependencies.  carefuuly note all packages removed then reinstal;l them all, making sure the xorg-edgers repo is disabled.  It may sound daunting, but it is relatively quick to do, and I think should solve your problem.

I had exactly the same problem several months ago with an ati driver, and this is the only way I could get back to the gnome desktop.

```
sudo apt-get remove xserver-xorg
sudo apt-get install xserver-xorg xorg xserver-xorg-core *#(plus all the other packages that xserver-xorg took with it)*
```

no change.still the same problem.as far as i understand i think this is a mesa driver problem

---

### Post by fardin97 on 2012-01-08
bump!!

---

