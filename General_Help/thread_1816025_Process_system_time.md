---
title: "Process system time"
date: 2011-08-01
forum: General Help
---

### Post by jorge_ on 2011-08-01
Hello everyone,

I´m using the /usr/bin/time command to measure a process´s elapsed time. It divides the time in user time, system time and wall clock time. I was suposing (after reading the man of the command), that the user time is the time that the process stays in processor executing, without the time of interruptions and process scheduling, but I believe that I´m wrong.

I´m using this command in a quad-core processor. When I run only one process that uses 100% of one core, the user time it´s about 7 hours and 18 minutes. If I run that same process with other process using all cores, this time it´s about 12 hours.

The elapsed time for the process (user time) shouldn´t be the same?

The command that I´m using is 
```
/usr/bin/time -o tempo.txt --verbose nohup R -f a1.r &
```

Since now, thank you for the help.

---

### Post by karlson on 2011-08-01
> **jorge_ said:**
> Hello everyone,

I´m using the /usr/bin/time command to measure a process´s elapsed time. It divides the time in user time, system time and wall clock time. I was suposing (after reading the man of the command), that the user time is the time that the process stays in processor executing, without the time of interruptions and process scheduling, but I believe that I´m wrong.

I´m using this command in a quad-core processor. When I run only one process that uses 100% of one core, the user time it´s about 7 hours and 18 minutes. If I run that same process with other process using all cores, this time it´s about 12 hours.

The elapsed time for the process (user time) shouldn´t be the same?

The command that I´m using is 
```
/usr/bin/time -o tempo.txt --verbose nohup R -f a1.r &
```

Since now, thank you for the help.

That is entirely possible.  When you are using all cores on the system for the user processes OS will preempt them for its own needs etc.

In addition since you are using R for a long running processes you should consider the blas library you are using, some implementations have issues with multithreading.

---

### Post by jorge_ on 2011-08-01
So, if I understand it correctly, there's no way to get only the process´s time without the time preempted for the OS and process scheduling. It´s that correct?

Thanks again.

---

