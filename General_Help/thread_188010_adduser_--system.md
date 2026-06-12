---
title: "adduser --system"
date: 2006-06-03
forum: General Help
---

### Post by jtxx000 on 2006-06-03
What exactly does the system option do?  The man page isn't very clear on it's purpose.  I'm looking to add an underprivileged user to run a server daemon on, how would I go about this?

---

### Post by taurus on 2006-06-03
```

man useradd

```

---

### Post by jtxx000 on 2006-06-03
The man page for useradd isn't much more helpful than that for adduser.  It only says that IDs between 0-999 are reserved for system users without going into details about what the difference is between system users and normal users.

---

### Post by jtxx000 on 2006-06-03
Nevermind, this page seemed to shed some light on the subject: [http://www.debian.org/doc/manuals/securing-debian-howto/ch9.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch9.en.html)

---

