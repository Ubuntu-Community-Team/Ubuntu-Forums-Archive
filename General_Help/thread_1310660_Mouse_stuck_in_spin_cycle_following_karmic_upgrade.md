---
title: "Mouse stuck in spin cycle following karmic upgrades"
date: 2009-11-02
forum: General Help
---

### Post by valadil on 2009-11-02
Hi.  I upgraded to karmic.  Initially I upgraded over apt, but that didn't work out so I did a full reinstall.  In both cases my mouse spins as though busy pretty much constantly.  It's ****ing annoying.  Oddly enough my gf's account doesn't have this problem.  Any ideas?

---

### Post by Crumbles on 2009-11-11
Does it for me too.  Welcome to hell.  Every problem I've had on ubuntu has never been answered here on the forums.  So.... good luck!

---

### Post by valadil on 2009-11-11
> **Crumbles said:**
> Does it for me too.  Welcome to hell.  Every problem I've had on ubuntu has never been answered here on the forums.  So.... good luck!

Yeah, unless the solution involves "sudo wget something.deb" or "sudo sh some_script_you_downloaded_and_havent_read.sh" it doesn't usually exist here.

Anyway I found an answer for this problem.  It is caused by GDM auto login.  Using timed or standard login fixes it.  I still wanted auto login, so I set timed to 1 second.

---

