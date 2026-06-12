---
title: "cpu overload, harddrive always buzy, gconfd2 and metacity"
date: 2010-09-07
forum: General Help
---

### Post by xiboce on 2010-09-07
When login into Ubuntu netbook remix 10.04 with "compiz --replace" , "emerald --replace" and "avant-window-navigator" as additional autostart programs causes :
1) CPU overload ... most possibly from _gcond2_
2) hard drive constantly buzy/ in use .... even when machine is innactive
3) performance issues (slow)

So when i searched the forum i found 
[http://ubuntuforums.org/showthread.php?t=349485](http://ubuntuforums.org/showthread.php?t=349485)
[http://ubuntuforums.org/showthread.php?t=1028207](http://ubuntuforums.org/showthread.php?t=1028207)
[http://ubuntuforums.org/showthread.php?t=1254418&highlight=gconfd2](http://ubuntuforums.org/showthread.php?t=1254418&highlight=gconfd2)

which led to 
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/389686](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/389686)

Upon reading the comments section people suggest:
1) run "killall metacity"
2) remove the compiz manager icon from autostart
3) run compiz /emerald with --replace 

With regards to my situation:
1) killall metacity does not work for me,
2) compiz manager icon is not autostarting nor its running in the background
3) i have both compiz and emerald executing with the "--replace" option.

My workaround:
Thinking it is metacity related I installed _xfce4_

Booting into an xfce4 session with compiz --replace" , "emerald --replace" and "avant-window-navigator" as additional autostart programs solved the problem, specifically
1)gconfd2 does not appear when i run "top"
2) hard drive is not constantly in use
3) CPU is not overloaded anymore

However now i need to fix:
[http://ubuntuforums.org/showthread.php?t=1569707&highlight=xfce4+autostart](http://ubuntuforums.org/showthread.php?t=1569707&highlight=xfce4+autostart)

---

### Post by mhagger on 2010-09-14
This sounds like [a problem that I was having]("https://bugs.launchpad.net/ubuntu/+source/sawfish/+bug/453115").  The cause of the excessive CPU was that metacity was rapidly being started then dying because another window manager was already in use.  Because each metacity process lived for only a short time, it did not show up in the output of "top".

Maybe that helps...

---

### Post by xiboce on 2010-09-15
However ... in my case, metacity does not terminate when emerald is in use. It still shows up in "top", its usually on the top 3 processes consuming quite a bit of CPU

---

