---
title: "&quot;background&quot; app mystery"
date: 2010-07-05
forum: General Help
---

### Post by pdadad on 2010-07-05
There is a process running on my system, Lucid Lynx, named "background" that appears randomly and consumes a large percentage of my cpu.  I've been able to observed this in conky.  Seeing the PID in conky, I tried to kill the app.  I got a message that there was no such PID.  The last time this happened there were 2 apps named "background" that I could not kill, both consuming 30 to 40% of my processor.

I've searched for an answer, but the problem is that many processes/apps run in the background, but are not named "background".

I've run chkrootkit, rkhunter, and unhide to see if there may be a rootkit.  Nothing showed up but a few suspicious files that appear to be false positives, from what I read here in the forums.

Otherwise the system is running great. Any thoughts about what else I can do to discover what is going on with my system would be much appreciated.

---

### Post by Smart Viking on 2010-07-05
Hi, i does not have a process called background on my system at least.

The problem you talk about that it says that there is no such process might be that the process switches PID all the time, but im not sure, you could try to do this command:

```
pkill background
```

And that should kill the processes containing the word "background".

I hope this helps :)

---

### Post by pdadad on 2010-07-05
Thanks Smart Viking!  I'll give it a try.  I was trying killall and then the PID number.

---

### Post by pdadad on 2010-08-09
My intention was to come back and report results on this but so far I have not seen the process turn up again.

---

