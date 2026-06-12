---
title: "wolfenstein enemy territory error"
date: 2009-08-15
forum: General Help
---

### Post by Eurysan on 2009-08-15
i have been getting a error that i cant find anywhere els or any info on so ill ask you guys 
i managed to get my graphics card to work i use ati radeon Xpress 200m 

and when i install in terminal it tells me to intall as super user so i entered the password and then it gives me this error

im using ubuntu 8.10

It is recommended to install as super user
Please enter password or hit enter to continue as is
Password:
/root/.setup5837: error while loading shared libraries: libgtk-1.2.so.0:cannot
open shared object file: no suck file or directory
the setup program seems to have failed on x86/glibc-2.1


im a new ubuntu user so im not exactly sure whats wrong any help would be nice

---

### Post by whitethorn on 2009-08-15
Well it seems like your missing some libraries.  If you go to System -> Adminstration -> Synaptic Package Manager, you can browse all the programs/libraries.  Just type in the searchbox, libgtk   What ur looking for is something called libgtk1.2    not sure if you need the libgtk1.2-dev. Give it a try, what's happening is that the program is trying to use a certain library which you haven't installed yet.  You might get a couple more dependencies, just use synaptic and search for em.

---

