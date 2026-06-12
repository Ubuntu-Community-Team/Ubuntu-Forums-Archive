---
title: "firmware directory??"
date: 2006-04-15
forum: General Help
---

### Post by Elif Tymes on 2006-04-15
Hey, what would the firmware directory be for Kubuntu?

/lib/firmware?

Also, is there anything I would need to define in order to create the firmware directory?

---

### Post by cilynx on 2006-04-15
Inside of /lib/firmware, there should be a subdirectory for each kernel version you have installed.  The firmware that ships with the kernels goes there.

---

### Post by Elif Tymes on 2006-04-15
well, the problem is lib/firmware/ doesn't exist

Did alot of searching, and found out that the firmware is stored in /usr/lib/hotplug/firmware

---

### Post by cilynx on 2006-04-15
Maybe this is a differency Breezy to Dapper.  On my machines, "hotplug" is obsoleted and thus the firmware directory has been moved.  Sorry for the confusion.

---

