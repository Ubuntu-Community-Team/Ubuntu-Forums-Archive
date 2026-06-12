---
title: "Problem with sudo &amp; root login"
date: 2009-10-21
forum: General Help
---

### Post by Engec on 2009-10-21
Hi. Somehow i can't use sudo with my admin user account I created with setup of Ubuntu server. I never gave root a password. I used to be able to use sudo with my admin user accout I created with setup, but now suddenly i can't. It tells me: "access denied: not in the sudoers file" I can't even vi into the sudoers file. I can't use root, cause no password there. I can't give root a password, cause i can't sudo and visudo and su -s root or passwd root doesn't work.
 
Please help, this prevents me from being able to change anything mostly.
I use this as a samba file server and I'm about 2 month's new to Ubuntu server.
 
Thanks - Ubuntu Server -noob

---

### Post by sisco311 on 2009-10-21
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by nothingspecial on 2009-10-21
Press escape at grub and enter recovery mode/root shell

Type ```
adduser username admin
```

Then log in as that username.

---

### Post by Engec on 2009-10-21
Thanks, It worked

---

### Post by nothingspecial on 2009-10-21
> **Engec said:**
> Thanks, It worked

Linux tends to. It`s the fact that it does without asking you weather you`re sure that creates the problems.

---

