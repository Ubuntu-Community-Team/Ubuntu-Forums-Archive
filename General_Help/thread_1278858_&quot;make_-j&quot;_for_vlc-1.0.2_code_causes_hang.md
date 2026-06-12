---
title: "&quot;make -j&quot; for vlc-1.0.2 code causes hang"
date: 2009-09-30
forum: General Help
---

### Post by rshetye on 2009-09-30
invoking "make -j" as non-root user for vlc-1.0.2 code causes hang:confused:

9.10 alpha 6

partition is ext4 - (this is the first time I am using ext4, have always used ext3 or reiser - not sure if ext4 is causing any issues)

setting maxproc limit to 256 does not stop the hang

running just "make" works fine

Update: *echo 1 > /proc/sys/vm/oom_kill_allocating_task* does not seem to do anything either. Anyone know the magic incantation to avoid the system going down due to a user fork-bomb?

---

