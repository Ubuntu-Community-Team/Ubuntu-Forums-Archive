---
title: "Task Manager &amp; msconfig?"
date: 2006-04-03
forum: General Help
---

### Post by dawhoo on 2006-04-03
I've had kubuntu a few days now and I can't believe how great it is.  However, the learning curve is a little steep.

I'm trying to figure out where I can start/stop programs from running at startup and how I can add programs to run at startup - kind of like msconfig. I don't even have a printer, so I think I could get rid of most printer services that are running from boot.

Also, is there a process viewer like Task Manager that will let you close down processes? I read about 'top', but I don't know how to shut down processes.  

I really like the Windows/Linux application comparison charts. Is there one for system processes and commands? It took me a while to find that ipconfig is ifconfig in kubuntu.  

/old dog learning new tricks...

---

### Post by Barrakketh on 2006-04-03
kcontrol -> System Administration -> System Services for services (not to be confused with applications that you launch like amaroK).

And KSysGuard.

Personally, I use the command line ^_^

---

### Post by dawhoo on 2006-04-04
ksysguard - exactly what I was looking for and way more functional than Task Manager!  

NOw all those processes running.... I've got some reading to do.

THanks for getting me pointed in the right direction!

---

### Post by Parkotron on 2006-04-05
Personally I wouldn't worry too mch about removing extra processes, unless your having serious performance issues, especially if you're a new user. But if you do wan to get rid of some system services on boot up, I'd reccomend this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

Oh, and by default you can open a barebones KSysGuard at any time by pressing ctrl+esc.

---

