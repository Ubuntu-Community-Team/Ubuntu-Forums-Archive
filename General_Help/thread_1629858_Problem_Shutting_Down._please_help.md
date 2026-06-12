---
title: "Problem Shutting Down. please help"
date: 2010-11-24
forum: General Help
---

### Post by Glen Montanaro on 2010-11-24
Hi, I'm new to Ubuntu and i'm having some serious problems.

Everytime i get to shutdown Ubuntu 10.10 It starts closing all apps etc... but then instead of turning off the machine it just switches off the monitor but clearly the machine is still on. 
I'v given it loads of time but it still dosen't turn off the machine just the monitor. Then after i pull the plug on the next start ubuntu has to run disk checking (i'm assuming that it runs disk checking because i pull the plug).

Can anyone tell me why it isn't making a proper shutdown???

Tnks,
Glen

---

### Post by eric3_14159 on 2010-12-23
It sounds like a program is hanging for some reason, that is, during the phase where Ubuntu sends kill signals to all of the applications, one or more stop responding.

Your best bet is probably to edit /etc/default/bootlogd as root. There, change "BOOTLOGD_ENABLE=No" to "BOOTLOGD_ENABLE=Yes". Now, the programs that are run and whether they are successful on startup will be stored in /var/log/boot. I believe that there will also be similar messages for shutdown, which ideally should look something like (just for example):

* Stopping apache2...             [ OK ]
* Stopping program_that_is_broken...

Whatever the last few lines in the file are should show you what program won't shut down properly. Depending on what it is, you could uninstall it, stop it manually before powering off, or possibly look for a bug fix.

Good luck!

---

