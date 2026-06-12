---
title: "Gtk Radiant Trouble"
date: 2006-03-26
forum: General Help
---

### Post by amunimanghi on 2006-03-26
Hi,

I downloaded gtkradiant 1.4.0 for linux. I installed it (see picture) and at the end of the installalation, clicked finish. It didnt load up. 

i opened the terminal and typed ```
{username}@ubuntu:/usr/local/bin$ ./radiant
```
this came up: ```
./radiant.x86: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```

i did sudo /usr/local/bin$./radiant, but i still get the same problem.

i open up synaptic and tried to get libgtk2.0-dev and other *****-dev files. when ever i mark it it complains about dependencies.
 ```
libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.6-0ubuntu2) but 2.8.6-0ubuntu2.1 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libcairo2-dev but it is not going to be installed
```
and that just keeps on going. i tried to mark 4 different ones, all came up with the dependencies problem. if the linux version isnt good, i will go as far as to download the windows version. 


can someone help me. i originally wanted to just use gtkradiant to make some maps for star wars jedi academy but now im on an expedition. :p

---

