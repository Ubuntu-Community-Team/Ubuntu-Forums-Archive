---
title: "program convert consumes most of my computer's memory"
date: 2010-10-05
forum: General Help
---

### Post by batman34 on 2010-10-05
Hello,
I am using ubuntu 10.10 with gnome desktop on a desktop computer (pentium 4 cpu with 1 Gb memory), and when I use OpenOffice Impress, convert opens up and uses most of my cpu power. Even worse, after closing OpenOffice and all instances of nautilus, convert stays in memory and keeps using most of my cpu power (between 30 and 75 %, acccording to system monitor.
Is it normal ? How could I set up my computer to limit convert cpu usage, and to unload from memory after being used.
Thanks for any help that could be given.

---

### Post by batman34 on 2010-10-08
> **batman34 said:**
> Hello,
I am using ubuntu 10.10 with gnome desktop on a desktop computer  (pentium 4 cpu with 1 Gb memory), and when I use OpenOffice, convert  opens up and uses most of my cpu power. Even worse, after closing  OpenOffice and all instances of nautilus, convert stays in memory and  keeps using most of my cpu power (between 30 and 75 %, acccording to  system monitor.
Is it normal ? How could I set up my computer to limit convert cpu usage, and to unload from memory after being used.
Thanks for any help that could be given.

Hello everybody,
A great thanks to all that have checked my first message :smile:. 
But I renew my question, because this problem impairs a lot the use of my computer :sad:;  at the moment, the only solution that I have found is to force unload  of the convert program from memory through the use of system monitor; it  works, but I would prefer a systemic solution, even better a solution  that could also limit the consumption of cpu power, even when convert is  used by OpenOffice.
Thanks for your help.

---

### Post by UnterUn on 2010-10-08
Hey! I found this which may help:
                 [http://ubuntuforums.org/showthread.php?t=1289166](http://ubuntuforums.org/showthread.php?t=1289166)

---

### Post by batman34 on 2010-10-08
> **UnterUn said:**
> Hey! I found this which may help:
                 [http://ubuntuforums.org/showthread.php?t=1289166](http://ubuntuforums.org/showthread.php?t=1289166)

Thanks for your help. In the meantime, I installed LibreOffice from the Document Foundation; and when used in place to OpenOffice, this solved most of my problem; in particular, once my document loaded, convert exited and no longer stayed in memory; this suggests that there was a configuration problem in OpenOffice.

Anyway, thanks for this link; I think the cpulimit program might be an interesting solution for a similar problem.

---

