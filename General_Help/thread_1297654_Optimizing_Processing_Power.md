---
title: "Optimizing Processing Power"
date: 2009-10-22
forum: General Help
---

### Post by rezapiri09 on 2009-10-22
I find it difficult to optimize my processing power while running awn and using crossover applications to run MS word, excel, and powerpoint.   When I run Firefox with all my extensions it becomes an even bigger cluster that pretty much runs my machine into the ground.  When I look inside htop to kill the power sucking applications I find this piece of code that says this:

/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm : 0.xauth -nolisten tcp vt7

F9 (kill tab) doesn't work so what can I do to kill it?  Can anyone tell me what in the name of sweet baby jesus does this do and why is it eating up my CPU?   I have tried to google it, but can't find real answers. I also tried restarting, but it runs on startup.  

What else can I do to optimize my processing power for faster web browsing, managing applications, and running multiple desktop environments?  Thanks in advance

---

### Post by aesis05401 on 2009-10-22
That is X : [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

The wiki article does a better job explaining the many issues that surround X than I could in this post.  Best of luck.

---

### Post by P4man on 2009-10-22
can you launch system monitor, go to processes, select view all, sort by memory usage and post a screenshot?

Its kinda hard to say if there is anything you can do. If you're trying to run a ton of bloated windows apps on top of a windows emulation layer on top of an OS with less than 512Mb ram, I guess the short answer is you cant. Use OpenOffice or run your windows software on windows.

But its also possible you're encountering a memory leak. If the xorg process is taking >100Mb then is something is wrong.

---

### Post by rezapiri09 on 2009-10-22
> **P4man said:**
> 
  If you're trying to run a ton of bloated windows apps on top of a windows emulation layer on top of an OS with less than 512Mb ram, I guess the short answer is you cant. 


I've got 2G of mem and intel core duo @ 1.6 GHz each.  I've got the power, but for some reason this bloody Xorg is sucking down my power. At the moment I am only running firefox and the system monitor, but it is taking up 30% of my CPU.  when sitting idle it does an even 14-20 % and when I start activating programs is really goes off the charts.  any suggestions?

---

### Post by P4man on 2009-10-22
Keep in mind your cpu likely clocks down to 800 Mhz or so on light loads, so 30% isnt quite as much as you'd think.

Still,Im gonna guess: you have an intel onboard videocard and you got desktop effects enabled. If so, there are a gazillion threads and bug resports about that combination, but your best bet is probably waiting for karmic as it will have much better support for onboard intel graphics.

---

### Post by rezapiri09 on 2009-10-22
Sound advice P4. Thanks!

---

