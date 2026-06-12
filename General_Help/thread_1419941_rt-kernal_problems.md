---
title: "rt-kernal problems"
date: 2010-03-02
forum: General Help
---

### Post by mrblowtatoes on 2010-03-02
So, latest kubuntu. everything was working fine. Anyways...

I wanted to try some audio production on linux, so i decided to switch to a real-time kernal, so..

sudo apt-get install linux-rt

restarted, nothing happened, same kernal, went into chat, was told to hold shift to get into grub and select it, i did so,my laptop made 3 loud pc speaker beeps, then proceeded to load, it did a disk check, i canceled it...

go into x, typed my password in, and oh noes

x failed to write to /tmp;, x will now crash

[tried with ever kernal]

so i was instructed to delete xorg.conf, i did that, rebooted, get back to kde type in password, and now i get:

Mont of filesystem failed
maintence shell will now be started
CONTROL-D will terminate this shell and re-try

...

i cannot get back to x...

---

### Post by mrblowtatoes on 2010-03-02
Bump

---

### Post by Chronon on 2010-03-02
Is /tmp full?  I got this message before and clearing files from /tmp allowed me to boot into Kubuntu properly.

---

### Post by mrblowtatoes on 2010-03-04
Yes, i fixed the issue, kubuntu made 5 GB log files and filled my drive up after one reboot, i limited log files to 10mb now

---

