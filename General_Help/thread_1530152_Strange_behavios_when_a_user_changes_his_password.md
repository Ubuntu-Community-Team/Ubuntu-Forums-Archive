---
title: "Strange behavios when a user changes his password"
date: 2010-07-13
forum: General Help
---

### Post by Tha_Duck on 2010-07-13
Hi all,

First post here, so I hope that it is in the right category.

I have some strange behavior when a user logs in with an expired  password and he has to change it. He has to put in the old password 2  times, and then the new password 4 times. It looks like this on the  prompt:

user@server:~$ passwd
Changing password for user.
(current) UNIX password:
Changing password for user.
(current) UNIX password:
Enter new UNIX password:
Retype new UNIX password:
New UNIX password:
Retype new UNIX password:
passwd: password updated successfully
user@server:~$

In the auth.log I find the following:
Jul 13 10:06:49 server sshd[22622]: pam_unix(sshd:session): session  opened for user user by (uid=0)
Jul 13 10:06:57 server passwd[22630]: pam_unix(passwd:chauthtok):  password changed for user
Jul 13 10:07:03 server passwd[22630]: pam_unix(passwd:chauthtok):  authentication failure; logname=user uid=1003 euid=0 tty= ruser= rhost=   user=user
Jul 13 10:07:03 server passwd[22630]: pam_unix(passwd:chauthtok): user  password changed by another process

Very strange, I cannot get a clue why this goes this way. Some servers  do have the problem, some servers don't.

Anybody who recognize this and know a fix?

---

