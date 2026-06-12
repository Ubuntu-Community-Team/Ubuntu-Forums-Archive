---
title: "How to trace GUI locking up?"
date: 2010-01-01
forum: General Help
---

### Post by vayu on 2010-01-01
I just did a fresh install of Kubuntu 9.10. The GUI regularly locks up.  I can SSH to it from another machine everytime it locks up.  Top shows Xorg consuming 99% cpu. I think downgrading the nvidia driver to 173 from 185 helped reduce the lockups. Before they seemed very random and very often.  Now it seems to happen when copying a large amount of files over the network but I'm not entirely sure.  It ran the electricsheep screensaver all day today with no problems and the RSS euphoria GL screensaver all day yesterday.  If I copy 2GB of files from one local directory to another no problem, if I do it through cifs mounted samba shares it will lock up for sure. Small amounts seem ok. Apt-get install has had some lock ups too.

I don't really know how to trace what's going on beyond installing ssh and finding out that it's totally alive inside.  I don't know what to look for in log files nor which ones to look at.  I didn't recognize anything wrong in Xorg log.  In the system log I look for the time gap between when it locked up and I shut down and when I rebooted but I didn't notice anything.

Can someone give me some ideas how to trace this problem?  I've just spent 3 days installing and tweaking a totally sweet setup.

---

### Post by vayu on 2010-01-01
So much for the idea that it's a networking problem. It just locked up while cutting and pasting from one konsole terminal to another.  Those were the only two windows open.  It's always the same kind of lockup.  Fist the mouse and keyboard freeze.  Then the screen blacks out for 20-30 seconds, then it redisplays the frozen desktop.  I can always ssh into at that point and copy lots of files, apt-get install, check out log files, ...

I don't think it's compositing.  I just suspended compositing from the system settings control panel.  Did the 1.9GB copy from a network computer and same lockup.

---

