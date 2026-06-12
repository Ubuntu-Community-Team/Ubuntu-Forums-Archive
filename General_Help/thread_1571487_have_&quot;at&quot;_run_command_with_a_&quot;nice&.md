---
title: "have &quot;at&quot; run command with a &quot;nice&quot; of 0 instead of 2"
date: 2010-09-09
forum: General Help
---

### Post by rbpember on 2010-09-09
This is more a general Linux question than a Ubuntu question. (FYI, I'm using Gutsy Gibbon, 7.10) I want to run a command one time a later time with "at". I've noticed that, at least on my system, commands run with "at" are automatically "niced" to 2. Is there some way to have "at" run the command at a nice value of 0?

For example, if I just type "myprog" at a command line prompt, "myprog" runs at a nice of 0. However, if I use "at", e.g.,

at -f myprog 14:00

then at 14:00, myprog is executing but with a nice value of 2 in queue "a", the default queue with the lowest nice value.  
By trying, I learned that crontab will do what I want -- run the command with a nice of 0 at a later time -- but that seems awkward.

On a related note, I've also learned that running with a nice value of 2, my program runs 2-3x more slowly, even with no other system load. (Otherwise what "at" does with the nice value [HTML][/HTML]wouldn't matter to me.)

Any suggestions?

---

