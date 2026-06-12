---
title: "added new user but can't see the shell prompt."
date: 2010-04-08
forum: General Help
---

### Post by adhg on 2010-04-08
Hi there,
I just added a new user to my ubuntu by:

useradd -gdevelopers -d/home/peter -m peter

when peter logs in (after I created a passwd for him) he doesn't see the shell as I do:

me:
adhg@server:~$ 

peter
$

ALSO, he can't user the TAB to move inside a folder (when you type cs /home/p  and use tab to get /home/peter)

can anyone advise why? 

Thank you

---

### Post by dominiquec on 2010-04-08
useradd is a low-level utility for adding users.  For Ubuntu, you should use adduser instead.

What happened is: useradd created the user but didn't create the home directory or the proper entries in /etc/passwd.

I suggest: delete the user (userdel) and create it again.

---

### Post by adhg on 2010-04-08
yep, thanks!

---

