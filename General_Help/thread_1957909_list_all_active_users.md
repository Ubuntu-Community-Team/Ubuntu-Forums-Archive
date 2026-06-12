---
title: "list all active users"
date: 2012-04-13
forum: General Help
---

### Post by mErchamion on 2012-04-13
How do I do that in ubuntu oneiric? the 'who', 'lastlog', 'last' commands do not show the x sessions (normal sessoins on ubuntu), but only terminal sessions. 

Thankyou in advance!

---

### Post by raja.genupula on 2012-04-13
use finger command

---

### Post by SeijiSensei on 2012-04-13
```
ps aux | awk '{print $1}' | sort | uniq
```

---

### Post by mErchamion on 2012-04-13
Sorry guys, something is not working for me. I have, for instance, 2 users on my system, user1 is admin and user2 is desktop user. when using finger, only user1 is listed. When using ps aux pipe, many users are listed (daemon, root, syslog, etc) but not user2. There should be an easier way! I also tried command users, but the same behavior.

---

### Post by mErchamion on 2012-04-13
ok, I got what I needed with dm-tool command:

$dm-tool list-seats

this gives me all the users that are loged in in x sessions, but not those who are on ttys or ssh'ing.  That I can get through who or users commands (or finger, but it is not built in)

---

