---
title: "Laggy install."
date: 2010-01-26
forum: General Help
---

### Post by venividibitchy on 2010-01-26
I'm a new Ubuntu user, and I've found that my install is rather laggy.

Sometimes, it works just fine, but other times, it'll lag terribly for about one minute, before it resumes working again.

Music will lag mid-song, and so will videos on Youtube, which previously ran fine on XP.

It's sort of unbearable to multitask at all.

Any advice or recommendations?

---

### Post by kerry_s on 2010-01-26
specs of the machine?

---

### Post by venividibitchy on 2010-01-26
Pentium 4 3.0Ghz CPU, 512mb RAM plus a swap partition, onboard video (laptop).

Not sure if it's connected, but I'll get random application crashes, sometimes, too.

---

### Post by venividibitchy on 2010-01-29
Bump.

---

### Post by venividibitchy on 2010-01-29
No help?

---

### Post by venividibitchy on 2010-01-29
Bump x2.

---

### Post by warfacegod on 2010-01-29
Try watching System Monitor. Or "top", or "htop" from the terminal to see if anything is using allot of CPU %.

htop can be installed with:

```
sudo apt-get install htop
```

Look for things that spike up and stay up for a while.

---

### Post by venividibitchy on 2010-01-29
My CPU stays around the 20s, unless I drag a window (then it goes up to high 50s). No suspicious processes.

---

### Post by warfacegod on 2010-01-29
> **venividibitchy said:**
> My CPU stays around the 20s, unless I drag a window (then it goes up to high 50s). No suspicious processes.

That seems about right for your hardware. For the moment, I would keep watching. There must be something in the processes that's causing this.

How old is the hard drive in your laptop?

---

