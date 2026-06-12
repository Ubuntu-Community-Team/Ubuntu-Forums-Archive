---
title: "access.conf Manipulation"
date: 2010-10-12
forum: General Help
---

### Post by sid.mallya on 2010-10-12
Okay, this is actually a school homework, but I couldn't figure it out so posting here as the final option. :popcorn:

We have use /etc/pam.d/login in order to restrict the access privileges for regular users. Now, part of the assignment was to disallow login to user say, X on a Wednesday betn certain times. I did this using the shared object, 'pam_time.so' and editing the 'time.conf' file in /etc/security.

Now, the second part of the exercise is to restrict the number of executions a user can have. The hint says I have to do so using 'access.conf' but even after reading the documentation online and in Linux, I wasn't able to do so.

How to do I do it ? Say, the user is allowed only 10 executions.

---

