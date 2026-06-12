---
title: "Super newbie evolution question"
date: 2009-09-25
forum: General Help
---

### Post by blm14 on 2009-09-25
I have just migrated from Win XP to Ubuntu (2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux), yay me! I am using evolution mail with IMAP which I like so far, but I have a question about the calendar.

When I was in outlook, if I had a reminder set up for an event, I would get a popup which would persist until I "dismissed" it. It appears that in evolution, when the alert comes up that I have an appointment, it flashes for a few seconds and then just vanishes. Is there a way to make those alerts persist in some kind of modal popup? 

Please forgive my newbie-ness. The last time I used unix was System V. :)

---

### Post by Commander_Keen on 2009-09-25
Although I dont' have a reall answer for you.
You may want to google Evolution. as its host site does have a user guide and a FAQ..

---

### Post by mbeach on 2009-09-25
not exactly sure if this is the same issue, but this solution is quoted at the link below:
> **the real omni said:**
> 
anyone else who wants to make Evolution just pop up the alert dialog with the snooze button directly instead of a tray alert, here's the fix:

1) ALT+F2 for a run dialog, and type 'gconf-editor'

2) navigate to apps/evolution/calendar/notify

3) de-select the 'notify_with_tray' entry.

source:
[http://ubuntuforums.org/showthread.php?t=874333](http://ubuntuforums.org/showthread.php?t=874333)

---

