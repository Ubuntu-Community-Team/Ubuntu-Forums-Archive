---
title: "User name help"
date: 2011-02-16
forum: General Help
---

### Post by fk4rp6 on 2011-02-16
I've created a new user under Ubuntu server.  The problem is when the user logins it doesn't show user@host:path.  All that is displayed is $.

I've also noticed that with this user when the command logout is used I get the message "-sh: logout: not found".

Not sure what's going on here, never had this problem before.

---

### Post by cjhabs on 2011-02-16
> **fk4rp6 said:**
> I've created a new user under Ubuntu server.  The problem is when the user logins it doesn't show user@host:path.  All that is displayed is $.

I've also noticed that with this user when the command logout is used I get the message "-sh: logout: not found".

Not sure what's going on here, never had this problem before.

Sounds like you may have the wrong shell - should be /bin/bash by default.

---

### Post by fk4rp6 on 2011-02-16
That fixed the problem, thank you.

---

### Post by cjhabs on 2011-02-19
Great - can you please mark the thread as solved?

---

