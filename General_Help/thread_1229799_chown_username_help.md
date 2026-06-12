---
title: "chown username help"
date: 2009-08-02
forum: General Help
---

### Post by bossltr on 2009-08-02
Hi 
I'm trying to change the ownership of folders on a second hard disk on my system.
The files were put on there using various versions of Linux over several years.
When I try to delete folders certain folder I get the message that I am not the owner.
My username has been pretty much the same. I found this suggestion using the search feature
sudo chown -R user:user /media/Partition3
However I am not sure what the original owner's exact spelling was.
Any ideas would be most appreciated
Brian Rodgers

---

### Post by The Cog on 2009-08-02
Whth chown, you need to give a name of a current user on the system. Chown looks up the name in /etc/passwd to get the users numeric ID. It is the numeric ID that is stored on the hard disk. So whatever the username used to be on previous system installations is irrelevant.

---

### Post by michy99 on 2009-08-02
Also, different distributions are not consistent in how they number users. Ubuntu makes the first user 1000, then 1001, 1002, etc., but some other distributions start at 500.```
sudo chown -R user:user /media/Partition3
```This should change everything to be owned by you if you use your username where it says user. It doesn't matter what the previous username was.

---

### Post by bossltr on 2009-08-30
Thanks gang this worked great, 
Brian:guitar:

---

