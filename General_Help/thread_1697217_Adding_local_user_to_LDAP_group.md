---
title: "Adding local user to LDAP group"
date: 2011-02-28
forum: General Help
---

### Post by natomb on 2011-02-28
... or enable *su* command for LDAP user.

Here is a brief description of my situation:

I have a machine offering "FreeNX". On that machine I have an *admin* user that has "sudo"-permission (i.e. the first user created during setup). This *admin* user is managed in the local user management files (/etc/passwd, ...) .

I also have an LDAP up and running. There I have a user *user*. This user is member of the *nx* group. For some reasons, I had to move the *nx* group into the LDAP.

Log in via FreeNX using user *user* works fine.

But log in via FreeNX using user *admin* does not work, because *admin* is not member of group *nx*.

Trying "usermod -a -G nx admin" did not add the *admin* to *nx* group.

What I could also live with is log in using user *user* and then "su" to *admin* (as I know the password, this would be little of a problem). Yet, trying so resulted in the following messages:

Feb 28 21:04:50 nx unix_chkpwd[19537]: check pass; user unknown
Feb 28 21:04:50 nx unix_chkpwd[19537]: password check failed for user (admin)
Feb 28 21:04:50 nx su[19512]: pam_unix(su:auth): authentication failure; logname=user uid=3001 euid=3001 tty=/dev/pts/5 ruser=user rhost=  user=admin
Feb 28 21:04:52 nx su[19512]: pam_authenticate: Authentication failure
Feb 28 21:04:52 nx su[19512]: FAILED su for admin by user
Feb 28 21:04:52 nx su[19512]: - /dev/pts/5 user:admin


Do you have any solution? Both ways, adding local user *admin* to the LDAP group *nx*, or enabling LDAP user *user* to "su" to local user *admin* would be acceptable. While the log is quite recent, I am working on this problem for nearly a week now.


Thanks in advance
  Bjoern

---

