---
title: "superuser?"
date: 2009-07-27
forum: General Help
---

### Post by pmooney78 on 2009-07-27
What's the difference between using sudo and su to become the root user? (And, equivalently, between gksudo and gksu?)

---

### Post by credobyte on 2009-07-27
*sudo* uses *sudoers file*, *su* uses *root account* and it's password.

---

### Post by SuperSonic4 on 2009-07-27
sudo references the sudoers file to check if you're in the right group. It means you can put in your user password. Ubuntu and it's derivates use sudo so the root account can be disabled

su gives you direct access to the root account. While it's less troublesome for an admin to be root it's less secure. To access it you need root's password

More Info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pmooney78 on 2009-07-27
Gotcha ... thanks!

---

### Post by ajgreeny on 2009-07-27
And just to confuse even further you can use ```
sudo su
``` to get you a root terminal ie. root@hostname but still working in your own home folder, and you can also use ```
sudo -i
``` which gives you root@hostname, but this time in root's home folder.  Try them out to see the difference if you can't see what I mean.

---

