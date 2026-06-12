---
title: "64 bit Opera won't fully close"
date: 2009-11-11
forum: General Help
---

### Post by schmidtbag on 2009-11-11
I run 64 bit Kubuntu 9.10 and for the most part everything is working ok, but some programs (so far its only been frostwire and opera) won't fully close.  Opera is my main concern, since that becomes fairly resource demanding on 64 bit systems and i use it all the time.

When I click the close button on Opera, it does close without really complaining.  But then when I check ksysguard, its still running.  then, I click on it and try to kill it and it won't "die".  it just stays there.  when i open up konsole and type in "killall opera" it still doesn't close.  strangely though, "pkill opera" does work, and when i right-click on the opera process, click on "send signal", and THEN select kill, it works.

So basically what i'm asking is, why won't the process stop and why are my killing options limited?

I am running the 64 bit version of opera AND flash if that makes a difference

---

### Post by schmidtbag on 2009-11-12
no one else is experiencing this?

---

### Post by Sav1 on 2009-11-13
I'm having the same issue on Xubuntu 9.10 64bit with Opera 10.01

---

### Post by Soul-Sing on 2009-11-13
what is the outcome of:
```
opera %u
``` in the terminal?

---

### Post by schmidtbag on 2009-11-13
as i have suspected, running opera in the terminal wouldn't display anything.  i don't think opera itself is dysfunctional but theres something wrong with it when it ends.  i'm not sure if opera 9.xx did this because i never used it in 64 bit, but regardless if it doesn't close all the way, why are there only 2 specific ways of killing it, where the other 2 don't work?

btw, it also has these random moments where it goes on a "crashing spree".  so it'll run fine for hours and then every time i start it up again, it crashes within a few seconds.  about 2 minutes later, it stops doing it.  i'm not running any background processes that would be causing this, but i think the opera devs are to blame on this one.

---

### Post by Soul-Sing on 2009-11-13
strange, i do run opera 10.1 on a 64bit system without any problems. and did use "old" opera profiles....

---

### Post by schmidtbag on 2009-11-13
well in that case, heres what i think may be the culprit - are you running 64 bit flash or forcing 32 bit to work?

---

### Post by schmidtbag on 2009-11-14
still nobody has an answer?  this is really getting annoying

---

### Post by Sinsemila on 2009-12-11
I have this problem with 9.10 Ubuntu 32 and 64 as well as Kubuntu. I even tried Mint 8, 32 and 64 bit and still get this problem. I tried it on 3 different computers and all have the same problem. 
The Opera Sync feature is really important to me so for now Ive switched to OpenSuse 11.2 . No problems with either the 32 or 64 bit edition. I also tried a few other non Ubuntu based distributions and none have the problems Opera for Ubuntu 9.10 has.

---

### Post by schmidtbag on 2009-12-11
hmm interesting.  i'm running my opera 32 bit on 9.04, but my opera 64 bit is on 9.10.  what i find strange is how, according to you, both gnome and kde 9.10 have this problem.  i thought it was just a 64 bit kubuntu problem, since this is the first time i've used kde or 64 bit.  unfortunately detecting such problems is out of our knowledge, so lets hope the opera development team figures out whats wrong for the next update

---

### Post by Cieniek on 2009-12-12
Same issue with Opera 10.10 @ Ubuntu 9.10 64bit. (64bit flash and sync. option enabled.)
It would be nice if someone submit a bug ;-)

---

### Post by schmidtbag on 2009-12-12
> **Cieniek said:**
> Same issue with Opera 10.10 @ Ubuntu 9.10 64bit. (64bit flash and sync. option enabled.)
It would be nice if someone submit a bug ;-)

although sync is a good feature to blame since its new, sync is most likely not the problem.  i'm not using it and i still get the crashes.  according to that other guy, apparently this happens in 32 bit as well so surprisingly flash may not be the problem either.  i'm using kde but a lot of people here seem to be using gnome, so its not a DE problem

---

