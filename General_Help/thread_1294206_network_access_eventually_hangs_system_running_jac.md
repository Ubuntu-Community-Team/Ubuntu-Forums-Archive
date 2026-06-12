---
title: "network access eventually hangs system running jackd, rt kernel"
date: 2009-10-18
forum: General Help
---

### Post by rmcgowan on 2009-10-18
Hi,

Please redirect me to the right place if this is not the right one. ;)

My setup:

Compag computer with Ubuntu Studio 9.04 (Jaunty Jackalope), MAudio Delta-1010 audio subsystem.  The system is used as a PA and an event recording tool.  Software is up to date as of about two weeks ago (beginning of October).  It is running the distribution RT kernel, with jackd and ardour as the main software in use.  I'v recorded events up to 78 minutes with only minor issues.

However, the system is not readily accessable during events.  In order to manage microphone muting and sound levels, I'd planned to use a laptop networked with the main system, using desktop sharing or ssh with Xforwarding to access the ardour display.

Networking is just fine, so long as I do not run audio applications (actually, I should say, jackd).  Shortly after starting jackd, the system hangs, hard.  It requires a power off/on and reboot to "recover".

I need some ideas for how to get this to work.

Thanks,

Bob

---

