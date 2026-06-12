---
title: "user management logs"
date: 2006-05-11
forum: General Help
---

### Post by trawler on 2006-05-11
Hi,

I recently got a sudo user for a debian server at work, for a work-related project.

I found out there were more than a healthy sum of sudo users already set up on the machine, some of them don't even work there anymore, but for some reasons use that server for their own reasons...

I decided to not yet change any of the users, untill i find out which is legitimate and which is not.

what is disturbing, however, is that twice already, my password had been changed (in the middle of work! :mad: ) by someone with root privileges, obviously. luckily, there's one more sys admin - to whom i went to twice already to change my password back.

I would like to know if there are any logs which i can check to see who that user was... who messed around with user management and whatnot.

since debian is very much like ubuntu, i'm hoping someone might have an idea :)

---

### Post by hw-tph on 2006-05-11
The default syslog setup in Debian logs all sudo messages to /var/log/auth.log. sudo is very useful since you can see who has done what: **grep sudo /var/log/auth.log** and look at the COMMAND part.


Håkan

---

