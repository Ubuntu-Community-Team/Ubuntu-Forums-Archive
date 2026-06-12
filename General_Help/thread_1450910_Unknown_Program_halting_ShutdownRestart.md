---
title: "Unknown Program halting Shutdown/Restart"
date: 2010-04-09
forum: General Help
---

### Post by drewsus on 2010-04-09
Hellllllo All!

So, recently I have been plagued with an issue. Whenever I try to **restart** or **shutdown** I am greeted with a popup message telling me that a program is still running and whether I want to shutdown/restart anyway. The program that it says is still running is "Unknown" and "Not Responding." This happens without fail, every single time. 

How can I resolve this/find out what program is causing this issue?
*I have attached a screenshot showing the particular message*

Drewsus

---

### Post by jobix on 2010-04-09
Sorry I don't have a strong suggestion but you could try looking at the log files and see if there's anything relevant there. Look for lines corresponding to the time when you are shutting down.

---

### Post by drewsus on 2010-04-09
Do you have any idea which log files might show this information and where they would be?

Thanks, 
Drew

---

### Post by drewsus on 2010-04-09
So, I checked syslog and noted the time I shutdown. 
First thing I noticed was:
```
Apr  9 18:19:29 drewsus-lite x-session-manager[1569]: WARNING: Client '/org/gnome/SessionManager/Client7' failed to reply before timeout
```

So then I tried just tried shutting down to bring up the "Unknown" popup window and the next 3 times I did it I saw:
```
----first try----
Apr  9 18:26:52 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
----second try----
Apr  9 18:28:04 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
----third try----
Apr  9 18:29:25 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
```

So what exactly is going on here? What might be done to stop this? Is this even the right thing to be looking at?

---

### Post by rwaldo on 2010-12-28
Probably the program TANGERINE.
See [http://ubuntuforums.org/showthread.php?t=1523374](http://ubuntuforums.org/showthread.php?t=1523374)

---

### Post by Chriske on 2011-09-09
> **drewsus said:**
> So, I checked syslog and noted the time I shutdown. 
First thing I noticed was:
```
Apr  9 18:19:29 drewsus-lite x-session-manager[1569]: WARNING: Client '/org/gnome/SessionManager/Client7' failed to reply before timeout
```So then I tried just tried shutting down to bring up the "Unknown" popup window and the next 3 times I did it I saw:
```
----first try----
Apr  9 18:26:52 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
----second try----
Apr  9 18:28:04 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
----third try----
Apr  9 18:29:25 drewsus-lite x-session-manager[1273]: WARNING: Client '/org/gnome/SessionManager/Client8' failed to reply before timeout
```So what exactly is going on here? What might be done to stop this? Is this even the right thing to be looking at?


I had the same problem in the last few days and could not establish the cause.

Using:
[INDENT]sudo apt-get autoremove
[/INDENT]in a terminal solved the problem for me.

---

### Post by Bodsda on 2011-09-09
> **drewsus said:**
> Hellllllo All!
 
So, recently I have been plagued with an issue. Whenever I try to **restart** or **shutdown** I am greeted with a popup message telling me that a program is still running and whether I want to shutdown/restart anyway. The program that it says is still running is "Unknown" and "Not Responding." This happens without fail, every single time. 
 
How can I resolve this/find out what program is causing this issue?
*I have attached a screenshot showing the particular message*
 
Drewsus
 
The popu shows a thumbnail of the problematic app. Can you see the program and interact with it?
 
If so, take a quick dump of the process list, then use xkill to select and kill that app, then run top again, did any processes dissappear?
 
Bodsda

---

