---
title: "CPU Governor"
date: 2010-05-11
forum: General Help
---

### Post by jsevi83 on 2010-05-11
Hi, I have a laptop and my cpu is using the default ondemand governor. I would like it to switch to powersave when I unplug the AC cable, and switch back to ondemand when I plug it again.

I know how to make this manually, but I would like to know if there is a way to make it happen automatically. Thanks.

Ubuntu Lucid 64bit.

---

### Post by 3rdalbum on 2010-05-11
I don't know how to set this up to happen (probably requires a Udev rule, which is beyond my knowledge), but Intel recommends leaving the computer at "OnDemand".

When the computer is not working hard, it will use the same power as "Powersave". When the computer is at high load, it will bump up the CPU speed to get the task finished quickly and get the CPU back to sleep as quickly as possible. If you were using Powersave, the CPU would be awake and slogging away for longer; this is inefficient because the trick is to make the CPU *sleep* as much as possible.

---

### Post by jsevi83 on 2010-05-12
Does this apply to situations like watching a movie? The movie won't be finished earlier because of using a faster governor, and I guess the processor cannot go to sleep while playing a movie.

The same applies to the flash player, if I spend all the time watching videos in youtube, with the processor in ondemand the battery will drain faster, as the task doesn't seem to be finished, so there are no chances to sleep.

But I don't really know, so any information is welcomed.

---

### Post by a-user on 2010-05-12
you guess wrong. if the cpu is not much used the cpu freq starts to drop after it first jumps to max (thatrs on demand behaviour).

edit: there is a gnome panel-applet you can add with that you can change the governour.

---

### Post by jsevi83 on 2010-05-12
Well, my processor is intel i5 430m and I'm using Ubuntu Lucid Lynx 64bit. I don't know the theory very well, but I can say that my battery lasts half an hour longer (at least) when using powersave governor. The main use is web browsing, watching videos, listening to music...  Maybe there is something I am missing.

---

### Post by jsevi83 on 2010-05-15
So anybody else is recommending to stay with ondemand governor on battery? On the other hand, how would I make the cpu governor to change automatically to powersave when ac cable is unplugged?

---

