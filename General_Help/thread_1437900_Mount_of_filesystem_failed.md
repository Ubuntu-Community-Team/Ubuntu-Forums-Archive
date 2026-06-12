---
title: "Mount of filesystem failed"
date: 2010-03-24
forum: General Help
---

### Post by erixoltan on 2010-03-24
I have a 64 bit Karmic system with two drives.  One is mounted as / and the other is mounted as /home.  I just put the video card from my system into my son's system and got a new video card.  (Don't see how it's related but still...)

Now I am getting the following message when I turn on the system.  

```
Mount of filesystem failed.
A maintenance shell will now te started.
CONTROL-D will terminate this shell and re-try.
root@zoltan:~#
```

Tried putting the old video card back in, but it still happens.  

I can launch from a Live CD and it sees both drives.  I could reinstall the whole system but I want to see if there's a way to recover my existing system first.  Anyone have any thoughts?

---

### Post by erixoltan on 2010-03-24
On another thread...

[http://ubuntuforums.org/showthread.php?t=1305434](http://ubuntuforums.org/showthread.php?t=1305434)

...it said to run fsck and that solved my problem.

---

