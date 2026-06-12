---
title: "tracker-store and ubuntu 12.04"
date: 2012-09-08
forum: General Help
---

### Post by ronnystickshift on 2012-09-08
Greetings, folks.   I have not so much a direct question but a question about an observation I have made.

I'm currently running Ubuntu 12.04 on my Dell Inspiron 1525 laptop, which is about 4 years old.  I ran 8.04 and then 10.04 with enormous success.  After upgrading to 12.04 I used the Unity desktop at first.  It's beautiful, but I found that GNOME was much better for my purposes (mostly programming).  With Unity I had terrible system stability issues; it would crash several times a day, it would almost never wakeup after being in standby mode, and would almost never even come back from the black screen.  When switching to GNOME, this problems became much less frequent but still persisted, and i would have some kind of crash or another at least twice a week.  I decided to try a few other desktop environments, Xfce and KDE.  KDE crashed severely on the first login, so I didn't try it again.  Xfce ran fine, but the ssh-agent forwarding was not as good as it was in GNOME and also things didn't automount the way they had in GNOME in 12.04 and 10.04 (I just can't remember whether they did in 8.04).  So I switched back to GNOME.  

Shortly after switching back, one day, in a fit of frustration over tracker-store's very frequent and very annoying gobbling up of system resources (remember this is a comparatively old and weak laptop), I did sudo apt-get purge tracker* .  Brash, I know.  But that was more than a week ago and my system has been running perfectly ever since!  I've waited to make this post of course, because a week is not that long of a time, but this is definitely the most system stability I've had since I made the upgrade.

I've seen lots of "Unity sucks" or "Ubuntu 12.04 sucks" posts on the web but haven't seen a lot of specific problems, so I don't know if my  problem was unique; though I do know some people have had issues with  tracker-store using up system resources.  So finally, my question.  Has anyone else noticed anything like this, or tried anything like this?

---

### Post by ronnystickshift on 2012-09-13
just a quick update - lots of normal usage along with a few updates and some tweaks, and it's still working great.  i could be wrong but i gather it's the gnome desktop indexer.  whatever it is, not only does it not seem necessary but it seems to be potentially harmful on some systems, mine for example.  interesting...

---

