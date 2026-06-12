---
title: "Individual User Limits"
date: 2012-01-25
forum: General Help
---

### Post by hantechbl on 2012-01-25
Hello, 
I would like to set user limits for individual users, so for example it would limit RAM, Disk Space, CPU %.  Also if I could set process limits for infinite fork protection that would be great.  I've seen solutions like ulimit, but that appears to be a system-wide limitation.

---

### Post by dcstar on 2012-01-25
> **hantechbl said:**
> Hello, 
I would like to set user limits for individual users, so for example it would limit RAM, Disk Space, CPU %.  Also if I could set process limits for infinite fork protection that would be great.  I've seen solutions like ulimit, but that appears to be a system-wide limitation.

[http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)

---

### Post by hantechbl on 2012-01-25
I'm not quite sure how exactly this affects user limits, there's not much of an explanation on setting limits.  Is there a format for the quota?

---

### Post by Sazhen86 on 2012-01-26
You can set limit values for individual users in /etc/security/limits.conf

Hope that helps.

---

