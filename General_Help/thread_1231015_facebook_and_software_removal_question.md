---
title: "facebook and software removal question"
date: 2009-08-04
forum: General Help
---

### Post by dragon84 on 2009-08-04
After playing around with ubuntu for a while (installing and uninstalling programs) i have relised that everytime i uninstall a program it leaves some folders behind. eg multiget leaves .multget folder in and comix leaves .comix behind in the home folder (not sure if thats the only place). i was wondering how to completely remove a program without leaving anything behind.:confused:

does 'computer janitor' help?

also, facebook games don't load, even though flash is installed. anyone know the reason?:confused:

thanks

---

### Post by prshah on 2009-08-04
> **dragon84 said:**
> i was wondering how to completely remove a program without leaving anything behind.:confused:

does 'computer janitor' help?


If you are uninstalling via command line, use the "--purge" option eg```
sudo apt-get remove --purge someprogram
``` If you are using the GUI, for Eg Synaptic (You cannot completely remove using Add/Remove programs) then find the package to be removed, right click it, and choose "Completely Remove".

"Computer Janitor" does not help, and in fact many have reported huge problems after running this program, so avoid it... for now.

---

### Post by dragon84 on 2009-08-04
thanks heaps.:D

---

