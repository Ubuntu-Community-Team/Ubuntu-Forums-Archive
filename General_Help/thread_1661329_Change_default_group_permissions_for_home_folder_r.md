---
title: "Change default group permissions for home folder read/write"
date: 2011-01-06
forum: General Help
---

### Post by Tyler_Nieman on 2011-01-06
I have Ubuntu machines set up to login with Kerberos/LDAP so that it creates a home folder for each (new) user that logs into the client machine.  The home folders created are, by default, read-access between each other, but I would like to restrict this to so they cannot have read access. Is there a way to change the default group permissions for inter-file access between home folders?

EDIT - All of the users that login are in the same group, so I was hoping there's a way to change the default permissions on the group itself. If there's another way to do this (that isn't manually updating each of the folders), please share (:

EDIT - Solved!

With pam_mkhomedir.so in /etc/pam.d/common-session, I changed

```
session    required     pam_mkhomedir.so skel=/etc/skel/
```to
```
session    required     pam_mkhomedir.so skel=/etc/skel/ umask=0077
```The umask 0077 allows for the user to have all permissions and group/other to have none.

---

### Post by dcstar on 2011-01-07
> **Tyler_Nieman said:**
> I have Ubuntu machines set up to login with Kerberos/LDAP so that it creates a home folder for each (new) user that logs into the client machine.  The home folders created are, by default, read-access between each other, but I would like to restrict this to list-only.
........

Standard Linux permissions are Read, Write and Execute, there is no "List". Linux is not Windows.

---

### Post by Tyler_Nieman on 2011-01-07
> **dcstar said:**
> Standard Linux permissions are Read, Write and Execute, there is no "List". Linux is not Windows.

Pardon me.  I swear I could have come across this yesterday (as I was working with some permissions and haven't used Windows for any sort of file management in years), but perhaps I'm just imagining things.  I have edited my first post accordingly.  Thanks for your response.

---

### Post by luvshines on 2011-01-07
How exactly is the home directory being created on the fly ?

---

### Post by Tyler_Nieman on 2011-01-07
> **luvshines said:**
> How exactly is the home directory being created on the fly ?
With pam_mkhomedir.so.  I actually played around with it a bit and got it working with umask.

in /etc/pam.d/common-session, I changed

```
session    required     pam_mkhomedir.so skel=/etc/skel/
```to
```
session    required     pam_mkhomedir.so skel=/etc/skel/ umask=0077
```The umask 0077 allows for the user to have all permissions and group/other to have none.

I have edited the title to [SOLVED]

---

