---
title: "Super User Password - reset !!"
date: 2010-08-23
forum: General Help
---

### Post by merin_83 on 2010-08-23
Hi ,, I just installled the Ubuntu 9.1 In the terminal window when i try to use the SU - Super User, authentication failed message is coming up. I used my root password. But its not successful. Other places where it prompts the authentication, i use the same password and it is successful. Only in SU am having this issue. Please help !!!!:confused:

Thank you,
merin.

---

### Post by kerry_s on 2010-08-23
use "sudo su", ubuntu is a sudo os.

---

### Post by sidzen on 2010-08-23
Did you try, at the terminal, [PHP]sudo passwd root[/PHP] then following instructions?
I think ubuntu people do not want a user to employ the "su" command, but you may wish to try 
[PHP]su -l[/PHP] command to satisfy your curiosity.

---

### Post by kerry_s on 2010-08-24
you should not tell someone to activate root, you cut there security in half, an attacker now only has to crack the password. using sudo, they have to guess the user name & password.

---

