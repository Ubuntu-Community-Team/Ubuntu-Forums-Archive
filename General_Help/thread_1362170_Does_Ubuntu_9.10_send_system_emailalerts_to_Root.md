---
title: "Does Ubuntu 9.10 send system email/alerts to Root?"
date: 2009-12-22
forum: General Help
---

### Post by 55tptag on 2009-12-22
Does Ubuntu send system email/alerts to Root?
If yes, how do I read those emails? Do I need to install an email server?
Thank you.

---

### Post by dcstar on 2009-12-22
> **55tptag said:**
> Does Ubuntu send system email/alerts to Root?
If yes, how do I read those emails? Do I need to install an email server?
Thank you.

```
sudo dpkg-reconfigure postfix
```
Then set up your mail client to access your mbox file (in Evolution it is called "Local Delivery").

---

