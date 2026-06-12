---
title: "Clock running fast"
date: 2006-01-28
forum: General Help
---

### Post by redbull on 2006-01-28
My clock was always fine with 5.04, and when I first upgraded to 5.10. But somewhere along the way, I noticed that my clock was running fast and then before I hibernated it said that "the wait for clock tick timed out", which I have never seen before. It the device reference wrong or something? Please help.

P.S. And running NTP is not a solution, though that is what I'm doing now.

---

### Post by bernardfrancois on 2006-01-28
If it's the famous problem that the speed of the clock has been doubled or quadrupled, then you should have searched the forums first before posting. There are multiple threads about it.

---

### Post by redbull on 2006-01-29
No, it's not doubled or any obvious multiple. It's more like 10-20 minutes a day, depending on if the computer is on or hibernated. And it's not the clock battery, because Windows keeps the time.

---

### Post by bernardfrancois on 2006-01-29
If you can't find a proper solution there's always a way out by using a time server to keep your clock sync'ed(right-click the time in your task bar, choose '*adjust date & time*', and then check '*periodically synchronize clock with Internet servers*').

Since it's only 10-20 min a day, you could sync your clock for example every hour; then your clock's time will always be as close as a few minutes from the real time.

---

### Post by tseliot on 2006-01-29
Have a look at my guide: Double Clock Speed which is in my signature.

---

### Post by redbull on 2006-01-30
If I don't have 50% CPU usage, will your guide work?

---

### Post by RAOF on 2006-01-30
[QUOTE=redbull]If I don't have 50% CPU usage, will your guide work?[/QUOTE]
I've referred a number of people without 50% CPU usage to that guide, and it's fixed their problem.  Give it a whirl ;)

---

### Post by deathshadow on 2006-01-30
I've seen this two or three times on certain models of Dell - and it is COMPLETELY unrelated to the 'double clock' issue. It has nothing to do with the CPU clock, but the clock interrupt that handles the time... He's referring to the time clock, NOT the cpu clock. Two different entities (which are semi-unrelated)

the full message should say something like "select() to /dev/rtc to wait for clock tick timed out".

Been about a year since I've seen it, but the solution is a kernel patch available here:
[http://rtr.ca/dell_i9300/kernel/kernel-2.6.13/](http://rtr.ca/dell_i9300/kernel/kernel-2.6.13/)

you want the 'libata-suspend' patch.

Building and installing the latest stable vanilla kernel (2.6.15.1) may also solve the problem. (I REALLY wish they'd hurry up and fold 2.6.13 or newer into the damned repositories already)

---

### Post by RAOF on 2006-01-30
[QUOTE=deathshadow]...
(I REALLY wish they'd hurry up and fold 2.6.13 or newer into the damned repositories already)[/QUOTE]
They're not going to - it's essentially bugfixes only once a version is released.  Posting a bug to bugzilla attaching the patch that fixes it may get them to release a new, patched kernel image, but you won't be seeing 2.6.13 in the Breezy repositories.

---

### Post by s_spiff on 2006-01-30
well I don't quite know what 50% CPU useage refers to, but I have this wierd problem : I have both XP and Ubuntu on my pc... and If I set the Ubuntu time to the right time, the clock in XP gets messed up, and if I set the time in XP, the time in ubuntu gets scrwd up. Any solutions to this?

---

### Post by RAOF on 2006-01-30
[QUOTE=s_spiff]well I don't quite know what 50% CPU useage refers to, but I have this wierd problem : I have both XP and Ubuntu on my pc... and If I set the Ubuntu time to the right time, the clock in XP gets messed up, and if I set the time in XP, the time in ubuntu gets scrwd up. Any solutions to this?[/QUOTE]
Ask microsoft to fix Windows :)

The problem is: Ubuntu sets your clock to GMT, and applies your timezone when stuff asks for the time.  Windows sets your clock to the local time, and so doesn't apply any modifiers when something asks for the time.  So when Ubuntu has set the clock, it will be off by (-ve) your timezone (+10GMT for me) in Windows, and when Windows has set your clock it will be off by your timezone in Ubuntu.

---

### Post by bernardfrancois on 2006-01-31
[QUOTE=RAOF]Ubuntu sets your clock to GMT, and applies your timezone when stuff asks for the time.[/QUOTE]

Then the solution is: don't set a local time zone, but set your time to GMT in linux, and change the time so it matches your time.

---

### Post by s_spiff on 2006-01-31
all right, that worked. kept it as GMT and set the time to my locl time.. hehe, nice logic.

---

### Post by redbull on 2006-02-01
Thanks shadow. Is it possible to add a Dapper repository to my list and install that kernel, or is it unstable? If that's no good, can anyone point me to a good guide on installing/patching the kernel, as I've never done it. Also, is there any chance that since the name "libata_suspend" that is will fix my problem with suspending? at: 

[http://www.ubuntuforums.org/showthread.php?p=688855#post688855](http://www.ubuntuforums.org/showthread.php?p=688855#post688855) 

Thanks.

---

