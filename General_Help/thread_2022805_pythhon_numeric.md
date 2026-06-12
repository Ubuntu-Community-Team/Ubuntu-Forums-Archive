---
title: "pythhon numeric"
date: 2012-07-11
forum: General Help
---

### Post by sputnik2012 on 2012-07-11
Hi all.

I'm trying to install [Duplicate Music Matcher]("http://Duplicate Music Matcher").

It needs python-numeric, which is depreciated and now replaced with python-numpy, which i've installed,  I changed core.py to import numpy instead of Numeric but it crashes at line 112:
>   File "./DupeMusicMatch.py", line 58, in <module>
    find.run(output)
  File "/home/rob/DupeMusicMatch-2.3/core.py", line 112, in run
    self.matrix = Numeric.zeros([self.count_files(),36], Numeric.Int)
NameError: global name 'Numeric' is not defined



any ideas on what to do?

Thanks,
        Rob.

---

