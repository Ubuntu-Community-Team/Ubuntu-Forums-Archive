---
title: "Javascript Adobe Reader problem in some linux distributions"
date: 2011-11-17
forum: General Help
---

### Post by TheSil on 2011-11-17
Adobe Reader doesn't execute initial javascript code of 3D scene in pdf document. With friends we've tested several linux distributions, namely CentOS, Ubuntu, Arch Linux, Mandriva, OpenSUSE. Also several Adobe Reader versions like 9.4.6 or 9.1. No luck. For some reason though, it works fine in Fedora (with exactly the same Adobe Reader). Here is an example pdf for test: [http://www.2shared.com/document/LIbyWm_l/mysterious_dice.html](http://www.2shared.com/document/LIbyWm_l/mysterious_dice.html) . Just open the mysterious_dice.pdf and you should see a rotating dice. If you dont, javascript wasn't executed properly (it should be easy to check in Windows 7/XP or Fedora). 

We thought that something is wrong in Reader settings (like disabled javascript), but javascript was always allowed. Then that maybe it is linux Adobe Reader bug, but again, why does it work in Fedora? So maybe some package(s) or something.

Another example is the Asymptote application, which uses javascript at the beginning for some scene settings (lights, camera position, etc) and especially with orthographic projection this problem shows up. More about this here: [http://sourceforge.net/projects/asymptote/forums/forum/409349/topic/4021157](http://sourceforge.net/projects/asymptote/forums/forum/409349/topic/4021157). 

Any idea what might be wrong with this? I will just add that javascript later on works, only the initial code is ignored. Thanks for any suggestion. :(

---

### Post by TheSil on 2011-11-18
Alright, we managed to fix this behaviour, turned out that this is a problem on non-english linux systems  with linux Adobe Reader. It has something to do with LC_NUMERIC  variable, seems like Adobe Reader bug. Solution is to either use english  system language or just run Adobe Reader with command like this:
 
LC_NUMERIC=C acroread
 
and then it works fine on non-english systems.

---

