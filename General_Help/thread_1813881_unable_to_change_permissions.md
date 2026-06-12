---
title: "unable to change permissions"
date: 2011-07-28
forum: General Help
---

### Post by paras_saini on 2011-07-28
Hi,
Recently I installed ubuntu 10 on my machine. Installed using windows installer and it is installed in one of the windows drive. It didnt asked me for root password, so i used sudo -i to become a root user.

now when i was trying to execute a file named all.bash ([http://golang.org/doc/install.html](http://golang.org/doc/install.html)) using ./all.bash but it says permission denied error.
I saw that the file have only read and write permission. I tried to change the permission by using chmod u+rx all.bash but it does nothing. Is there any way to change the permissions.

---

### Post by cjack2964 on 2011-07-28
Have you tried changing the ownership first?

 "chown <username> <file>"

---

### Post by IWantFroyo on 2011-07-28
I don't know about chmod u+rx, but just a 'chmod +x' or a 'chmod 777' does it for me.

---

