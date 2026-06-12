---
title: "why cant i change my password?"
date: 2012-01-08
forum: General Help
---

### Post by ugotboxed on 2012-01-08
i tried to turn my password off, and i thought that i didn't have a password any more and when i have to authenticate myself i needed a password. i then tried nothing and my old password. what do i do?

---

### Post by bluexrider on 2012-01-08
follow this tutorial [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Buntumatic on 2012-01-08
There are two different things, an account without password and **automatic login**. In latter case the password still exists, and **that's the way you should go in Ubuntu**.
Because, if you succeeded with passwordless account then all root/sudo access would be passwordless, too. And this is The Very Bad Thing, practically trashing all security of your operating system.

---

### Post by ugotboxed on 2012-01-08
this didnt work, any other ideas?

---

### Post by Buntumatic on 2012-01-08
There is a number of ways, booting up in single user mode is probably the easiest. At Grub screen, pass init=/bin/bash to your kernel. When it boots up you will be logged in as root, no password asked. Just set your user password and reboot.

---

