---
title: "help running command on system startup"
date: 2011-08-10
forum: General Help
---

### Post by lazerking9 on 2011-08-10
I'm not sure if this is posted anywhere else(google didn't come up with anything), but here it goes anyway..

Is there a simple way to have a command (or a very small BASH script) run on system startup? I have a terrible habit of leaving my computer on overnight, and my electric bill is starting to show it. I wrote a BASH script to automatically do some end-of-day-housekeeping, as well as shutdown the system at night. Can I get this to run on startup?

---

### Post by TeoBigusGeekus on 2011-08-10
Of course. Go to Startup applications (search for it if you're on unity or go to Administration>System - or was it Preferences? - if you're in classic gnome) and add it.

---

### Post by mikewhatever on 2011-08-10
I am not sure a startup script is the best was to do it. How about setting a cron job that would run at night and execute the script?
[Cron Howto]("https://help.ubuntu.com/community/CronHowto?action=fullsearch&context=180&value=linkto%3A%22CronHowto%22")

---

### Post by lazerking9 on 2011-08-10
thanks, CRON will solve it perfectly! And even if I need something closer to a bash script, i can always write one and have CRON execute that.

Splendid, thanks!:KS

---

### Post by dcstar on 2011-08-11
> **lazerking9 said:**
> I'm not sure if this is posted anywhere else(google didn't come up with anything), but here it goes anyway..

Is there a simple way to have a command (or a very small BASH script) run on system startup? I have a terrible habit of leaving my computer on overnight, and my electric bill is starting to show it. I wrote a BASH script to automatically do some end-of-day-housekeeping, as well as shutdown the system at night. Can I get this to run on startup?

/etc/rc.local

---

