---
title: "And again: Desktop versus Server"
date: 2009-12-27
forum: General Help
---

### Post by umeboshi80 on 2009-12-27
Hi

I am a total newbie and I hope I am not repeating an endless question. 
The main use of my computer will be to run heavy simulations and I would
like to be able to monitor those remotely of course. 
Will there be a big disadvantage if I install Desktop and not Server? I am not sure I can
handle things without a GUI yet but on the other hand running time is crucial.

Any suggestions as to what is best to do?

Thanks a lot! Much appreciated!

---

### Post by howefield on 2009-12-27
A gui can be installed in the server version until you get more comfortable with the terminal.

Likewise you can start with the desktop and add the server packages required.

Maybe start with the server edition and add a lightweight gui.

---

### Post by dcstar on 2009-12-27
> **umeboshi80 said:**
> Hi

I am a total newbie and I hope I am not repeating an endless question. 
The main use of my computer will be to run heavy simulations and I would
like to be able to monitor those remotely of course. 
Will there be a big disadvantage if I install Desktop and not Server? I am not sure I can
handle things without a GUI yet but on the other hand running time is crucial.


Unless you are **using** the GUI then it will not consume resources. There is no "big" disadvantage apart from using a bit of disk space for the packages.

You can even install the server kernel that will perform (slightly) better than the generic kernel for non-GUI use.

---

### Post by jim_charlton on 2009-12-27
I find that there are a ton of kernel modules loaded with linux desktop version, especially dealing with the sound system, that are not required on a server.  You can disable them by copying the files from /lib/linux-sound-base/* to /etc/modprobe.d/.  This will blacklist the sound modules and prevent them from loading.  I have no data to prove that this frees up resources... (I should have checked)... but it seems like it should.  I have 1.2.31-16-generic pae running on my server and I find that gdm eats up a lot of cpu cylcles.  But you can easily just turn it off with "stop gdm" and if you need it you can restart with "start gdm".  YMMV! :-)

---

### Post by dcstar on 2009-12-27
> **jim_charlton said:**
> I find that there are a ton of kernel modules loaded with linux desktop version, especially dealing with the sound system, that are not required on a server.  You can disable them by copying the files from /lib/linux-sound-base/* to /etc/modprobe.d/.  This will blacklist the sound modules and prevent them from loading.  I have no data to prove that this frees up resources... (I should have checked)... but it seems like it should.  I have 1.2.31-16-generic pae running on my server and I find that gdm eats up a lot of cpu cylcles.  But you can easily just turn it off with "stop gdm" and if you need it you can restart with "start gdm".  YMMV! :-)

xorg consumes less than 1% of CPU when sitting at the login screen on my system, so if you have more use than that from an essentially dormant process then you have something wrong with your system.

That basic facts still are that installing any desktop GUI will not make any **significant** difference to resource usage until actually used.

This is not the early 1990's when every MB of RAM or disk space is precious, any modern system has more than enough resources as well as the ability to swap out any unused modules when necessary, so the "freeing up" of resources by not installing a GUI is really an illusion.

---

