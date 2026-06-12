---
title: "pm-suspend: command not found"
date: 2011-07-26
forum: General Help
---

### Post by alj on 2011-07-26
I have a cron (running as root) that does some work and then suspends the pc until the next morning. This script works fine when run fom the terminal, but when running the script via the cron, it fails. 

This is my test script:

#!/bin/bash
pm-suspend

The cron is:
10 9 * * * bash /home/administrator/sleep.sh > /home/administrator/error.log 2>&1


The error is:
line 2: pm-suspend: command not found

---

### Post by Toz on 2011-07-26
The environment variables when running cron jobs is different than the environment variables when you log in. Specifically, the path identifiers. Most likely, /usr/sbin is not in the default cron path which is why the pm-suspend command is not being found. Try changing your second line to read:
```
/usr/sbin/pm-suspend
```

As a general rule, when creating cron scripts, always fully specify the path to the executables. The **which** command can be a handy tool.```
which pm-suspend
```

---

### Post by alj on 2011-07-27
That works. And thanks also for the tip about **which**. I've been learning a lot over the last week.
Cheers.

---

