---
title: "Laptop will not come out of suspend"
date: 2010-06-19
forum: General Help
---

### Post by kev3124 on 2010-06-19
Dell Inspiron E1505 will not come out of suspend mode. Running 10.04. When lid is closed the laptop suspends. When lid is opened, blank screen and will not resume from suspended state. With black screen (not coming out of suspend): Power light is on, laptop is on, bluetooth light is on. Hard restart needed, after restart networking is disabled and needs to be manually turned back on (even though it was on before going into suspend). 

Any ideas on how to fix this? I installed all updates and haven't made any changes to the system prefs. Suspend used to work without issue about 2-3 days ago. 

Note: screensaver is one of the 'GL' pre-installed ones, and have unticked the "lock screen when computer is idle". When SS comes on, mouse movement returns to desktop without issue. Also, accessing the laptop via a network is not possible.

---

### Post by Untergeher on 2010-06-28
Hi,

I am having the same issue: The screen goes to blank when I suspend, the computer stops responding, the "sleeping-diode" blinks happily - and a system restart is required. After restart, some settings are changed, networking is disabled, etc. Apparently, the computer goes successfully into suspend for a short time, there are no error messages in the pm-suspend log file. Suspend used to work until 3 days ago, just before I did an update. There are other threads describing similar problems. But I did not find any solution that would work for me.

I am running 10.4 64 bit on an x61s Thinkpad (model 7668 ).

I hope someone will help us. I'll let you know once I found a solution.
Untergeher

---

### Post by Untergeher on 2010-06-28
I also tried downgrading the pm-utils. Did not work.

---

### Post by Untergeher on 2010-07-01
I read something in another thread - many people seem have the same issue. What worked for me: remove removable media, i.e. SD cards. This works for me. I know this shouldn't matter, but I do not know how to fix this problem. Suspend works fine without removable media, but it causes the exact above issues if an SD card is in place.

I will keep looking for better solutions - reasons.

Untergeher.

---

### Post by loaba on 2010-07-02
I'm experiencing the same issue with my HP dv7-1245dx. Whenever I shut the lid, I can't get the thing to come out of suspend mode. I'll try the SD card solution.


EDIT: SD card solution worked... crazy. I wonder when they'll come up with a real fix.

---

### Post by apstanto on 2010-08-21
Having the same problem on an IBM Thinkpad with 10.04.  Let us know when somebody finds a solution.

---

### Post by johnalexrob on 2011-08-24
Mine does not have an sd card in it when it happens, but the strange thing is, I had an sdb. I had no other removable devices and fdisk couldn't open it and my computer has only one internal hard drive. I tried deleting it, but the computer still wouldn't come out of suspend. Oh well.

---

### Post by South Shore Pats Fan on 2011-08-27
I have an HP DV7 with the same problem.

---

