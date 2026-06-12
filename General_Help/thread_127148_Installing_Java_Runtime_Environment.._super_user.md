---
title: "Installing Java Runtime Environment.. super user?"
date: 2006-02-08
forum: General Help
---

### Post by KevNice on 2006-02-08
I downloaded and installed the Java runtime environment.. but when I went to do the dpkg command, I got this:

kevin@softbank:~$ dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb
dpkg: requested operation requires superuser privilege

What's "superuser privilege"? i dont understand, I am the only user on this computer and im under the administrator.

---

### Post by PaulMellors on 2006-02-08
hi you need to sudo the command, so type this

sudo dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

---

### Post by lamego on 2006-02-08
Unlike at windows you are not administrator, wenever you need to run a superuser command you will need sudo .
Other superuser gui applications will ask you for the root password.

---

### Post by KevNice on 2006-02-08
oooh, oops, I forgot the sudo. theres a typo in the guide then, I got it now, thanks!

---

