---
title: "Ubuntu runs slow after update?"
date: 2011-07-18
forum: General Help
---

### Post by ferret_ on 2011-07-18
Hi all, I installed ubuntu 10.04 and then updated my system with gui, now it's running slow like a second or two sometimes for apps to respond? wonder if anyone can tell me what's up?

---

### Post by Paventhan on 2011-07-18
try to uncheck unnecessary things from System->Preferences->Startup Applications

---

### Post by ferret_ on 2011-07-18
Don't think it's that Paventhan, the menu is slow and general apps like firefox, well basically the system is slow. Worked fine before...if i revert back to the older kernel it works fine?

---

### Post by dmikulec on 2011-07-19
I'm having the similar problems: slow to boot and slow to launch applications. In one third party app the cursor lags the mouse by 1 sec or more. Also, strange behaviors with the window manager (dash panels slow to load at boot and sometimes disappear after application actions). In syslog there are many events for notebooks (e.g., battery).

---

### Post by cipherboy_loc on 2011-07-19
Have you tried logging into the Ubuntu Classic desktop environment, and do the problems persist there? Also, try opening up the system monitor and look for the process that is using up the CPU. 


Cipherboy

---

### Post by dmikulec on 2011-07-19
Thanks for your response. I'm using Gnome. Please correct me if that is not the Classic DE. There are no cpu hogs on the system. I'm doing basic stuff with Firefox using ~25% cpu and everything else much less. Regardless, the DE is not part of the slowness to boot. I suspect that the presence of the notebook references in syslog is an indicator that something is wrong with the build. I did an upgrade from 9.10 but didn't see or select any options for a notebook.

---

### Post by cipherboy_loc on 2011-07-20
Two things come to mind:

1) The disk read/write is slow. Not likely, with the specs you listed in your signature.
2) The graphics driver (nVidia?) is slowing down your system, maybe due to incompatibility. 

Also, can you post a copy of that syslog line?

Cipherboy


P.S. GNOME is the classic DE.

---

### Post by dmikulec on 2011-08-07
Sorry for not replying earlier. The problem has disappeared. I didn't do anything so I wonder if an update made changes that corrected the boot issues. Otherwise, the performance issue was caused by a conflict between OpenJava and SunJava. Thanks for paying attention to my post. 

Don

---

### Post by ottosykora on 2011-08-07
>a conflict between OpenJava and SunJava.<


oh, interesting! I had this issue long time ago on some 8.04 or 8.10 too and took me long time to figure out. I thought this was not an issue to day any more, but seems it still is.

---

### Post by boscharun on 2012-02-24
Last time my ubuntu went slow after upgrading from 10.10 to 11, there  was a performance issue with feeling a lot sluggish. For me the issue  was with compiz. I had the effects set to the medium one and when I  switched to "no effects" sanity came back :grin:
Still it was good actually because found out about lots of ideas to make things better. Here's a consolidation to [speed up ubuntu]("http://www.skipser.com/p/2/p/speed-up-ubuntu.html").

---

