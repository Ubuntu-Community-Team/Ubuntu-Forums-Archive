---
title: "update manager is not launched automatically?"
date: 2009-11-10
forum: General Help
---

### Post by claracc on 2009-11-10
Hallo, i have notice that since last week, it doesn't appear in the bottom panel the minimized window of update manager telling there are available updates.

So, i run manually update manager from system, administration and it shows me all the updates for my software, i can install them without problem.

I have launched gconf-editor, went to apps, update manger, and there, the key corresponding to launch_time shows 1257840857, in the bottom part of this window, it appears an attention sign saying "this key has not scheme", name of the key: "/apps/update-manager/launch_time; owner of the key: none; short description: none; long description: none.Are these values correct?

¿Is there any problem with this key causing update manager doesn't automatically notify me about update as it did one week ago?. Could  this behaviour be the correct one?.

I have karmic koala, upgraded from jaunty two weeks ago. 

Thanks in advance

Clara

---

### Post by RochJer on 2009-11-10
Strange thing has happened to me as well. I was doing the Update Manager and it has listed the updates which it didn't notify me automatically as it should. I checked the update tab for Automatic Update and it is already checked, somehow it won't pop up on the screen. It sounds like a bug or something - I had jaunty as well and it does pop up to me everyday as I set it to Daily for Automatic Update. I am going to report this bug.

---

### Post by claracc on 2009-11-11
Well, this morning, update manager automatically poped up and notified about security updates, i installed them (all about cups). So the problem doesn't exist, perhaps i misundertood the new updates policy (unless i think it is the same as in jaunty?): security ones everyday and the other once a week.

Anycase, i would like somebody answer me about the meaning of the launch_time key and its values, as i asked in the first post of this thread.

Despite of  the "noise" about karmic koala i find that it is a much better release than jaunty, at less for me, now the pulseaudio sound works always (analog devices ad1981 integrated audio card), i can see streaming videos very well (i have the intel graphics card gm965), the fonts and images in firefox are not pixelated or blurred, now they are clear. The stress over cpu is lower than in jaunty and the laptop doesn't heat and software is very stable.

Of course there are some bugs and problems(evolution notifications and panel's indicator applet, totem's plugins for BBC and playing youtube videos,java?..), but in general people behind ubuntu is working better and better.

Thanks

---

### Post by fragos on 2009-11-11
I believe that starting with 9.10 updates are checked for every 7 days by default. You can still run Update Manager but you need to click the Check button to get it to reload the repositories.

---

