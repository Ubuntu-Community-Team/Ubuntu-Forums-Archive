---
title: "fglrx Bug that won't go away"
date: 2010-10-15
forum: General Help
---

### Post by gamer_pro_2000 on 2010-10-15
Alright guys.  I'm trying to figure out a bug with fglrx.  Whenever I go to log a machine out, sometimes the screen will go black and never come out of it.  Upon reviewing the system logs for XServer, I find the following: 
(II) Keyboard2: Close
(II) UnloadModule: "evdev"
(II) Mouse2: Close
(II) UnloadModule: "evdev"
(II) fglrx(0): Shutdown CMMQS
(II) fglrx(0): [uki] removed 1 reserved context for kernel
(II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x4e000 at 0x7f43d7474000
(II) fglrx(0): Interrupt handler Shutdown.
 ddxSigGiveUp: Closing log
For some reason, going back to the login screen will sometimes cause fglrx(0) to freak out and interrupt the logout process.  Any ideas how to force it to stop doing this or fix this issue?  I'm using the ATI proprietary drivers with the latest version.

---

### Post by gamer_pro_2000 on 2010-10-18
*bump*

---

### Post by professordes on 2011-04-26
Interesting, same bug and error message has appeared for me on updating an fglrx machine to 11.04 (was fine in 10.10).....

Crash on shutdown/suspend/logoff

    Ubuntu
    Bugs
    Bug #766272

---

### Post by Mark Phelps on 2011-04-26
> **professordes said:**
> Interesting, same bug and error message has appeared for me on updating an fglrx machine to 11.04 (was fine in 10.10).....

There have been problems reported with video in Natty.  Suggest you check in the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion

Good Luck

---

