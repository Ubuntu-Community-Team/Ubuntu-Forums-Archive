---
title: "ulimit"
date: 2011-07-01
forum: General Help
---

### Post by nebu on 2011-07-01
Hi,
If I set /etc/security/limits.conf and enable the options for the security module in pam.d
And I restart my system why are the ulimits -a values not updated to show the values I put in limits.conf

by the way, I am using Ubuntu 11.04

---

### Post by Gryllida on 2011-07-02
- Please check that you use proper syntax.

[http://www.debian.org/doc/manuals/securing-debian-howto/ch4.en.html#s-user-limits](http://www.debian.org/doc/manuals/securing-debian-howto/ch4.en.html#s-user-limits)

- What is your limits.conf file contents?
- What is the username and usergroups of the user whose limits you're checking?

---

