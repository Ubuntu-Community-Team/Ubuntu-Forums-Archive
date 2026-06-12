---
title: "Demo CD 9.10 changes system clock"
date: 2010-03-28
forum: General Help
---

### Post by RichPasco on 2010-03-28
I booted the 9.10 demo CD from [http://www.ubuntu.com/](http://www.ubuntu.com/) and chose the option to Run Ubuntu without making any changes to my computer.  But a change was made, with potentially serious consequences.

I run Windows XP with my time zone set to U.S. Eastern Daylight Time (-0400) and my clock set to the correct time.  At 9:00 a.m. EDT, I booted the Ubuntu 9.10 demo CD, and when I quit, and re-booted Windows my system clock had been changed to 1:00 p.m. EDT -- a four-hour error.

Apparently the Ubuntu demo CD had changed the system clock to 1:00 p.m. but neither restored it on exit nor changed Windows time zone to UTC.  Thus my system was left displaying a local time four hours later than it really was.

This is potentially serious because my backup system overwrites older files with newer versions, according to the time stamp.  If the time had subsequently been corrected without my being aware of the issue, files modified in the four hours before the correction would have appeared newer than, and thus replaced, files modified in the four hours after it.

---

