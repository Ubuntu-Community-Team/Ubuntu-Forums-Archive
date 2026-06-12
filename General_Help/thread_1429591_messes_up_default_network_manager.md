---
title: "messes up default network manager"
date: 2010-03-14
forum: General Help
---

### Post by jsriz on 2010-03-14
Hearing the praises about fastness of xfce all over the net i decided to try it for my fav ubuntu
i rightaway installed xubuntu (without creating a bakup of the names of programs that were going to be installed which i generally do to fully remove any utility that i install for test) 
i understood that fast for xfce actually meant light(stupid me).....
now i switch back to gnome onlt to find xfce stuff like pacmn file browser and wicd to name a few.
i removed the pacmn browser but when i remove wicd  the default network manager does not show up in the task panel
i would like to know:
1.how to get back to gnome'z default network manager AND
2.the list of utilities installed when xubuntu-desktop is installed (plz someone run sudo apt-get install xubuntu-desktop and then copy the dependencies it shows and post it here)

---

### Post by DawieS on 2010-03-14
Open Synaptic Package Manager. Click on the **File - History** tab. For every update or installation instance, you should have an date/time entry showing which packages was installed/upgraded.

Where more than one package is installed at the same time, the main package is usually dependent on the others. Where packages were upgraded to other versions, it shows the "from" and "to" packages. 

By analyzing this information you should be able to decide which packages should be un-installed, and which re-installed, to get the result you want.
:grin:

---

