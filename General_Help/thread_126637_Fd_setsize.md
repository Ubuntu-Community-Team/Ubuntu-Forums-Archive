---
title: "Fd_setsize"
date: 2006-02-07
forum: General Help
---

### Post by xelix on 2006-02-07
Im running Ubuntu 5.10 and im trying to raise my ulimit. I already set everything in limits.conf and changed the __FD_SETSIZE in typesizes.h. But when I try and start my UnrealIRCd I still get an error...

MAXCONNECTIONS (5000) is higher than FD_SETSIZE (1024)

How do I raise this...I already changed the __FD_SETSIZE in typesizes.h, I thought thats all I needed, but I guess it's in another section. Anyone know how to raise the FD_SETSIZE? thanks

---

### Post by nanotube on 2006-02-07
did you recompile your program after changing the .h header file? header files are not like conf files, you have to recompile the program for the changes to take effect. 

also, as to the file you need to change, might want to check out this link:
[http://64.233.179.104/search?q=cache:3SpMbN9zwSEJ:newton.gra2.com/unreal32docs.html+FD_SETSIZE+UnrealIRCd&hl=en&gl=us&ct=clnk&cd=7&client=firefox-a](http://64.233.179.104/search?q=cache:3SpMbN9zwSEJ:newton.gra2.com/unreal32docs.html+FD_SETSIZE+UnrealIRCd&hl=en&gl=us&ct=clnk&cd=7&client=firefox-a)
(search for section that mentions FD_SETSIZE).

---

### Post by xelix on 2006-02-07
Yeah I recompiled the program, but still didnt work. I'm going to check out this link you posted, thanks for the help. If anyone else has any comments, it would be much appreciated, thanks in advance.

---

