---
title: "Trying to locate SDLMAME executable"
date: 2010-03-16
forum: General Help
---

### Post by blazini on 2010-03-16
I'm trying to get the frontend setup for sdlmame but it needs the location of the executable. I tried to locate through the terminal but the output isn't really gettimng me anywhere. Anybody know where they hide the executables? 

Four years of running Ubuntu and I still really don't understand the placement of files. That's probably the one thing I liked about Windows, the program files were in "program files" lol.

---

### Post by rnerwein on 2010-03-16
hi
i'll try to help you with the understanding of "unwritten rules in unix/linux". i'm running unix since about 25 years and my experience is:
/sbin        --> system administrator commands, come with the os
/usr/bin    --> is what the path tell you, common commands, coming with the os.
/usr/local/bin --> commands coming from third parties, or own written commands.
/usr/sbin   --> comming from third parties, realy system depending 
/opt/bin --> third parties, mostely system depending commands ( often saw databases there )
/etc       ---> sometimes system commands ( i think they don't have to place there.

for your problem with SDLMAME ( i don't know this software ) try:
cd /
sudo find . -iname "*sdlma*"
may be this help you
ciao

---

### Post by blazini on 2010-03-16
Thanks for the explanation. I usually have a general idea of where to find what I'm looking for but sometimes I just have to poke around for a while.

I figured it out though. I had just upgraded the package and It's no longer named SDLMAME, everything is just MAME now. Seems they've unified everything for this release.

---

