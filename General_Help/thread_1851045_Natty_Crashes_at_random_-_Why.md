---
title: "Natty Crashes at random - Why?"
date: 2011-09-27
forum: General Help
---

### Post by mebunto on 2011-09-27
Hi, I've been running Kubuntu Natty for quite some time.  I have also suffered with a fairly random crash where the computer just dies completely and restarts.  There is no "crash report" dialogue, as you get with some software bugs in Kubuntu, the computer just died completely.
I have googled  and searched the forums but I can't get to the bottom of it.  I have looked through log files and also I've run memtest overnight, which does not indicate any errors.
It would be helpful if someone could tell me how I might be able to narrow this down - is there a diagnostic utility that I can run in the background?  Anything please.

Thanks
Mebunto

---

### Post by mebunto on 2011-10-02
Well I've tried overloading all four cpus; temperature went much higher than I've ever seen it normally - something like 80C and it didn't crash.  So I don't think it's a temperature event.
I can't see anything in the event logs.  But every so often I can be away from my desk and the machine's back at the login prompt (I don't use a screen saver) so it must have crashed and rebooted.
Can anyone help to get me looking in the right direction?

---

### Post by LinTux on 2011-10-02
I have a ubuntu machine running 11.04, which shut down randomly. I went through the kernel log and found that it had sent out a message to shut down because my CPU had reached critical temperature. It seems to shut down at 99, and will stay active at 70 or 80.

However the point of this post is to tell you to look through /var/log/kern.log and search for keywords (with your text editor's built in search tool). This is how i figured out that my computer was shutting down because it was overheating.

hope it helps.

---

### Post by mebunto on 2011-10-04
Thanks for the tip - what are the best key words to look for?  Just in case I search for the wrong ones.

---

### Post by knutschr on 2011-10-04
Are you running 64 bits?
If so, it can be npwiever.bin.
Close it

---

### Post by Topsiho on 2011-10-04
Another option is it's hardware. Check your memory (memory test, several passes), and your hard disk (disk utility)

Topsiho

---

### Post by deserthowler on 2011-10-04
> **Topsiho said:**
> Another option is it's hardware. Check your memory (memory test, several passes), and your hard disk (disk utility)

Topsiho

I found memory to be the culprit in several instances.  I'm using boxes that I've salvaged and scavanged parts for so there are other problems involved here (P4 is my leading edge box).  If you have extra memory or memory from in a box that doesn't have this problem, you can change out the memory see if this helps.

Earl

---

### Post by mebunto on 2011-10-04
Do you mean npwiever.bin or npviewer.bin ?  I have 64-bit

I ran memtest overnight without any problem.  Yes could be a hardware fault but I have no inkling what might be the cause.  The MB is SandyBridge (not the original faulty one) and it's about 6 months old.

---

