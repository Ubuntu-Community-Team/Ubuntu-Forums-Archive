---
title: "can't log on as root"
date: 2010-08-11
forum: General Help
---

### Post by astroknott on 2010-08-11
I just installed Ubuntu on a Gateway NV52.  I am very impressed BTW.  Works perfectly.  I have one strange problem though.  When I installed it, it asked me for a password for either the administrator or root user I don't remember which it said.  And a user name and password for a regular account.  I wrote all this down so I have the passwords and such.  When Ubuntu starts the only option is for the regular account.  There is no root account to sign on to.  I have chosen the "other" option and used root as a user name and the password i wrote down.  No good.  I have tried using administrator as a user name, I have even tried using nothing as a user name.  No matter what I do I cant see how to log on as root.

Any help would be appreciated.

---

### Post by Unknown-Demon on 2010-08-11
There is no login for root. That's why you have a regular account to sign onto.
Login to the regular account and go to terminal and type 
```
su
```
And then it will ask for a password (when you enter your password you wont see it) for security reasons.
and then once you enter your password you should have root privileges.

---

### Post by wojox on 2010-08-11
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Frogs Hair on 2010-08-11
Try Administration> Users and Groups and see if you can change your account types from there with your working password.

---

### Post by astroknott on 2010-08-11
Thanks thats what I needed to know

---

