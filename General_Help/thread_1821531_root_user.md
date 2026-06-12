---
title: "root user"
date: 2011-08-09
forum: General Help
---

### Post by spawn82 on 2011-08-09
Hi all haven't been on for a while i do apoligise, 

a little while ago my facebook account got hacked as a precaution i changed 
passwords for just about everything but i forgot to change my password for 
the root user it is still the old one wich i have forgoton.
what can i do so i can log in as root user :-k

---

### Post by sisco311 on 2011-08-09
By default, in Ubuntu, the root account password is locked. If you have an admin account with full sudo rights, then the best thing you could do is to (re)lock the root account. See: [uhelp]community/RootSudo[/uhelp].

---

### Post by anaconda on 2011-08-09
you shouldn't give root a password. 
Root password is disabled in ubuntu by default.

However. if you have already given root a password you can (propably) change it using sudo as a normal user
eg: (from terminal)
sudo passwd root
and then give the new passwd

I once tried editing the /etc/shadow -file from liveCD so that I changed the encrypted password in that file to another users encrypted password (which I knew) and it worked...

---

