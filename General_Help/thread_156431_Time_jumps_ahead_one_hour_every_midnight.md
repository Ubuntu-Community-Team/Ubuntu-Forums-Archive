---
title: "Time jumps ahead one hour every midnight"
date: 2006-04-07
forum: General Help
---

### Post by Insyte on 2006-04-07
I have a pair of breezy boxes that, ever since daylight savings time started, have been jumping ahead one hour every night shortly after midnight.  My BIOS clock is set to UTC and I have /etc/localtime symlinked to /usr/share/zoneinfo/US/Central.  The output of 'date' indicates that I'm in the correct timezone (CDT):

swozzle:~ ben$ date
Fri Apr  7 00:39:30 CDT 2006

I thought maybe something whacky was happening with ntpd, so tonight I disabled ntp on one of the boxes and left the other alone.  Then I logged the output of 'date' once every minute.  This is what I got on both boxes:

Thu Apr  6 23:57:07 CDT 2006
Thu Apr  6 23:58:07 CDT 2006
Thu Apr  6 23:59:07 CDT 2006
Fri Apr  7 00:00:07 CDT 2006
Fri Apr  7 00:01:07 CDT 2006
Fri Apr  7 01:02:06 CDT 2006
Fri Apr  7 01:03:06 CDT 2006

I have UTC set to "yes" in /etc/default/rcS

Any thoughts?  Everything I've read seems to indicate that this is the correct setup, yet it fails...

Oh, and my libc6 version is 2.3.5-1ubuntu12.5.10.1.

Thanks!

-Ben

---

