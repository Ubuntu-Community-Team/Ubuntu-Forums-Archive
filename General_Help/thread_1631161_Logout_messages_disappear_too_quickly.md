---
title: "Logout messages disappear too quickly"
date: 2010-11-26
forum: General Help
---

### Post by mynot on 2010-11-26
Ubuntu 10.04 - when I logout I get screenful (at least) of messages all with the same format. They disappear too quickly to see what they're about. I've looked at the logs but can't see anything like what I see on the screen. Is there any way I can find them?
Thanks
Tony

---

### Post by WorMzy on 2010-11-26
Are you sure they happen when you log out, and not, say, when you shut down?

If you've disabled the bootsplash, then you'll (probably*) get a report of daemons shutting down, filesystems unmounting, etc. when shutting down. That's perfectly normal.



*I don't use Ubuntu without a bootsplash that often.

---

### Post by mynot on 2010-12-03
Thanks. It's when I log out. After many repeated logouts I've worked out that it's to do with SYSFS and ATTR. Not too sure what it means but there's lots about it on the web. I'll look into it further.
Tony

---

