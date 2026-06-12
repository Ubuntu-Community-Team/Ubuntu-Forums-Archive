---
title: "Can't find an application on ubuntu 8.10"
date: 2009-07-01
forum: General Help
---

### Post by g35celicaz on 2009-07-01
I just installed LogMeIn Remote Control on my laptop and i cannot find it. I am sure I installed I went to synaptic package manager and it said i installed it but i cant find it!

Do you guys know where I could find it?

 - Thanks

---

### Post by abhi_69 on 2009-07-01
do u try via console? is it a terminal based software?
u can try this-
***********
$ sudo which yoursoftwarename
*********
this will show u the path of the apps if it installed correctly.

---

### Post by 3rdalbum on 2009-07-02
You can get Synaptic to tell you where it is.

Go to Synaptic, do a search for the package name. When you have the package displayed in the list, right-click it and choose Properties. Go to the Installed Files tab.

The executable will be in a directory that has /bin/ in its name. (like /usr/bin/)

---

