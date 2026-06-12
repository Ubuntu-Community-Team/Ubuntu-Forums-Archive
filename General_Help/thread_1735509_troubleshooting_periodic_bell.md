---
title: "troubleshooting periodic bell"
date: 2011-04-21
forum: General Help
---

### Post by rifter on 2011-04-21
For some reason I have a bell sound going off periodically on my installation.  It sounds like a little ding, kind of like the bells they have on the front desks of some hotels or the sound of two crystal glasses clinking together.

     I do have some alarm clock software installed (from the repositories) from when I was trying to find one that actually worked.  (They all have reasons to be sub-optimal unfortunately, at least the ones I have found).  But I don't as far as I can tell have any of that running.  Once in awhile I will fire up alarmclock, which can't run long without messing itself up, and set a one-time alarm for something, but I have never used a sound like the ding for an alarm.

     In fact as far as I know I have not set that sound for anything.  I don't even know where such a sound file lives, really because I don't remember hearing one like that before.  I know I can check the crontab but I don't have much hope for something there sticking out.  Then again it has to be something that is already running if it isn't in the crontab.  I don't see any alarm clock apps running when this happens, so short of writing a monitoring script or something that records all the processes when they happen and hoping to catch it, I am not sure where to begin troubleshooting this.

     If anyone has an idea what it might be or at least where else to look I would be glad to hear it.  By the way I am not running gnome anymore so the little thing that starts apps when you log in to gnome should not be a factor.  (I am using fvwm which basically is not currently starting anything like that.  I do start xclock -digital manually when I log in because I have not bothered to fix it starting up, but I don't think it is making that noise.  Could totally be wrong though.

---

### Post by rifter on 2011-04-21
Okay looking at the xclock man page it might be that it is chiming.  But it seems like it should only do that when you do -chime and I am not.  Somehow I have two of them, too, so there is another thing for me to deal with.  I have no problem with that part, just if xclock is not what is chiming what else to look at.  Or if someone knows about a bug in xclock that would cause this.  There seems not to be any option to tell it not to chime, but that should not be necessary since it is I am sure the default not to chime.

---

### Post by rifter on 2011-04-21
I am suspecting xclock now.  The man page says if chimes are on it will ding twice every hour and once every half hour.  I noticed this time that the ding happened a minnute and a half after the half hour which is still wrong, and it should not be dinging at all, but that seems to be what is going on.

---

### Post by rifter on 2011-07-26
Turns out the second xclock was from fvwm's default settings.  I don't think the chime was from there.  It seems to be tied to the google calendar settings.  So I guess google calendar was chiming when it was time for an event I had scheduled, probably the ones I had a popup for.

---

