---
title: "lightning extension on thunderbird: where is the data saved ?"
date: 2011-03-05
forum: General Help
---

### Post by then_dude on 2011-03-05
hello people,

in my home folder i have the /.thunderbird folder, and in this folder i have the profile. ini, i have changed some things in this ini folder so that i can put my data on another partition. now i have installed lightning, i wonder where that data is installed ?

are all extesions of thunderbird installed and safed under the directory specified in the profile.ini ? or does lightning safe the appointments somewhere else. 
thanks so much

---

### Post by peculiar penguin on 2011-03-05
Unless you really broke things, it's going to be in the profile directory. Look for a file named storage.sdb, which is the internal calendar data in SQLite format.

---

### Post by then_dude on 2011-03-05
yes i have found it, thanks a lot, so the data is safe, if something should go wrong with the boot partition. 

thanks again
greetz

---

