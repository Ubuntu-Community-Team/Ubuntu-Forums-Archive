---
title: "Dual-core, one cpu always at 100%"
date: 2010-05-02
forum: General Help
---

### Post by kpuz on 2010-05-02
Maybe a noob question but...

I have a dual-core computer that I just upgraded to lucid lynx. when looking at the system monitor, one of the cpu's is always running at 100% and its not always the same one. Is this normal or do I have an issue? I would really like some info.
edit: sorry, i restarted the computer and it looks fine now. please delete this thread

---

### Post by UbuNoob001 on 2010-05-02
Well, while your issue may be solved, i might note that I too had the same problem. Restarted and is fine. However, upon running FF/Chrome browser with any flash/java, CPUs are back up to 80+ and cpu temps on the rise/fan on.....Let us know if the same thing happens again. Im curious if this is a 10.04 specific issue.

---

### Post by mk1w86 on 2010-05-02
I would say this happens because the applications are not multi threaded.  However, if this does not happen on other Ubuntu versions it could be a Lucid issue. :-k

---

### Post by quadproc on 2010-05-02
> **UbuNoob001 said:**
> Well, while your issue may be solved, i might note that I too had the same problem. Restarted and is fine. However, upon running FF/Chrome browser with any flash/java, CPUs are back up to 80+ and cpu temps on the rise/fan on.....Let us know if the same thing happens again. Im curious if this is a 10.04 specific issue.
Yes, it is a problem in 10.04.  I ran 9.04 and 9.10 and typically found a maximum of about 12% CPU usage on one processor during idle time, and a typical usage of around 6%.

Many people have noted this problem in 10.04.  I am waiting until it gets diagnosed and fixed.

quadproc

---

### Post by vandepavert on 2010-05-06
I had the same 100% on both CPUs on a dual core processor. In my case, after I stopped sendmail all went back to normal values.

---

### Post by dino99 on 2010-05-06
no issue here with a quad cores, i'm using "pae" kernel

might check for errors: system-admin-log viewer

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by eldragon on 2010-05-06
install htop
and run it with sudo.

check if its ck-history owned by gdm. i found it IS the culprit. i dont know how to prevent it. and since its not my notebook (i cannot do this manually every time), ive set a nasty NASTY workaround.

setup a cron job for root to run every minute and just "killall ck-history"

it seems to work. but i much rather see the issue resolved ;)

i havent found anything relevant in the web.

---

### Post by pipas on 2010-05-14
I'm also having this problem.

I've a Compaq CQ61 laptop, and i noticed that one of the cores is always at 100%.

I didn't check the duration of the battery but surely it will "eat" my battery in a hurry

Anyone has a update / fix, that will fix this?


Thanks in advance
Pipas

---

