---
title: "Running a process allowing it only a defined max cpu usage?"
date: 2009-12-15
forum: General Help
---

### Post by rowz on 2009-12-15
Is there a way to run a process while explicitly defining it's max cpu usage?
For instance allow it to use max 20% of the cpu.
How would one go about to accomplish this?

I have this game which uses a whole lot of cpu.
Often times to the degree of making the rest of the system unstable.
As I understand priority/nice only define what process should have priority and if there only is one process it's allowed full cpu usage.

Help very much appreciated.
I'd really like to get rid of windows for good ;D
The game is Savage 2 btw.

---

### Post by rowz on 2009-12-15
Cpulimit.
Perfect for the job.
Found it.

**apt-get install cpulimit**

---

