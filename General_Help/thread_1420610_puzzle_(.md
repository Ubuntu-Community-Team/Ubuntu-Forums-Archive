---
title: "puzzle :("
date: 2010-03-03
forum: General Help
---

### Post by ub007 on 2010-03-03
I got a log file of fixed size 5M, however it changes in time( as expected when we talk of a log file )

 WHat i think is happenning is The file gets updated with the new logs from the bottom and the top entries get flushed out to make way for the new entries at the bottom (fixed size file )

I'm trying to figure out a way to capture the entire logs to another file via a shell script maybe

pseudo code
:logfile > myfile
from then on 
:in loop
:log_new_entries >> myfile

So effectively i have my file with the complete log!!

tail -f logfile > myfile doesn't seem to work .
Any other options?

Thanks in advance

---

### Post by sisco311 on 2010-03-04
logrotate allows automatic rotation, compression, removal, and mailing of log files.

See:
```
man logrotate
```for more details.

---

