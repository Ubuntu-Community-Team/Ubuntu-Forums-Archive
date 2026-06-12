---
title: "Ubuntu 11.10 lots of apps crash when typing in them; chrome(ium), dropbox, etc."
date: 2011-12-07
forum: General Help
---

### Post by nxumdon on 2011-12-07
Hi
At some point in time since installing (fresh install) ubuntu 11.10 a problem started where whenever I type into the address bar of chrome/chromium, the login box of the dropbox setup, and a number of other apps, they just crash away with no error msg...I checked the syslog and this is what it shows...any thoughts?

Dec  7 13:45:56 hellportalgate kernel: [22428.111149] gksu[4211]: segfault at bf11affc ip b712dcc0 sp bf11b000 error 6 in libc-2.13.so[b706e000+176000]
Dec  7 13:50:24 hellportalgate kernel: [22695.978652] chromium-browse[4321]: segfault at bf5c9ffc ip b3d8e416 sp bf5ca000 error 6

Thanks

J

---

### Post by oldtimer7777 on 2011-12-07
Replace HDD?  How old is your equipment/components? Make/Model system? Details please.

> **nxumdon said:**
> Hi
At some point in time since installing (fresh install) ubuntu 11.10 a problem started where whenever I type into the address bar of chrome/chromium, the login box of the dropbox setup, and a number of other apps, they just crash away with no error msg...I checked the syslog and this is what it shows...any thoughts?

Dec  7 13:45:56 hellportalgate kernel: [22428.111149] gksu[4211]: segfault at bf11affc ip b712dcc0 sp bf11b000 error 6 in libc-2.13.so[b706e000+176000]
Dec  7 13:50:24 hellportalgate kernel: [22695.978652] chromium-browse[4321]: segfault at bf5c9ffc ip b3d8e416 sp bf5ca000 error 6

Thanks

J

---

### Post by BC59 on 2011-12-07
I think your programs are not compiled well. This is causing the trouble with segfault. Hopefully is only this.

---

### Post by BC59 on 2011-12-07
There is an easy way to check if the programs are not well compiled. Reinstall them. Go to Ubuntu software center and remove chromium. Then install it again. Do the same to Dropbox and the other apps not working. Then try to see if that solved the problem.

---

### Post by nxumdon on 2011-12-07
Hi
Reinstalling the apps dont help...same issue.

The system works fine running 11.10 live, my upgraded build from 8.04 now at 11.10 works fine...but the clean install does not.

Its mostly new hardware...decent ati graphics, core2 cpu, multiple gigs of ram all tests fine, multiple hard drives some mechanical some solid....

Guess I'll just re-install the O/S and watch for which update/package breaks it.

Thanks anyways.

J

---

### Post by PCman13 on 2011-12-16
I use Google Chrome. Same problem. It started happening when I upgraded from 11.04 to 11.10. Firefox works fine. Sadly, I use chrome too on other computers and I really like the sync feature.

This is really a problem to me, and others: [https://groups.google.com/a/chromium.org/group/chromium-bugs/browse_thread/thread/2486842f5c11eeb3/b4d32291ec22b614?lnk=raot](https://groups.google.com/a/chromium.org/group/chromium-bugs/browse_thread/thread/2486842f5c11eeb3/b4d32291ec22b614?lnk=raot)

I hope someone finds a solution.

---

