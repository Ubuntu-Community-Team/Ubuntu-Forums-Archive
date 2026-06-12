---
title: "Is Ubuntu usable with disabled swap?"
date: 2011-12-30
forum: General Help
---

### Post by alexei_ on 2011-12-30
I am still having issues described in different threads, some of them are:
[Is Ubuntu usable on laptop after "Suspend"?]("http://ubuntuforums.org/showthread.php?t=1896669")
[Ubuntu 11.10 - Performance issues after upgrade]("http://ubuntuforums.org/showthread.php?t=1887669")
[Why one application could take Ubuntu down?]("http://ubuntuforums.org/showthread.php?t=1876364")

I am still not sure how to fix the issue. Now, in order to have Ubuntu running without freezing I have to reboot every 2-3 days.

During freezing it is usually permanently reading HD. ... I would assume reading/writing swap. So I decided to disable swap. First day it worked fine. Second day, after "suspend" I started a command line compilation process... By the end of compilation I got my laptop frozen (not responding to any keyboard, mouse action) and permanently reading HD. I waited for 3 minutes... I did not have time to wait more... May be my laptop would recover after 20-60 minutes... but this is not acceptable for me. Before running the process I had about 300Mb of memory available as per htop (I did not run "free")... 

Well I can not understand one thing -- why Ubuntu got to frozen state? 

Could Ubuntu be smart enough to not let keyboard and mouse become frozen???

---

### Post by 2F4U on 2011-12-31
Suspend to RAM may work without swap, but obviously you won't be able to suspend to disk without a swap partition. The other case where swap is needed if you run out of physical memory. Linux will then move inactive programs and memory structures out to the swap partition to make room for active programs requesting more RAM. If your system can't provide enough RAM that may indeed lead to a state where the system seems to be frozen.

---

### Post by Paqman on 2011-12-31
> **alexei_ said:**
> ==During freezing it is usually permanently reading HD. ... I would assume reading/writing swap.

POssibly but not necessarily. The system writes to places other than swap in normal use. Have you checked your logs to see if anything shows up? Lockups can be due to all sorts of things, graphics always used to be bad for this a few years ago.

---

