---
title: "Weird grub"
date: 2011-01-01
forum: General Help
---

### Post by Mosabama on 2011-01-01
Yo,

When I start my computer, before the grub menu appears, a message says boot failed "for less than a second" and then the menu shows.

some times it takes 1 minute until the menu shows !!!

I did update-grub ... but nothing changed.

any idea ?

---

### Post by Rubi1200 on 2011-01-01
Do you only have Ubuntu installed or do you also have Windows?

How did you install it; to the hard-drive or via Wubi?

Thanks

---

### Post by Mosabama on 2011-01-01
I installed windows first and then ubuntu 10.10.
and I installed ubuntu from the live CD not wubi.

actually it doesnt take time any more, but the fake boot failed message is still there.

Thanks for your reply

---

### Post by Rubi1200 on 2011-01-01
No problem, you are more than welcome :-)

If you want to try and track this down, start looking at the logs for messages about failed boot.

The relevant logs are dmesg, syslog, and kern.log

Hope this helps.

---

### Post by Mosabama on 2011-01-01
```

reeing initrd memory: 10504k freed
Dec 26 06:49:50 mosab-Lap kernel: [    0.816075] EISA: Probing bus 0 at eisa.0
Dec 26 06:49:50 mosab-Lap kernel: [    0.816081] EISA: Cannot allocate resource for mainboard
Dec 26 06:49:50 mosab-Lap kernel: [    0.816085] Cannot allocate resource for EISA slot 1
Dec 26 06:49:50 mosab-Lap kernel: [    0.816088] Cannot allocate resource for EISA slot 2
Dec 26 06:49:50 mosab-Lap kernel: [    0.816090] Cannot allocate resource for EISA slot 3
Dec 26 06:49:50 mosab-Lap kernel: [    0.816093] Cannot allocate resource for EISA slot 4
Dec 26 06:49:50 mosab-Lap kernel: [    0.816096] Cannot allocate resource for EISA slot 5
Dec 26 06:49:50 mosab-Lap kernel: [    0.816099] Cannot allocate resource for EISA slot 6
Dec 26 06:49:50 mosab-Lap kernel: [    0.816102] Cannot allocate resource for EISA slot 7
Dec 26 06:49:50 mosab-Lap kernel: [    0.816105] Cannot allocate resource for EISA slot 8
Dec 26 06:49:50 mosab-Lap kernel: [    0.816107] EISA: Detected 0 cards.
Dec 26 06:49:50 mosab-Lap kernel: [    0.816446] cpuidle: using governor ladder
Dec 26 06:49:50 mosab-Lap kernel: [    0.816763] cpuidle: using governor menu
Dec 26 06:49:50 mosab-Lap kernel: [    0.817191] TCP cubic registered
Dec 26 06:49:50 mosab-Lap kernel: [    0.817384] NET: Registered protocol family 10
Dec 26 06:49:50 mosab-Lap kernel: [    0.817929] lo: Disabled Privacy Extensions
Dec 26 06:49:50 mosab-Lap kernel: [    0.818201] NET: Registered protocol family 17
Dec 26 06:49:50 mosab-Lap kernel: [    0.820504] Using IPI No-Shortcut mode
**Dec 26 06:49:50 mosab-Lap kernel: [    0.820639] PM: Resume from disk failed.**
Dec 26 06:49:50 mosab-Lap kernel: [    0.820651] registered taskstats version 1
Dec 26 06:49:50 mosab-Lap kernel: [    0.821104]   Magic number: 6:413:823
Dec 26 06:49:50 mosab-Lap kernel: [    0.821210] rtc_cmos 00:05: setting system clock to 2010-12-26 06:49:30 UTC (1293346170)
Dec 26 06:49:50 mosab-Lap kernel: [    0.821214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 26 06:49:50 mosab-Lap kernel: [    0.821216] EDD information not available.
Dec 26 06:49:50 mosab-Lap kernel: [    0.834781] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3

```

This is what I could get !

---

### Post by Rubi1200 on 2011-01-01
I can't say for sure, but this may have something to do with Suspend/Hibernate. I never use those functions because I know on some computers/some Ubuntu versions it can be an issue.

If you have been doing this, then that is the answer. If not, I am not sure what to tell you.

---

### Post by drs305 on 2011-01-01
I get messages from time to time that are too quick for me to read. I just purge and reinstall grub and they go away. Usually it's a message about a background image not found, or some minor issue that really doesn't affect the system. I purge/reinstall G2 a lot so it only takes me a minute or so, but I wouldn't suggest you do it for something relatively minor. (But I'll tell you how if you really want to know.)

I think the "resume" entry in the logs is fairly normal. I believe the system checks for a hibernated/suspended system as it boots and generates that message. I have the same message in my dmesg log, but I don't get the grub message. 

You might check the remainder of the log and see if there is a long delay somewhere. Mine totals 24 seconds. If you find a long lapse, you might be able to determine what the system is waiting for.

---

