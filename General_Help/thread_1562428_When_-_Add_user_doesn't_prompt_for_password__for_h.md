---
title: "When - Add user: doesn't prompt for password  for him?"
date: 2010-08-27
forum: General Help
---

### Post by QuickSnail on 2010-08-27
Hi all,

Trying to "_adduser_" via SSH.  The new user name is accepted O.K. but it is not followed by prompt to *add a password* for the new user.  So we have a new name in the system but lacking a password.  How can i add a password for the new user?  ( This is in CentOS)

---

### Post by akoskm on 2010-08-27
> **QuickSnail said:**
> Hi all,

Trying to "_adduser_" via SSH.  The new user name is accepted O.K. but it is not followed by prompt to *add a password* for the new user.  So we have a new name in the system but lacking a password.  How can i add a password for the new user?  ( This is in CentOS)

Have you tried with
```

passwd <login>

``` ?
Replace the <login> with the users login name.
Hope this help.

---

### Post by QuickSnail on 2010-08-27
Oooops.

finally found it.

type the following command: 
***passwd username*** (where username is the username of the new user)   
This will prompt you to enter a password.  Enter the  password and press enter.  You will be asked to confirm the password.  Type the password in again and  press enter.  As long as you typed the same password in both times, you have finished adding a new user

---

