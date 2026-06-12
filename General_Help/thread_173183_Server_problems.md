---
title: "Server problems"
date: 2006-05-09
forum: General Help
---

### Post by shugie on 2006-05-09
I installed vsftpd to run a little filesharing server between my friends. Everything works beautifully as long as ftp is used. I decided to try using putty to login to the server. I decided to try to login with putty. Using putty and SSH I noticed I have a SSH server open. I don't know what it is or how to turn it off. So, how do I find what is listening to port 22, and then either configure it better or turn it off.

---

### Post by GNUrag on 2006-05-10
hi shugie, Probably your server has ssh daemon running..
You can run **/etc/init.d/ssh stop**  to stop ssh daemon on your server

Or you can permanently stop ssh daemon from autostarting by giving this:
**$ sudo update-rc.d -f ssh remove**

---

### Post by shugie on 2006-05-10
thank you

---

