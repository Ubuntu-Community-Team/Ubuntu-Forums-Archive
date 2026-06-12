---
title: "HELP: Hard Drive Device Not Recognized"
date: 2010-02-04
forum: General Help
---

### Post by ngrieb on 2010-02-04
So I logged on today to find my computer with a blank black screen when I walked back into the room. 

It appears that Ubuntu suddenly cannot find my HD anymore. I get through the grub screen and even past the little white Ubuntu 9.10 logo, but then no login box appears and when I press a key I get the terminal, where is says something to the effect of:

Error can not locate drive by-dev-id HD_BLAH , 

my Ubuntu partitioned drive of course. Is there any way to check that that drive is even still functioning. I pretty much have permanently switched over to Ubuntu, so it would suck to lose that drive.

I really need some advice on what to do...should I just attempt to boot the live CD? (by attempt I mean my computer is so damn old that the CD and DVD drives are pretty much dead, and I'd be lucky to read a CD correctly because of this).

Thanks.

---

### Post by ngrieb on 2010-02-04
Ok, just an update...for clarity. My BIOS sees my HD, but neither Windows 7 or Linux can see my drive. I'll try and update this with the exact error that I am receiving on the Linux boot screen later tonight.

...So this is the exact error:
Gave up waiting for root dev. Common problems: 7cc43d2...
   - Boot args (cat /proc/cmdline)
   - Check root delay
   - Check root
-Missing modules (cat /proc/modules; ls dev)

ALERT: /dev/disk/by-uuid/2.... DOES NOT EXIST. Dropping to shell.

Is there any hope for my HD?

---

### Post by jARLAXL on 2010-02-05
Try this:
[http://ubuntuforums.org/showthread.php?t=370386](http://ubuntuforums.org/showthread.php?t=370386)

---

### Post by ngrieb on 2010-02-05
[F6] does nothing at any point in the startup. I get thrown into "BusyBox"...? 

Is there any way to get to the kernel command line from here?

---

### Post by joaqal on 2010-02-06
Hello: Did you find a solution to this problem? I am having the same issue. It just won´t boot since this morning.

---

### Post by ngrieb on 2010-02-06
No, no solution yet. I have been using Ubuntu 9.10 for nearly a year, and this just suddenly happened. I can't see any way to get to the kernel from here either. It's just like my main HD disappeared. 

You might want to try using the live CD to re-detect your HD's, but I'm without any well working DVD or CD drives at the moment, so I don't have that option right now. Let me know if that works, so I can perhaps borrow an external DVD/CD drive.  

Did you install anything on your computer before this happened? The last thing I remember installing was a Pidgin plug in.

[SOLVED]

Ok...found the solution. It appears as though this has been happening a lot recently. Some update for something it seems is doing this. The solution is here:

[http://ubuntuforums.org/showthread.php?t=1400783](http://ubuntuforums.org/showthread.php?t=1400783)

---

