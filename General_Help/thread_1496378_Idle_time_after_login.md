---
title: "Idle time after login"
date: 2010-05-29
forum: General Help
---

### Post by eev2 on 2010-05-29
Hi all, I'm observing about 20 sec idle time after I log-in until the autostart applications start. I mean, I see the desktop and the panels and after ~20 sec the application icons start appearing in the notification area. I was wondering if you could help me diagnose what is causing this. I can't see any action when I use the top command during the idle time. Any ideas? I have xubuntu 10.4.

---

### Post by eev2 on 2010-05-30
Hey guys, anyone can help me with this?

---

### Post by Soul-Sing on 2010-05-30
afaik you have to disable the floppy disk drive option in your bios.

---

### Post by eev2 on 2010-05-30
Hey thanks for replying. I know about the issue that you mentioned but I don't think this is the problem in my case. In the case of the floppy, the delay is caused due to the fact that the system is trying to mount the floppy disk but judging from a recent bootchart I made, my mount commant is not slow. See here 
[http://i.imgur.com/vfhBE.png](http://i.imgur.com/vfhBE.png)
Also, I don't have a /dev/fd0 file. 

From the bootchart, is ifup supposed to take so long? Is is a problem with the network device?

---

