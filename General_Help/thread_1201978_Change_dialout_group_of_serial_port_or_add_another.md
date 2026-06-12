---
title: "Change dialout group of serial port or add another group to dialout?"
date: 2009-07-01
forum: General Help
---

### Post by mswebersd on 2009-07-01
We have a group of users connecting to a server over NIS, and once logged in, they are a member of the "users" group.   

They need access to the /dev/ttyS0 serial port, which is owned by the dialout group.

I can chmod the permissions of the /dev/ttyS0 serial port every time the box reboots, but that's not a good solution.  Is there any way to change the default group of /dev/ttyS0 to "users"?  If not, is there a way to add the "users" group to "dialout"?

Thanks,
Mike

**SOLVED**

I added 

```
KERNEL=="ttyS0", MODE="0777"
```

to /lib/udev/rules.d/10-local.rules and rebooted.

---

