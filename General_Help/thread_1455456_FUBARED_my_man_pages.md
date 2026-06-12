---
title: "FUBARED my man pages?"
date: 2010-04-16
forum: General Help
---

### Post by phatnutz on 2010-04-16
Hello,

  I've been running karmic desktop for a while with no issues.  I wanted to try my hand at re-encoding some mkv files and I found makemkv, which seemed promising and didn't look like it'd be too tough to get running.  I followed the instructions here:

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

and ended up somehow screwing up my man pages?

when running the command:

apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev

The system froze during this, which was the first time this box has EVER locked up on me.  I tried killing xserver, but the machine seemed unresponsive so I tried to ssh to the box, but it wasn't up.  It wouldn't respond to pings, so I just assumed it was totally frozen and shut down hard.  

I rebooted and figured I'd just try the command again, but had to run dpkg --configure -a first, which hung.  I can't remember exactly what the message was, maybe I can find it in a log somewhere?  I recall it was related to mandb, I think it was rebuilding indexes or something of that nature and it just hung there.  The box wasn't locked, but the process seemed to be dead.  I let it run overnight thinking that if it were building indexes it might take a long time but in the morning it hadn't budged.  I ctrl-c'd to skip that step and let it finish, there were numerous errors on the screen.  At this point I thought that it might be a good idea to reinstall mandb and the man pages and just stat over.  So I did an apt-get remove --purge man mandb with the expectation that I could just reinstall it with apt-get install man mandb but I'm not having any luck.
It hangs every time when trying to rebuild indexes.  

Any input out there on how I can get my man page issue resolved?  
Ultimately, I'd still like to get makemkv running if anyone has any input on that as well.

Thanks!

---

