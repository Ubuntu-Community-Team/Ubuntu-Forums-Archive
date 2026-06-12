---
title: "Black screen, with &quot;starting NTP server ntpd&quot; message"
date: 2010-03-02
forum: General Help
---

### Post by kanolsen on 2010-03-02
My ubuntu 9.10 desktop worked perfectly this morning after I installed K9copy, ubuntu restricted extras, Compiz Fusion Advanced Settings Manager, and WINE. I also got an update on Sudo, which I installed as well.

Later in the evening I restarted and suddenly the computer went totally black after the Ubuntu logo. 
Every few seconds the following blinks on the top "Starting NTP server ntpd"

I can't get an terminal up, I have tried to boot in recovery mode, but didn't help much. 

However, one of the harddrives show up on my homenetwork, and I can access the data. So it's alive somehow. 

How can I get it back to as it were?

Thanks for any help
Kanolsen

---

### Post by kanolsen on 2010-03-11
Is it safe to uninstall NTP so I might skip this problem altogether?

Kanolsen

---

### Post by scrapnon on 2010-11-29
I have the same problem in 1n 10.10 (Lubuntu, actually), I am able to switch to the other TTY consoles, although every few seconds I am brought back to the original (TTY7?). I was able to quickly uninstall the 'ntp' package, but the same thing happens, although the boot screen now reads a different message about the b43 wireless drivers. I don't believe ntp or the wireless drivers are the issue, but I have no clue what to do now, and I cannot boot to any desktop now.

---

### Post by v5ar on 2010-12-14
[http://www.linuxquestions.org/questions/linux-newbie-8/system-boot-hangs-at-starting-ntp-server-ntpd-why-679714/#post3324951](http://www.linuxquestions.org/questions/linux-newbie-8/system-boot-hangs-at-starting-ntp-server-ntpd-why-679714/#post3324951)

from this post it seems the problem itself lies in tty not being configured proprely,
i'm also looking for a solution, since i have the same problem when using -nv driver

---

