---
title: "how to make goldendict load up?"
date: 2011-08-03
forum: General Help
---

### Post by aninona on 2011-08-03
Hi
I've tried to purge[linux] goldendict and reinstall it, and when I type 'goldendict' inside the terminal it outputs 'Another GoldenDict copy started already.'

And running 'sudo killall goldendict' outputs 'goldendict: no process found'

What should I do?

Thanks!!!

---

### Post by Hatsune Miku on 2011-08-03
> **aninona said:**
> Hi
I've tried to purge[linux] goldendict and reinstall it, and when I type 'goldendict' inside the terminal it outputs 'Another GoldenDict copy started already.'

And running 'sudo killall goldendict' outputs 'goldendict: no process found'

What should I do?

Thanks!!!

It might be running under another process name; if you do a reboot it will stop ALL processes, thus stopping the goldendict.

~Miku

---

### Post by ajgreeny on 2011-08-03
If it appears to be still running even after a reboot, run the command in terminal ```
ps aux | grep golden
```and if we assume that the word golden is somewhere in the executable's name it will show up.  You can then stop it running either with ```
killall name
```or using the pid number, second item in the output```
 kill pid
```If that does not work try ```
kill -9 pid
```You may need sudo if it is a root process.

---

### Post by aninona on 2011-08-04
deleted ~/.goldendict/pid file:o:):D:P

---

