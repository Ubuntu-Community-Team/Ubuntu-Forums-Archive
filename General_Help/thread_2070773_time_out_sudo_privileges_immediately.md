---
title: "time out sudo privileges immediately?"
date: 2012-10-13
forum: General Help
---

### Post by Hekabe on 2012-10-13
How do I make sudo require a password every use in terminal? As in, once you do one sudo operation, sudo stays authorized for five minutes unless you specifically revoke it (sudo -k). how do I make it time out immediately?
Note: I'm running Ubuntu Studio 12.4, and I use Guake for all my terminal stuff. Don't know if that would affect it.

---

### Post by Cheesemill on 2012-10-13
It's in the documentation:

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by Hekabe on 2012-10-13
Thanks a lot. Now my paranoia is satisfied.

---

### Post by Lars Noodén on 2012-10-13
You can set it for the whole set of users by making it the default.

```

Defaults        timestamp_timeout=0

```

Or you can set it for some users and not others.  The full explanations of options is in the manual page for [sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html).

---

