---
title: "Abort Shutdown if Apt-Get is Running"
date: 2010-10-26
forum: General Help
---

### Post by xz124 on 2010-10-26
Hey everyone,

I am running KUbuntu 10.10 desktop and I scheduled a cron job to auto-update all packages. I shutdown my computer once while apt-get was updating in the background and had to spend some time using dpkg and apt to fix what happened. Checking every time before shutting down has become a pain. So, is there any way to make init or shutdown check to make sure that apt-get is not running before shutting down?

Thanks :)

---

### Post by ivarn on 2010-10-26
> **xz124 said:**
> Hey everyone,

I am running KUbuntu 10.10 desktop and I scheduled a cron job to auto-update all packages. I shutdown my computer once while apt-get was updating in the background and had to spend some time using dpkg and apt to fix what happened. Checking every time before shutting down has become a pain. So, is there any way to make init or shutdown check to make sure that apt-get is not running before shutting down?

Thanks :)

I have the same question.
This is really something Ubuntu should fix.

---

### Post by katykat on 2010-10-26
The simplest solution would be to shutdown from a script that checks first to see if apt-get is running and aborts if it is. 

Since apt uses a lockfile you can check for the existence of that lockfile in an if-then statement in either bash or perl. 

I'm not on the Linux machine now, so dont know offhand where it is, but if you try to run apt-get while synaptic is running you should get an error message saying where it is. 

My scripting is a bit rusty so i will leave it for someone more skilled than I. 

There is also a neat little applet for the top bar that when clicked will prevent shutdown or sleep mode until clicked again. I have found it quite useful. My sleep mode is not workign right. but thats a problem for another day....

Edited to add: the script should have a basic sleep loop so that it rechecks periodically and shuts down when the installation is complete and the lockfile is removed.

---

### Post by xz124 on 2010-10-27
Is there any way to change what script kdm or kde uses to shutdown? If not, then I'd have to move shutdown and put another one by me in its place and I'd rather not do that in case of updates to shutdown.

---

