---
title: "Ubuntu 9.10 64 bits Freeze, crash, OOM Killer"
date: 2010-04-13
forum: General Help
---

### Post by Eul_Mulot on 2010-04-13
Hi everybody !

I was happily running Ubuntu 9.10 since Mars, without a problem, and since last sunday, I have some issues: I let my computer run 24H a day, and when I woke up on Sunday the computer was frozen, mouse frozen, need to restart it. On monday Same thing I leave it for 3 hours idle, come back, and only the desktop background was left and everything frozen too. I don't remember a special update since the changes, but kind of remember while installing OOo 3.2 that he warning me about so issue, in case of issues I should remove some package ...

I decided to go to see the logs, but not very sure which ones, and found different things like dbus having a segfault, or Xorg invoked oom-killer. (logs at the end of the post).

So yesterday night I decided to reinstall Ubuntu on my / and keep my older /home, so I reinstall all the binaries and did all the updates (I didn't install pre version of the system).

Once everything is set up, seems to work fine, until this morning whne i watched TV online through VLC, and crash the computer,I tried two times in a row, two times crash in a very short time.

I also did a complete pass of Memcheck on my 2GB DDR, I have a swap of 1.9 GB so I don't get the invocation of oom-killer .

I would really like some help because I'm new to Ubuntu and Linux systems in general, and not very able to see direct problems in the messy logs.

Some part of log that may be interesting (or not ! ;) attached)

On the "old" system. (supposed time of crash since I wasn't there)

On the new system already 2 crashs.

The second crash one seems really similar with the log to the first one ...

I really don't get what is happening, is there a good way to diagnosis what is wrong with my system ? I would prefer not to return on 7, or worst, Mac Os ! ;)

---

### Post by Eul_Mulot on 2010-04-14
Apparently those weird crash were due to a massive dust inside the computer. Don't ask me why but the memory was totally out of control during a memetest, once cleaned, nothing.

---

