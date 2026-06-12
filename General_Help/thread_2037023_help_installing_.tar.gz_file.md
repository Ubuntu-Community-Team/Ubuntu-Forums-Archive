---
title: "help installing .tar.gz file"
date: 2012-08-03
forum: General Help
---

### Post by artofshred87 on 2012-08-03
hi i am trying to install the .tar.gz for a clockworkmod tether app from my phone and i dont completely undertstand how to do it. can someone help me? i downloaded the .tar.gz from my phone and then copied it to my computer, inside the .tar's main folder  called tether there are four other folders named as follows common, linux, node, node-tuntap, and  the a read me txt file, that says:

Running Tether on Linux:

# at the top level directory of the package:
sudo linux/run.sh

On the first run of Tether, node.js will be compiled. This will take a few minutes. 

 i have never compiled or installed one of these before and i cant get the app to work without installing it, so any help would be greatly appreciated. TY

---

### Post by ajgreeny on 2012-08-03
It sounds as if there is also a run.sh file in the folder you mentioned, /linux, so using a terminal navigate to the folder called tether; if it is in your home folder you need to use command ```
cd tether
``` then according to the readme file use command ```
sudo  linux/run.sh
```

Don't forget that linux is case sensitive, so should the top folder be Tether, not tether, you will have to use the correct case for the names of all files and folders.

PS:  I have no idea what that application is, or even if it is possible to find a deb file to install, so it may be worth a search first.

---

### Post by artofshred87 on 2012-08-04
hi Aj,  thanks for your help i figured it out. it seems i was opening the wrong directory when doing the ./configure and make part.

---

