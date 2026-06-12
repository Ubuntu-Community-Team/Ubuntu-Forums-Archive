---
title: "Sound is choppy on only one user account."
date: 2010-04-08
forum: General Help
---

### Post by blur xc on 2010-04-08
My original [thread]("http://ubuntuforums.org/showthread.php?t=1449517") was about a sound capture problem using kino- but after some more investigation I realized that sound was choppy on only my user account.  If I switched over to my wifes account, the sound was fine, then logged back in on my account, and the problem persisted.   I logged out, and logged back in, but still have the problem.

So, what could cause the sound to now work properly on only one user account?

Thanks,
BM

---

### Post by 666f6f on 2010-04-08
Since everything works on another account, I would check/compare the running processes. Maybe something occupies your sound card, when on your account.

You can get a list of running process by running
```

ps -aux > ~/Desktop/running-processes.txt

```

---

### Post by blur xc on 2010-04-08
thanks- I'll give that a try.  I haven't tried rebooting.  I'm trying to take advantage of Linux's "doesn't need to be reboot for everything like Windows" touted feature...  If there's a way to fix it w/o having to reboot it, I'd like to find that first, even if it means going longer with the problem.

BM

---

### Post by 666f6f on 2010-04-08
> **blur xc said:**
> I'm trying to take advantage of Linux's "doesn't need to be reboot for everything like Windows"

I'm not following you, what is a *reboot*? :guitar:

---

### Post by lidex on 2010-04-08
Check out "Part A" of this page:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by blur xc on 2010-04-08
> **lidex said:**
> Check out "Part A" of this page:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Sweet- thanks for that!

BM

---

### Post by lidex on 2010-04-08
> **666f6f said:**
> I'm not following you, what is a *reboot*? :guitar:

Synonymous with restart.

---

### Post by lidex on 2010-04-08
> **blur xc said:**
> Sweet- thanks for that!

BM

You're welcome. Did it fix your problem?

---

### Post by blur xc on 2010-04-09
> **lidex said:**
> You're welcome. Did it fix your problem?

I ran a few of those commands, and could not find any hung processes w/ ps aux so I finally gave in and rebooted it.  so much for my 9 day uptime...  :(

thanks anyway

BM

---

### Post by lidex on 2010-04-09
> **blur xc said:**
> I ran a few of those commands, and could not find any hung processes w/ ps aux so I finally gave in and rebooted it.  so much for my 9 day uptime...  :(

thanks anyway

BM
Ah...priorities :rolleyes:

---

