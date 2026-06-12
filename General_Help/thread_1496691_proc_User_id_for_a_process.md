---
title: "/proc/ User id for a process"
date: 2010-05-29
forum: General Help
---

### Post by z0rgy on 2010-05-29
[LEFT][SIZE=3]Hi,
[/SIZE][SIZE=3]How can I obtain the user that owns the process from /proc/process_id ?
[/SIZE][SIZE=3]Is it the Uid in /proc/process_id/status ? If so why are there 4 values ther[/SIZE][SIZE=3]e?[/SIZE][/LEFT]

---

### Post by sdennie on 2010-05-29
/proc/PID/status is the place to look.  As for the 4 columns, from the kernel documentation on /proc/PID/status:

```

Uid                         Real, effective, saved set, and  file system UIDs

```

---

### Post by z0rgy on 2010-05-29
Thanks :)

---

