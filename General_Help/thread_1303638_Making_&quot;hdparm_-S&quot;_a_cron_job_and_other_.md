---
title: "Making &quot;hdparm -S&quot; a cron job? and other energy-efficiency issues"
date: 2009-10-28
forum: General Help
---

### Post by dbsoundman on 2009-10-28
I'm looking for ways to save some energy on my little home server, and read something about using hdparm -S to spindown the disks after a certain amount of time. I also read that you could make it a cron job somehow. Looking into cron, however, I found that everything was set up to be run on a fixed-time basis; i.e. once an hour, once a day, etc. What I would like is for hdparm to spin down the drives when the machine has been idle for, say, 10 minutes. How exactly would I go about this?

Also, I'm a little bit skeptical about how spinning down the harddisks would save that much energy anyway. In the case of this computer, it just has one IDE drive in it. Should I even bother with this in the first place? I guess I don't have a good idea of how much energy the computer takes in in the first place but if I'm going to have it running all the time I'd like to minimize the power consumption when it's idle (not to mention the heat output as well). Any ideas?

Thanks,
Dan

---

### Post by Giblet5 on 2009-10-28
```
sudo hdparm -S120 /dev/sda
```

Will set the first disk to spin down after 10 minutes of idle time.

No need to put it in cron, just add it to the /etc/rc2.d/S99rc.local script. It's good until you reboot.

---

### Post by dbsoundman on 2009-10-28
Thanks, that's a good start, but how do I make it permanent? I may or may not be powering down this machine from time to time, and I'm sure I'll forget how to set this up after a certain amount of time, so it'd be great if it was a permanent operation.

-Dan

---

### Post by bribera on 2009-10-28
I think you can just add that line to /etc/rc.local and make sure that script is marked executable.

You might be able to reduce your disk spinning even more by mounting /tmp as a tmpfs. This is only worthwhile if you have enough RAM to store all of /tmp without swapping.

Take a look at:
[http://en.wikipedia.org/wiki/TMPFS#Linux](http://en.wikipedia.org/wiki/TMPFS#Linux)
[http://forums.debian.net/viewtopic.php?t=16450](http://forums.debian.net/viewtopic.php?t=16450)

---

### Post by dbsoundman on 2009-10-30
So, for example, I would just need to add:
```
#!/bin/sh -e
sudo hdparm -S120 /dev/sda
```
to the /etc/rc.local file? Or is there more to it? I'm still not exactly an expert at writing these little Unix scripts.

-Dan

---

