---
title: "Migrating user info from Redhat to Ubuntu"
date: 2010-02-12
forum: General Help
---

### Post by seanmccaskey on 2010-02-12
Ack!!  I must be lame or something.  

I have followed the instructions here:[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)  for moving my accounts from my old RedHat 9 something server to my new Ubuntu 9.10.  I was able to get the home directories all set up and Apache  works fine with them... however the user accounts are a different story.  None of the accounts I have appended per the instructions work.  With the help f this forum, I was able to set my login.def to allow for UIDs 500 and up , so I can see them.  I can even change the password for the accounts but I still get authentication failed when I try to login as them

What am I doing wrong?

---

### Post by jken146 on 2010-02-12
Have you set the right permissions on the directories in /home ?

---

### Post by seanmccaskey on 2010-02-13
> **jken146 said:**
> Have you set the right permissions on the directories in /home ?
 
The directory list shows the /home folders with the proper owner and group.  I did not chown them... would that make a difference?  
 
What log file should I be looking at for authentication failed?

---

