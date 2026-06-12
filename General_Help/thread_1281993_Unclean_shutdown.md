---
title: "Unclean shutdown"
date: 2009-10-03
forum: General Help
---

### Post by deadcorpz on 2009-10-03
I was getting ready to reformat my laptop but wanted to save some things so I was transferring them to an external hard drive. While transferring the files to the external my system froze up and the screen went black and it would not respond. I ended up having to just manually turn it off by pressing the power button and when I turned it back on it started to boot up as normal. When the ubuntu logo appeared and the bar started to load text appeared below the load bar that said "Unclean shut down, checking drives   1%" and it gets to 14% on the drive check before it locks up and sends me to a black screen. The black screen says

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 14% (stage 1/5, 484/2296)

*An automatic system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.


What do I do now?

---

### Post by fela on 2009-10-03
If it brings you to a shell prompt (root@box:# or similar), run:

```
fsck /dev/sda1
```

Your problem is overwhelmingly indicative of a failing hard drive. Sorry.

---

### Post by deadcorpz on 2009-10-03
Woot it worked. I ran the manual check and it had a bad node so I deleted the node and got back in and come to realize that 99% of what I had been transferring to my external had already made it so I just needed to reformat anyway. Thanks a ton! :D

---

### Post by fela on 2009-10-04
> **deadcorpz said:**
> Woot it worked. I ran the manual check and it had a bad node so I deleted the node and got back in and come to realize that 99% of what I had been transferring to my external had already made it so I just needed to reformat anyway. Thanks a ton! :D

Great! Good to hear it's not a failing hard drive...although you should backup all your data anyway. I had a hard drive that failed, I was too naive to backup beforehand and I lost tonnes of data :(

---

