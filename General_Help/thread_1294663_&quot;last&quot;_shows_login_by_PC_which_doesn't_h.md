---
title: "&quot;last&quot; shows login by PC which doesn't have access or ssh installed"
date: 2009-10-18
forum: General Help
---

### Post by daniel.pool on 2009-10-18
Hi,

I wanted to post about a strange issue that I'm having and can't seem to get to the bottom of.

I'm running an Ubuntu minimal build with both mythtv backend and XBMC installed on it. I have a script which is run by myth to make sure that XBMC is idle and that no users are logged on. If this is the case then myth will shut the box down, setting a wake up timer for the next time I want the PVR to come on and record ... all good.

However, recently the HTPC hasn't been shutting down. From the log files my scripts write, I've tracked the reason down as being that my wife's laptop is showing as logged onto the HTPC. This she's managed to do without having the user credentials or having Putty installed! I'm sure that she isn't that good at hacking ... unless there is a side of here that I really don't know :confused:

```

htpc@htpc:/home/htpc# last | grep -i karla
htpc     pts/0        karlas-laptop.ho Mon Sep 28 18:56 - down   (03:22)
htpc     pts/0        karlas-laptop.ho Mon Sep 28 18:34 - down   (00:20)
htpc     pts/0        karlas-laptop.ho Thu Sep 24 22:47 - down   (00:00)
htpc     pts/0        karlas-laptop.ho Thu Sep 24 18:04 - 22:46  (04:42)

```

* Yes, the logs are pretty old. This issue seems to come and go, and I can't seem to find a way to replicate it reliably ... woohoo :)

Thinking about what was installed on the HTPC about the only thing that I thought that could cause this sort of thing would be the UPnP server in myth (though I wouldn't have thought this would show up as a registered user, particularly the htpc user as myth runs under it's own account). I've disabled it anyway. However, as this issue isn't easily replicable, I can't be sure that that will fix it.

If anyone has any pointers or help they could offer in tracking it down that would be awesome. Whilst I'm not a complete n00b at linux, this one is slightly outside of my comfort zone.

Thanks in advance,
~Dan

---

