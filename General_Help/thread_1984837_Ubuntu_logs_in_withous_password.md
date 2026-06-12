---
title: "Ubuntu logs in withous password"
date: 2012-05-22
forum: General Help
---

### Post by SeLL on 2012-05-22
I was playing around with "User accounts" and I clicked in "change password" and selected "login without password" so the system logs in automatically. Now I want to undo it but I can't. On the login screen there's a button like Guest's account. There is no asking for password while logging in. As a side effect, it asks me separately for keyring password.
How to disable auto login and make login/keyring password unified again like before?

---

### Post by SeLL on 2012-05-22
It was solved on Brazilian forum: [URL="http://ubuntuforum-br.org/index.php/topic,95951.msg527443.html#msg527443"]http://ubuntuforum-br.org/index.php/topic,95951.msg527443.html#msg527443
[/URL][ ]("http://ubuntuforum-br.org/index.php/topic,95951.msg527443.html#msg527443")
For those who can't understand portuguese, the solution is:
> sudo gpasswd -d USER nopasswdlogin

where you should change "USER" to your user name.

---

