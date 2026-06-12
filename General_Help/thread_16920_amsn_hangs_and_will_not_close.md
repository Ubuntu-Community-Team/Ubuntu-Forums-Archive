---
title: "amsn hangs and will not close"
date: 2005-02-24
forum: General Help
---

### Post by mrs_squid on 2005-02-24
I have installed amsn version 0.92 and I can open it, log in, but not log out or close it. It appears to hang. I haven't much knowledge of Linux and do not know how to force-quit this application despite spending the past 3 hours googling and hunting this forum for clues. Any help, the simpler the better, appreciated.

I have also used the 'top' command to try and find the pid but had no luck.


Finally found a cure so if anyone else has this problem open terminal and type
ps auxw | grep amsn   [hit enter]
the second column from the left will tell you the process ID
then add
kill -9 [number of process id (PID)]

---

### Post by negatory on 2005-03-24
I've had success with amsn in Debian.After googled it up a little I've found that starting amsn like this "export LD_ASSUME_KERNEL=2.2.5 && amsn" would stop the random freezes and crashes but I've had no such luck with ubuntu for amd64, after I'd export LD_ASSUME_KERNEL=2.2.5 I allways get "*: error while loading sharing libraries:lib*.so.1:cannot open shared object file:No such file or directory" if I start any program.
Maybe something to do with the gcc version it was compiled....
Any help on this?

Pedro Carrico

---

### Post by NVRO on 2005-04-25
I have the same problem. :?

---

