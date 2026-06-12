---
title: "Wubi (Ubuntu 12.04) installation - wrong user name ?"
date: 2012-06-29
forum: General Help
---

### Post by Lavix on 2012-06-29
Not sure to post to the right category, so sorry for that. Here is a strange behaviour I discovered after installing Ubuntu 12.04 on a Windows 7, 64 bits box in dual boot by using wubi Windows installer. During the installation I was asked for a user name and a password for Ubuntu user account. After the installation was successfully finished, I discovered that:

[LIST]
[*]the only existing user logged in GNOME was the same as the Windows' one (i.e. on the Windows box there was ONE and the ONLY user named as USER1). Ubuntu had ONE and the ONLY user also named as USER1 with the same password as on Windows. Nevertheless, during the installation I entered USER2 and PASSWORD2 as credentials for Ubuntu .
[*]when I open a terminal, I can see that I'm no more USER1: user2@ubuntu:~$ instead of user1@ubuntu:~$ 
Is it normal?
[*]More of that, if I try to add a User named as USER2 (i.e. exactly the same that was entered during the installation), it doesn't pass.
[/LIST]
Any suggestions or ideas? Thank you.

---

### Post by bcbc on 2012-06-29
Wubi assigns the username 'description' as the windows account name:
[https://bugs.launchpad.net/wubi/+bug/790347](https://bugs.launchpad.net/wubi/+bug/790347)

And here's how to change the 'description':
[http://askubuntu.com/questions/136232/default-user-id-at-login-different-from-user-name-in-terminal-shell/143872#143872](http://askubuntu.com/questions/136232/default-user-id-at-login-different-from-user-name-in-terminal-shell/143872#143872)

---

