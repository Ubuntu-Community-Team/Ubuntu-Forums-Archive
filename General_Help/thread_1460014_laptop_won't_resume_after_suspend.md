---
title: "laptop won't resume after suspend"
date: 2010-04-22
forum: General Help
---

### Post by help_me_please on 2010-04-22
hi all.
total linux noob here, please be gentle.
after searching around for quite a while, i couldn't find anything about my specific problem anywhere. there are quite a few problems that sound similar **but the behavior is different** so please read all the way through before sending me to one of the threads i have already been to.


_**the problem:**_
whatever way i suspend my laptop (menu, keyboard shortcut, close lid), it seems to suspend just find (no panic lights, suspend LED indicator flashing as expected). however, when i try to resume, the laptop seems to begin the proper wakeup process (for example, the DVD-drive is tested), there's a lot of HDD activity for about 5 seconds, screen does not power on, and then the laptop just shuts off.


**_system setup:_**
lucid beta 2, fully updated (just check now)
LG E-500 laptop /w nvidia gforce mobile 8400G
bios version 1.17 from June 2007 (not sure this is important)


**_things i tried:_**
* completely remove anything to do with gpu drivers and installed nvidia-current driver.

* suspend stress test described [here]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting"). this didn't work at all. the first test failed (with ac adapter attached) and the second test suspended but didn't automatically resume (see "the behavior" above). also, when i booted up again, no apport bug report is created. i tried both with rtc set to utc=yes and utc=no. with utc=yes, the second test did automatically resume, but the same problem happened (laptop shutdown while resuming).

* the debugging steps described [here]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Debugging Suspend"), but i couldn't get the "no_console_suspend" option to work. i tried adding both "no_console_suspend" and "no_console_suspend=1" (without quotes) to the boot script in the grub menu, but when i did pm-suspend in tty1, the laptop really did suspend. i would like to try to do this again if someone could explain how to add this option.



**_notes:_**
* not sure this is relevant, but when i boot up after a failed resume attempt, wireless network is disabled (this only happens after a failed resume!!!).

* i found a package called nvram-wakeup in synaptic that seems to be related to this. this package **is not installed**. should i install it?



i would love to provide more information if it is needed.

thanx in advance

Edit: in case this is relevant, forgot to mention i'm running ubuntu in dual-boot along side windows7.

---

### Post by help_me_please on 2010-04-23
shameless bump :P

---

### Post by cespinal on 2010-04-23
You are aware you are running a beta version dont you?

In my own experience, suspend problems have been gradually fading away with every new release. At the time I was having those problems, I was HARD to find any good workarounds. 

Have you considered installing a stable version?

---

### Post by Mark Phelps on 2010-04-23
Does suspend work in Win7 without problems?

I'm asking because I have not been able to get suspend/resume working in ANY versions of Ubuntu on my primary desktop and was genuinely surprised whe, after installing Win7, I discovered quite by accident that suspend/resume works just fine!  So, what I was presuming was a hardware problem was obviously an Ubuntu problem. 

Unfortunately, suspend/resume is one of the few long-term Linux problems that just won't go away.

I have three PCs that I dual-boot between a version of MS Windows and a version of Ubuntu, and in all three cases, the MS Windows suspend/resume works just fine and the Ubuntu suspend/resume fails.

And, I've tried everything I could find -- and nothing fixes the Ubuntu suspend/resume problems.

---

### Post by help_me_please on 2010-04-30
@cespinal: stable is out and still no joy. i also remember having these problems with 8.04, so i know what you mean when you say it is difficult to find good solutions.

@Mark Phelps: yea, windows suspend/resume works just fine.

i'm having trouble with acpi-related stuff in general - wrong battery state reporting (both wrong % and reported as on ac when on battery), over heating, cpu frequency management doesn't seem to work properly, etc.
LG (my laptop vendor) haven't put out a newer bios version for my machine, so no joy there.
i found somewhere that i perhaps the dsdt table contains errors, and that i might try using iasl to decompile it, correct the errors and recompile, but specific instructions were not included and i am afraid to tamper with low level stuff that i don't understand.
is the proposed idea a good 1? if so, can someone point me in the direction of a tutorial on the dsdt and how to fix it's errors?

i really like linux, but the broken acpi is a real problem for me.

---

### Post by kuckunniwi on 2010-07-20
I'm having the same exact problem. System suspends OK, but refuses to resume (although disk activity sounds like it's resuming, it never leads to actually system waking up...).

In my case, this is on a netbook with Ubntu 10.04 NBR. I have 10.04 Desktop Amd64 on another Laptop, and don't have this problem there.

---

### Post by Hack.The.Pow. on 2011-01-08
anybody figure this out?  I get the same error on my acer aspire ao521

---

### Post by cmavr8 on 2011-11-23
Still a problem in 11.10 (kernel 3.0.0-13-generic).
I just re-opened the corresponding bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333033").

Please comment there saying "I am also affected by this" so we can draw attention and show this problem is really serious for some people..

---

