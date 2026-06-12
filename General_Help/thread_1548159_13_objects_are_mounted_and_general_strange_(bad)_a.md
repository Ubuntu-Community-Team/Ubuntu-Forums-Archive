---
title: "13 objects are mounted and general strange (bad) activity"
date: 2010-08-07
forum: General Help
---

### Post by nstgc379 on 2010-08-07
Prior to yesterday, I only had those devices partitions that I would expect. No more no less. Yesterday I installed some updates (I'm not sure what) and I restarted today. In addition to noticing some significant performance issues (general slow as well as programs, such as firefox, locking up) I noticed that under the Gnome System Monitor there are 15 mounted devices. Of these only two should be there.

I rebooted I tried using different headers in case that was the update that is causing issues. I'm having this problem with kernel version 2.6.32-24 and 32-23.

[IMG]http://i8.photobucket.com/albums/a36/nstgc/Screenshot.png[/IMG]

---

### Post by chopinhauer on 2010-08-07
> **nstgc379 said:**
> Prior to yesterday, I only had those devices partitions that I would expect. No more no less. Yesterday I installed some updates (I'm not sure what) and I restarted today. In addition to noticing some significant performance issues (general slow as well as programs, such as firefox, locking up) I noticed that under the Gnome System Monitor there are 15 mounted devices. Of these only two should be there.

Indeed only two real devices are mounted, the rest are virtual file systems (on Linux you can access almost anything as a file).

---

### Post by nstgc379 on 2010-08-08
I understand that, but why are they there? If I wasn't also experiencing poor performance over all, than I wouldn't have made this thread.

---

### Post by Noz3001 on 2010-08-08
I don't think the mounted file systems are the problem. Everyone should get something like that in the system monitor if they click "Show all filesystems" in the preferences

---

### Post by chopinhauer on 2010-08-08
> **nstgc379 said:**
> I understand that, but why are they there? If I wasn't also experiencing poor performance over all, than I wouldn't have made this thread.

It is totally normal to have these 13 virtual filesystems mounted, I am not sure what you performance problem is, but it isn't the filesystems. Maybe the disk is slowing down (you can check it with the '-t' parameter of 'hdparm').

---

