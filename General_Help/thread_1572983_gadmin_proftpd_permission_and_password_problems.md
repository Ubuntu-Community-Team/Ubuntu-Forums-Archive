---
title: "gadmin proftpd permission and password problems"
date: 2010-09-12
forum: General Help
---

### Post by burgundy on 2010-09-12
I'm not sure where to ask this question, but my gadmin-proftpd is having user password issues and when I try to 'cd' into the /etc/gadmin-proftpd folder with 'sudo' I get a 'sudo: cd: command not found'.

I can do a sudo ls -all on the folder but I can't go into it?

The only reason I care is because this is where gadmin keeps all its important user data?

For some reason when I use gksudo gadmin-proftpd I still don't have sufficient permissions to make and edit new user passwords for my proftpd TLS server.  None of the changes are saved.  I can change a password and gadmin doesn't complain, but when I try to actually use it, proftpd says the password is wrong.  Then I change it back to the old password and everything works fine.

While this isn't the end of the world, it would be nice to be able to create/change users and passwords instead of only having one single account.

I think there is some kind of error in the permissions and ownership of these configuration files, but I don't know where to begin since my understanding of all *nix permissions settings is very informal.

I'm using Ubuntu 10.04.

---

