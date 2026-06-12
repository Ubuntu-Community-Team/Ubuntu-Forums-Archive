---
title: "Does not find installed program"
date: 2010-03-05
forum: General Help
---

### Post by ratcheer on 2010-03-05
I am stumped on this one. Everything appears to be correct, but it does not work. I just compiled and installed the latest stable ruby language. The make installed it into /usr/local/bin. My PATH has /usr/local/bin before /usr/bin. A "which" command shows the program found in /usr/local/bin. But, when I try to run the program, the shell says it cannot be found in /usr/bin. This makes no sense, to me.

```

tim@tim-desktop:~$ which irb
/usr/local/bin/irb
tim@tim-desktop:~$ echo $PATH
/usr/java/jre1.6.0_18/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
tim@tim-desktop:~$ irb
bash: /usr/bin/irb: No such file or directory
tim@tim-desktop:~$ /usr/local/bin/irb
irb(main):001:0> 

```I know many ways to fix it, but I do not understand why it is not just working. Someone please educate me.

Thanks, Tim

---

### Post by Intrepid Ibex on 2010-03-05
Didn't you try out ```
export PATH=(/usr/local/bin/irb:$PATH)
``` ?
You need to relogin (or just login to another tty) for the PATH variables to reset if you have configured them wrong _temporarely_ (with export PATH=(/path/to/a/folder:$PATH)).

---

### Post by ratcheer on 2010-03-05
irb is an executable, not a directory. So, the PATH is correct.

Tim

---

### Post by ratcheer on 2010-03-05
However, you are correct - starting a new terminal session corrected the problem. Thank you.

I have been working with UNIX systems for almost 30 years, and I don't ever recall having to log back in to effect a new environment setting. :o

Tim

---

