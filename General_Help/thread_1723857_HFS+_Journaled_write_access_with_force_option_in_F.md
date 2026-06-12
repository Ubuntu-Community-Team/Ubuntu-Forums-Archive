---
title: "HFS+ Journaled write access with force option in FSTAB: Is it safe?"
date: 2011-04-07
forum: General Help
---

### Post by drowsyhaze on 2011-04-07
Hi! I wasn't sure if this thread belonged in hardware, apple users, development or wherever - please mods bare with me!

My question: is the "force" option safe for **journaled HFS+** volumes? Why discourage it/why not just support journaled HFS+ if it's working? I have only been able to find two posts on the subject: one user suggests it should be fine and he has no problem circa 2008, the other says that he read that others had problems (2006). Does anyone have any say/experience on this issue? Am I destroying my disks?

Background: I've been using ubuntu/xubuntu as a server for my primarily OS X environment for a few years thanks to the wonderful (though now out of date) [tutorial by kremalicious]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/"). When I initially started I had all of my music, movies and backups on journaled HFS+ volumes on external drives. Being poor I couldn't afford new drives, so rather than formatting to ext3 I just turned off journaling on the HFS+ volumes and mounting, r/w, and so on worked without issue.

I did a fresh install of 10.10 the other day and decided that I'd add network Time Machine backups to my current backup routine. Wanting to maintain a HFS+ environment and being very skeptical of turning off journaling (hasn't been a problem but everyone insists it will be), I formatted my new time machine volume as JOURNALED HFS+ and I reenabled journaling on all of my external/shared volumes from my mac and added the following to my clean FSTAB:
```
/dev/sdd3 /media/peggy\040sue hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 0
/dev/sdc2 /media/joan hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 0
```
and so on for each journaled HFS+ volume (spaces here are tabs in FSTAB)

This has allowed me r/w access on my HFS+ **JOURNALED** volumes, so far without any hiccup (though it's only been three days). In fact, I can backup to my networked journaled HFS+ time machine volume without any problem or need to hack Time Machine settings in OS X or add the "tm" option to netatalk's applevolumes.default.

I will probably be turning off journaling on the non-time machine volumes later today and use the time machine volume as an experiment (I do weekly SuperDuper backups), but it'd be nice if I could just leave it on.

P.S. Installed hfsutils, hfsprogs, and hfsplus

---

### Post by ubu84 on 2011-04-09
Just want to let you know I found this post useful.  I'd forgotten all about the force option in mount.  It's the little things I suppose.

---

### Post by drowsyhaze on 2011-04-29
Glad to hear it! I've seen a lot of threads where people were struggling to read journaled HFS+, hope this helps others as well.

So, update: I've been doing Time Machine backups to an HFS+ Journaled disk on my xubuntu 10.10 machine for about a month now with no problems at all! Passes fsck run by cron every week, will update again later...

---

### Post by Nopstnz8 on 2011-05-09
Wondering if someone could answer my question from this thread

[http://ubuntuforums.org/showthread.php?p=10790096#post10790096](http://ubuntuforums.org/showthread.php?p=10790096#post10790096)

---

### Post by drowsyhaze on 2011-05-13
Responded, good luck!

---

### Post by drowsyhaze on 2011-05-13
Update: about two days ago I got a TimeMachine error regarding the integrity of my backup, TimeMachine arguing that I have to make a new one. I performed an fsck, cleaned appled files, browsed the sparsebundle and "entered TimeMachine" but all seemed fine. So, I guess there's a bug someplace, but where and what is it?!

---

### Post by drowsyhaze on 2011-09-19
Just an update: it's been a few months now and I haven't had any errors on any of my machines since the last one. Will update again if I ever do, but for now I think it's safe to assume that it's pretty safe to force mount your HFS+ volumes.

---

