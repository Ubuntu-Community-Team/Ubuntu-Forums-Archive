---
title: "KVIrc and Xorg, a slowdown story..."
date: 2011-01-05
forum: General Help
---

### Post by Meshaal on 2011-01-05
Hi all,

I've noticed on occasion that KVIrc slows down when it has been running for a long period of time.  However, this is normally easily solved by closing and restarting the program.

However, earlier today, I attempted to start and use KVIrc, and it was running at unusable speeds.  It took over three minutes for me to connect to all my ajoin channels (about 40), and a further two to three minutes for them all to synchronize.  Following that, it was still unusably slow: it'd take about 20 seconds to change to another channel after clicking on it in the channel list, and typing messages proved nearly impossible, as characters only appeared in the message field about a half-minute behind my typing them.

Determining that it was not my internet connection that's the issue, and that KVIrc has been running fine up until today, I looked for solutions.  I restarted (to no avail), uninstalled KVIrc (backing up my settings) and reinstalled, and then tried "complete removal" from Synaptic and then reinstalled, each to no avail, and even tried removing my extensive log history, wondering if the ~60MB of text files was slowing it down somehow.  Nothing worked.

Probably late, I started it up and ran a [FONT="Lucida Console"]top[/FONT] command in Terminal, and noticed that Xorg (which [this thread](http://ubuntuforums.org/showthread.php?t=955672) enlightened me about) was running at near 100% CPU usage.

Browsing through that thread, most of the suggestions indicated something to do with graphics card issues, and suggested disabling graphics effects.  However, my graphics card (some integrated Intel product which I forget how to get the specific name of) is blacklisted by Compiz, so my graphics effects are already entirely disabled.

I really don't want to have to switch IRC clients, having extensively configured KVIrc to suit my needs.  Given it was running just fine until today, I'm really hoping someone may be able to help me get it running smoothly again.

Thanks!

---

### Post by Meshaal on 2011-01-06
Hate to bump this, but it's falling a bit behind... :(

---

### Post by Sarteck on 2011-01-12
Oi, no fix for you I'm afraid, just letting you know that I'm in the same boat.

I'm using KvIRC 4.0.0 (4.0.2 is not in the repositories).

I have recently updated a lot of packages, and after that is when I noticed KvIRC crawling to a halt.  :<

It's my favourite IRC Client, too, but at this rate, I'll have to switch to something else.

---

### Post by Meshaal on 2011-01-12
> **Sarteck said:**
> Oi, no fix for you I'm afraid, just letting you know that I'm in the same boat.

I'm using KvIRC 4.0.0 (4.0.2 is not in the repositories).

I have recently updated a lot of packages, and after that is when I noticed KvIRC crawling to a halt.  :<

It's my favourite IRC Client, too, but at this rate, I'll have to switch to something else.

Thanks for the reply.  After a few days, I installed xchat, and I'm finding it to work alright, though I still prefer KVIrc.  Going to keep both installed, and I'll be keeping an eye on updates to see if I can find anything to fix it.  If I can, I'll make sure to post again here to let you know. :)

---

### Post by Sarteck on 2011-01-12
I've been trying out Quassel and Konversation.

Quassel seems to be VERY limited in terms of customizing the looks, and I really need my colour scheme.  XP  You seem to only be able to change the background colour for the output window (not the nick list, input area, or channel list).  Couldn't stand using it for too very long.  >.>

Konversation is a bit better, but has this annoying bit where it tries to explain to you in plain English what's happening in the channel (like, "you have been granted channel owner by blah blah blah" instead of "ChanServ sets mode +q Sarteck").  I prefer the simpler way.  Maybe I'm just picky that way.  XD  Also, it doesn't nestle into the system tray, like Quassel and KvIRC do--it acts like any other regular window.  :<

KvIRC has a lot more customization options and different levels of highlighting and so on and so forth.





I have tried xChat in the past, and it was okay... before I found KvIRC.  (It might be a lot better now, I don't really know).



Some good news, though...  I went to the KvIRC site and downloaded the 4.0.2-1 files (both the main package and the data files), and installed them:

```
sudo dpkg -i kvirc_4.0.2-1_i386.deb kvirc-data_4.0.2-1_all.deb
```

It's been running so far with none of the errors I was having before, for about half an hour.  (I know that's not a very reliable tiemframe for testing, but half an hour into my old 4.0.0 and I was already typing half a minute ahead of where my cursor was at, and I'm a slow typist.)

If I don't come back to this thread and post differently, you can safely assume that I'm happily running that new version.  If that's the case, maybe it'll work for you.

---

### Post by Meshaal on 2011-01-12
Thanks!  I'll try installing it tomorrow when I'm less sleep-deprived :P

Edit: Seems to be working for me, too.  Thanks again for the help; issue solved :)

---

### Post by Sarteck on 2011-01-12
Just confirming that after upgrading and letting my IRC run for a whole night, KvIRC seems to be working as normal.  :)



I'm not sure how we go about getting the newest version included in the Repositories, but if anyone reading this does know how, it would probably be a cool thing to get 4.0.2-1 into the repos so others don't have the same issue.

---

