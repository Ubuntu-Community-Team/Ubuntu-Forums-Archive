---
title: "sudo on read-only file system fails"
date: 2010-12-08
forum: General Help
---

### Post by jamesgauth on 2010-12-08
My Ubuntu machine has entered a read-only file system state. I'd like to try move some files with root permissions (e.g. mysql data) to an external mount before rebooting. Unfortunately, when I use sudo, it complains about the read-only file system and aborts. 

Any idea how to get around this?

Here's the kernel running:
myusername@myhost:~$ uname -a
Linux myhost 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

Here's what happens when you run sudo:
myusername@myhost:~$ sudo ls
[sudo] password for myusername:
mail: /tmp/mail.RsXXXX6hYU4p: Read-only file system
Aborted
myusername@myhost:~$

---

