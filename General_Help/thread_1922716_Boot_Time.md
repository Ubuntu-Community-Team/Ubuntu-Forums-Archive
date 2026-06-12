---
title: "Boot Time"
date: 2012-02-09
forum: General Help
---

### Post by carlosbvp on 2012-02-09
Hello everyone,
I just installed Lubuntu on a Dell laptop D600. I replaced Windows XP with Lubuntu, so Lubuntu is the only OS in this machine. 
It takes about 1 minute to boot - start button until the machine is ready to be used.
I was wondering if there is anything that I can do to improve boot time.
Thanks in advance!
Total beginner here.

---

### Post by raja.genupula on 2012-02-09
open your terminal and type ```
cat /var/log/boot.log
```

give the output of it & BTW check your start up app list . 

i hope your system is having enough capability to run Lubuntu.

---

### Post by carlosbvp on 2012-02-09
Thank you very much Raja. This is what I get:


mps@mps-Latitude-D600:~$ cat /var/log/boot.log
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 87578/1798720 files, 542143/7194368 blocks
 * Starting network connection manager                                        [ OK ]
mps@mps-Latitude-D600:~$ 


Also I cannot find the startup list.
 Thanks Again
Carlos.

---

### Post by SteveDee on 2012-02-09
> **carlosbvp said:**
> ...I just installed Lubuntu on a Dell laptop D600....It takes about 1 minute to boot...

OK, so I also have a Latitude D600.

Using my phone as a stopwatch, I get 32 seconds from pressing the power button to a stable desktop. I pause the stopwatch when I reach the login screen, and resume as I hit enter key after entering my password.

My laptop is not in the best of health as I get a couple of disk error messages right after BIOS loads. However, my startup time compares well with similar spec'ed laptops & desktops (e.g. 1.3 - 1.7GHz cpus). Many of them start in less than 30 seconds and shutdown in about 3-5 secs.

How long does your D600 take from power button to login screen?

Attached shows my Desktop Session Settings.

---

