---
title: "CPU scheduling: threads or processes?"
date: 2011-05-23
forum: General Help
---

### Post by PhillyPhil on 2011-05-23
This is something I probably should know, but I don't, so here goes: 

I know Linux schedules threads (kernel threads), not processes. but what I want to know is does it only schedule threads inside the timeslice for the process they are part of?

In other words, does it schedule processes, and then schedule the threads inside each process, or does it schedule threads completely independently of which process they are part of.

An example: we have processes 1 and 2, each of which has two threads, A and B.
Can the scheduler schedule this: 1A, 2A, 1B, 2B ?

Or does it schedule 1, 2, and then only schedule the threads within that, eg: 1A, 1B, 2B, 2A ?

---

### Post by PhillyPhil on 2011-05-23
Hmm, no replies.  Should I have put it in a different subforum?  Or is UF just not the place for info like this?

---

