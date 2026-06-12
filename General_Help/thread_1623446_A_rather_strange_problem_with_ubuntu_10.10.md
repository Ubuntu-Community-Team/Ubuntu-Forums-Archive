---
title: "A rather strange problem with ubuntu 10.10"
date: 2010-11-16
forum: General Help
---

### Post by brabox on 2010-11-16
Hi,

I've got a Dell Studio 15 laptop with 4gb RAM, an i5 processor and some 1gb video card.
Ubuntu is the only OS on my hard disk and everything worked fine for about a week (I installed ubuntu 10.10 on a formatted hard disk).
Then all of a sudden Ubuntu started booting into a terminal and asked for my login info. I didn't know what to do, so I googled a little. Logging in using that terminal thing and executing startx got me to my desktop.
But when I do this the computer's battery drain in like half an hour because some process called ksoftirqd/2 uses 100% of the cpu (this can only be seen in terminal>top. However not any of my CPUs show an abnormally high %. Just 27%si seems strange).
Most extraordinary thing however is that once or twice when I booted up and pressed ESC at the correct time (I think just before I get the line with the login prompt) , it skipped the whole terminal thing and got me to my desktop without the CPU problem. I tried reproducing that result but it's apparently very tricky.


Hope anyone can help.
Regards,
Bram


PS: I can get my ubuntu to do anything. It's just noisy and I have to continuously plug it in.

---

### Post by yuki-nagato on 2010-11-16
> **brabox said:**
> Hi,

I've got a Dell Studio 15 laptop with 4gb RAM, an i5 processor and some 1gb video card.
Ubuntu is the only OS on my hard disk and everything worked fine for about a week (I installed ubuntu 10.10 on a formatted hard disk).
Then all of a sudden Ubuntu started booting into a terminal and asked for my login info. I didn't know what to do, so I googled a little. Logging in using that terminal thing and executing startx got me to my desktop.
But when I do this the computer's battery drain in like half an hour because some process called ksoftirqd/2 uses 100% of the cpu (this can only be seen in terminal>top. However not any of my CPUs show an abnormally high %. Just 27%si seems strange).
Most extraordinary thing however is that once or twice when I booted up and pressed ESC at the correct time (I think just before I get the line with the login prompt) , it skipped the whole terminal thing and got me to my desktop without the CPU problem. I tried reproducing that result but it's apparently very tricky.


Hope anyone can help.
Regards,
Bram


PS: I can get my ubuntu to do anything. It's just noisy and I have to continuously plug it in.

There seems to be the same issue going on in Suse.  **however the last mention of it happening consistently was in the 2.6.24 to 2.6.27 kernels for which maverick uses a much later kernel**  If you can get the system to synaptic, make sure the kernel version you're using is the latest version which is at the time of posting, 2.6.35-23.37

---

### Post by brabox on 2010-11-16
Oh woops silly me. Apparently I delayed some updates in the synaptic system manager. Thanks a bunch!

---

### Post by brabox on 2010-11-16
EDIT:
How very odd.
First run after the update went like a charm. After a reboot however I'm back at square 1....
Any suggestions?

Regards,
Bram

---

### Post by yuki-nagato on 2010-11-16
> **brabox said:**
> EDIT:
How very odd.
First run after the update went like a charm. After the update however I'm back at square 1....
Any suggestions?

Regards,
Bram

You may want to submit a bug report.  This problem has been around for a while.  Googling just "ksoftirqd"  brings up quite a few results concerning this exact issue.

---

