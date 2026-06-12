---
title: "evolution exchange 2003 calendar sync issues"
date: 2009-12-03
forum: General Help
---

### Post by nixIT on 2009-12-03
Hello all,

running Ubuntu 9.04 and about 2 weeks ago, I noticed my calendar in evolution was missing meetings.  I looked in OWA, and the meetings are there.

I ran the "rm ..." command to remove and then resync evolutions mail, but that did not fix the out of sync (missing calendar events) in evolution.

We are running exchange 2003 here at work.

Any way to resync my evolution calendar?

--nixIT

---

### Post by rchille on 2009-12-04
I'm running into the same trouble with Exchange 2007 and evolution-mapi plugin 0.28.1. Is this what you are running also?


I can see the meetings in OWA and I get this in the evolution debug:

```
|---+ Calendar        : (Container class: IPF.Appointment 1D9894311D000001) UnRead : 0 Total : 2 size : 5657
```


But when I try to do anything with that calendar I see a "Unable to open the calendar" message

---

### Post by nixIT on 2009-12-09
yes, I have the mapi plugin but we are using Exchange 2003.

---

### Post by jwkaisd on 2010-02-02
I am relatively new to using Evolution, but I have this same experience.  We are using Exchange 2003 at work, and many of my calendar events do not show up on evolution.

Is there any way to fix it?  This is extremely frustrating - definitely the most buggy program I have seen under Linux.

Cheers!
john

---

