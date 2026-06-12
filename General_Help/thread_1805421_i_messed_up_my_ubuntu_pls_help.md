---
title: "i messed up my ubuntu pls help"
date: 2011-07-16
forum: General Help
---

### Post by khaj_vah on 2011-07-16
ppl my ubuntu isnt working after i write my password and press enter it does nothig but gives a massage ''the configuration defaults for GNOME power manager have not been installed correctly'' the recovery console doesnt work too(same problem)  the problem appeared after i installed bittorent client called smth starting with 'd'.

---

### Post by khaj_vah on 2011-07-16
ooo it works i changed the language but it has a problem too the top bar of every window is changed and i cant close or minimize ...

---

### Post by forestG on 2011-07-16
if you want a pure ubuntu-desktop installation you can do the following. 

step 1:
sudo apt-get install ubuntu-desktop.

After that you will hopefully an installation that works. Then if you have played with kubuntu,xubuntu etc try the following

apt-get -s install kubuntu-desktop. 

This is a simulation of the installation. Now copy the names of the files and put them in a file and then run the command sudo apt-get remove *all the packagenames separated with comma*. You can find the command in the site psychocats.net/ubuntu/ site. If you have installed something else like gnome3 or other packages you can follow the example and remove the packages.

You can do that using synaptic as well.

---

### Post by wildmanne39 on 2011-07-16
> **khaj_vah said:**
> ooo it works i changed the language but it has a problem too the top bar of every window is changed and i cant close or minimize ...
Hi, it sounds like you are using unity, if so the buttons are in the top menu bar on the left when you have a window maximized.

---

### Post by khaj_vah on 2011-07-16
[wildmanne39]("http://ubuntuforums.org/member.php?u=508533") lol i am not an idiot i have been using unity for a month and now i changed to classic lol but [forestG]("http://ubuntuforums.org/member.php?u=1042748") saved me everything works now :) thank you mate

---

