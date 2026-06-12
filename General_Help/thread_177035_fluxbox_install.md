---
title: "fluxbox install"
date: 2006-05-15
forum: General Help
---

### Post by smokey132 on 2006-05-15
hello community. I recently wanted to try out fluxbox, so i removed ubuntu and decided to do a fresh install of 5.10. However, i only installed the base system, because i did not want fluxbox to co-exist with gnome/kde or whatever else. so after the base system was installed, the computer boots to the comand line. i login, update my repositories, and then I:

sudo apt-get install fluxbox

Everything worked fine, except fluxbox was telling me x system wasnt set up properly. I then 

sudo apt-get install xserver-xorg

and that worked fine. long story short, i cannot figure out how to start up the X system, (startx doiesnt work) and i do not know of any other x packages i need to install.

any help on what to do is greatly appreciated. thank you.

---

### Post by Ramses de Norre on 2006-05-15
```
sudo aptitude install --with-recommends x-window-system-core xserver-common xfonts-base
```

---

