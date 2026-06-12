---
title: "no password, read only user"
date: 2010-11-09
forum: General Help
---

### Post by hwttdz on 2010-11-09
I'd like to add essentially an anonymous user, which does not require a password.  Second I think it's probably a good idea to only give this user very limited permissions, is there a way I can restrict the commands that they can run to a list (i.e. they should be able to run scp, ls, cd, maybe a few more, but not much)?

---

### Post by Hippytaff on 2010-11-09
When you create a newuser, they are not in the sudoers file automatically, so they are fairly restricted anyway. :-)

---

### Post by hwttdz on 2010-11-09
Sure they're not in sudoers, but They should have no reason to even write files to their own home directory, so I can't see why I should give them this permission.  If it causes an issue later I can always expand permissions.  

Any ideas on how to remove the password?

---

### Post by sisco311 on 2010-11-09
> **hwttdz said:**
> Sure they're not in sudoers, but They should have no reason to even write files to their own home directory, so I can't see why I should give them this permission.  If it causes an issue later I can always expand permissions.  

Any ideas on how to remove the password?

Users form the nopasswdlogin group are allowed to log in without a password. Not sure about the restricted shell...

---

### Post by hwttdz on 2010-11-09
After running 
passwd -d username
and 
passwd -S username 
I see that username has "NP" or no password, but when I attempt to ssh or su as username I get a permission denied.  Same behavior after adding user to nopasswdlogin.

---

### Post by hwttdz on 2010-11-10
Replacing common-auth in /etc/pam.d/su and ssh with the stanza given here [https://singpolyma.net/2009/11/anonymous-sftp-on-ubuntu/](https://singpolyma.net/2009/11/anonymous-sftp-on-ubuntu/) seems to do the trick.  So passwd -d user, add to nopasswdlogin and update pam rules.  Marking as solved.

---

