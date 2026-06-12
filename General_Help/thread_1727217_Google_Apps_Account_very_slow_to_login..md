---
title: "Google Apps Account very slow to login."
date: 2011-04-12
forum: General Help
---

### Post by greenpeace on 2011-04-12
hi,

for the last few months my Google Apps account for work takes a small age to login, with both pidgin and empathy.

I have personal mail with google, and this account logs in very quickly... but my google apps one can take over 10 mins.

With pidgin it sometimes doesn't even login at all... very frustrating.

Has anyone else had this problem?  
Any suggestions for resolution or troubleshooting?



xxxx@xxxxx:~$ uname -a
Linux xxxxx 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

xxxx@xxxxx:~$ pidgin -v
Pidgin 2.7.3 (libpurple 2.7.3)

xxxx@xxxxx:~$ empathy -v
Empathy 2.32.1

---

### Post by thilina on 2011-05-04
I too have the same problem. :s

---

### Post by incognita on 2011-07-05
If anyone is still looking for a solution to this, the following worked for me:

Login ID: Your full email address
Encryption Required (check this)
Resource: Home
Server: talk.google.com
Port: 5223 (Use old SSL checked)

---

### Post by greenpeace on 2011-07-05
Amazing, that has worked for me!

---

### Post by incognita on 2011-07-19
Glad it worked!

---

### Post by incognita on 2011-07-19
> **greenpeace said:**
> Amazing, that has worked for me!

Can you please mark this thread closed then?

---

