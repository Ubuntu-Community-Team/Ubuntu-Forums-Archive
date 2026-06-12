---
title: "How do I log out another user?"
date: 2010-07-21
forum: General Help
---

### Post by saking on 2010-07-21
I am using a desktop computer with limited memory.  If I log in whenever someone else has forgotten to log out, the system becomes very slow.

Is there a way, as a user with admin privileges, to log out another user?

Thanks,
Steve

---

### Post by amauk on 2010-07-21
```
sudo pkill -KILL -u username
```

this will terminate all processes owned by username
It's brutal, but it'll log them out

---

### Post by saking on 2010-07-21
That works.

Thanks!

---

