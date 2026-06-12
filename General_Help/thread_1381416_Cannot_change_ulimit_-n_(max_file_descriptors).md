---
title: "Cannot change ulimit -n (max file descriptors)"
date: 2010-01-14
forum: General Help
---

### Post by R4KFFE on 2010-01-14
I have run into a limit of 1024 file descriptors. I have searched a lot and have tried various solutions. The **following methods have failed to change max file descriptors**

```
ulimit -n [new number]
```

```

File: /etc/pam.d/common-session
Add: session required pam_limits.so

File: /etc/security/limits.conf
Add: [user]             hard    nofile           [number]

```

**How can the max file descriptors be set in Ubuntu?**

---

### Post by Brandon Williams on 2010-01-15
For non-root users, the first method will probably only work to drop the limit, not to raise it.

The second method works on my karmic machines. Is the text you included exactly what is in your /etc/security/limits.conf file? Or did you replace the tags '[user]' and '[number]' with the correct user name and limit values?

---

