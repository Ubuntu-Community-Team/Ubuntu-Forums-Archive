---
title: "Cpu1 100% overload then cpu1 without run any program ???"
date: 2010-09-25
forum: General Help
---

### Post by firefox66 on 2010-09-25
Hi all !

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170482&stc=1&d=1285431063[/IMG]

Looking for my process monitor you see that i didn't run any program but my CPU01 100% overload and fax worked a lot,CPU02 just a bit.Ram's just 12%.

So what i when wrong ??? it is a bug.
I install Ubuntu 10.04 x64 - ram 4Gb - Nvidia quadro 140M.

Firefox66

---

### Post by MooPi on 2010-09-25
Can you show us the processes that are rumnning ? Please use terminal and ```
top
``` command. The resource monitor for Ubuntu isn't the best tool to view a resource hog because it too is a hog.

---

### Post by firefox66 on 2010-09-25
> **MooPi said:**
> Can you show us the processes that are rumnning ? Please use terminal and ```
top
``` command. The resource monitor for Ubuntu isn't the best tool to view a resource hog because it too is a hog.

when i restart and it stand down.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170484&stc=1&d=1285431784[/IMG]

i run acrobat reader and load page per page and then close it when cpu overload then it still overload cpu.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170485&stc=1&d=1285432051[/IMG]

I wonder why it is cpu01 instead of both cpu1 and cpu2.

Thanks,Firefox66.

---

### Post by luvshines on 2010-09-25
Did you run any command/tests before you see the 100% usage in the first place ?

---

### Post by MooPi on 2010-09-25
This is due to the reader being a single threaded application and it can't utilize multiple cores. Not many applications do utilize multiple cores yet, but this will change over time as they evolve. You probably don't have a serious issue just acrobat being hoggish.
Try evince to view your pdf files and see if there is a difference. Evince is the default pdf viewer in Ubuntu and should use less resources.

---

### Post by firefox66 on 2010-09-25
no i'v just run firefox view acrobat file on website then i reconigze that fan work alot so i open monitor view what process but not thing hapen.i'v closed firefox and looked monitor,it still overload cpu01 100% and cpu02 12%,ram nomarl as you'v seen in the fist picture.

i think it have bug in cpu load manager on ubuntu 10.04.

Firefox.

---

