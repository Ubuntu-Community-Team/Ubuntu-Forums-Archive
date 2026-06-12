---
title: "Opera - No Response"
date: 2010-08-27
forum: General Help
---

### Post by xkenshin on 2010-08-27
Hye, 
I'm using Ubuntu 10.04 with Opera 10.61. 
Whenever i'm using the Opera, there's no problem, everything works fine and perfect. But when i'm not using the PC for a while, it will goes into a sleep mode which is normal. And when it wakes up, the Opera browser doesn't respond to any mouse click or keyboard press. (it's like loosing focus) I had to close the Opera and open it back. (Restart Browser). Anyone with the same experience? How do i prevent this? Help!

---

### Post by azertyh on 2010-08-27
hi,
alt+tab to switch to opera doesn't work?

---

### Post by DogMatix on 2010-08-31
Hi

I am also using Opera 10.61 in Ubuntu 10.04 an I am having the identical problem that you are. I have been digging around trying to solve it but haven't managed to find a fix yet.

I am a long time Opera user and have been using Ubuntu for about 3 years this problem seemed to start around the Opera 10.5 era.

It seems to be a problem unique to Ubuntu as Opera on my Windows installations nor my Mac suffer.

---

### Post by Soul-Sing on 2010-08-31
Please take a look at your ubuntulogs (system-administration), are there warnings such as =segmentation fault= or similar ones?

---

### Post by DogMatix on 2010-08-31
Yes there are several such as:

> Aug 29 10:04:42 ubuntu kernel: [  142.512944] operapluginwrap[1784]: segfault at 0 ip (null) sp bfa23c3c error 4 in libXt.so.6.0.0[110000+4f000]

EDIT: Similar experiences are documented here and seem to be attributed to plugins. [Opera forums thread]("http://my.opera.com/community/forums/topic.dml?id=646682")

---

