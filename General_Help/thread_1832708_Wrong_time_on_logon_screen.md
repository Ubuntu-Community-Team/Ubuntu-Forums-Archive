---
title: "Wrong time on logon screen"
date: 2011-08-25
forum: General Help
---

### Post by ghendric on 2011-08-25
When I first start up Ubuntu, at the logon screen before I click on any user name, the time showing is 4 hrs behind. Soon as I click on a user id to log in, then the correct time shows. 

Something is going on there that is causing the computer clock to adjust its time to 4 hrs ahead when I click on a user id and log in even though i see the correct time when I log in.

I have a dual boot system with Windows 7 on it. Windows isn't doing that because I can go into the BIOS after rebooting and the clock is 4 hrs ahead. This might be a bug in Ubuntu. 

Any one else having this issue?

---

### Post by ghendric on 2011-09-20
Does anyone know how to fix this?

---

### Post by dino99 on 2011-09-20
i've seen that too, but dont brake my day, so its a good question to post on launchpad (maybe a plymouth issue)

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
select "ask a question" on right side.

---

### Post by mcduck on 2011-09-20
Sounds like the common issue people have with the way Linux and Windows handle hardware clock, Linux by default assumes the system to use UTC and then displays local time to each user based on the set timezone, while Windows on other hand assumes that the system clock runs in local time...

This document should help: [https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime") (scroll down to the "Multiple Boot Systems Time Conflicts"-section)

---

### Post by ghendric on 2011-10-18
> **mcduck said:**
> Sounds like the common issue people have with the way Linux and Windows handle hardware clock, Linux by default assumes the system to use UTC and then displays local time to each user based on the set timezone, while Windows on other hand assumes that the system clock runs in local time...

This document should help: [https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime") (scroll down to the "Multiple Boot Systems Time Conflicts"-section)

This is only happening on one of my pc's... I'm thinking maybe there was something I didn't set correctly when I installed Linux on the problem pc.

---

