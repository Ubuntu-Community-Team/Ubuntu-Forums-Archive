---
title: "how to control which ACtiveDirectory users can log in"
date: 2010-08-05
forum: General Help
---

### Post by gmoore777 on 2010-08-05
Using 64-bit LucidLynx, with winbind/samba (ActiveDirectory) authentication.

How would one control which users logged into this workstation
without doing something on the ActiveDirectory Server?

For example, we have 1000 ActiveDirectory users in the company
and they all can log into this one machine.
But I only want 3 of those users to be able to be allowed to log
in.
How does one do that?

Is there a section in /etc/samba/smb.conf whereas I can list
all the valid users?

Is there a PAM-related file where I would do something similar?

In other words, do i create a whitelist and put it somewhere?

---

### Post by Ovist on 2010-08-28
Bump
 
I too would like to know how to put specific users under an Active Directory, I have searched on "mysql user" and cannot find my answer.

---

