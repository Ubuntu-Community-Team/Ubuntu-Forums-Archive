---
title: "libalter.so.1: cannot open shared object file: No such file or directory"
date: 2010-05-11
forum: General Help
---

### Post by Deks90 on 2010-05-11
Hello!

I've got a problem with running a program called Synapse in ubuntu 10.04.

When i run "runSynapse.sh" script nothing happens. Then i tried running it from terminal with sudo command and this is what i got:

```
error while loading shared libraries: libalter.so.1: cannot open shared object file: No such file or directory
```

I checked the synapse directory but libalter.so.1 was there....:confused:

Can someone help me with this? :( :(

---

### Post by jazzroy on 2011-01-17
I had the same problem, I solved it copying all the libs and the links to the libs that you find in the main folder of Synapse to:

usr/lib

you need admin privileges to do it, so run 

sudo nautilus

to copy them.
then you can run directly "alter" (the executable) skipping the "runSynapse.sh" script

---

