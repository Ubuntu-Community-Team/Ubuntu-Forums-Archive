---
title: "beginner questions"
date: 2006-05-09
forum: General Help
---

### Post by zero76 on 2006-05-09
just installed ubuntu 5.1 , after setup it displays a startup window for the login and password.the problem is that any password i use says it is invalid so i can't log to use my computer.what can i do or which command to use so as to fix it , please be patient with me its my1st time with ubuntu..
thanks anyway

---

### Post by johnc4510 on 2006-05-09
Are you using the user name and password you imput during the install?

---

### Post by zero76 on 2006-05-09
yes i did .a friend just told me to use root as login.correct?

---

### Post by Al3xanR0 on 2006-05-09
[QUOTE=zero76]yes i did .a friend just told me to use root as login.correct?[/QUOTE]

What ever the passwd is for the userid you created (not the root) is the one that you want to use to login. Logging in as root is highly UNreccommended.

---

### Post by kbudurka on 2006-05-09
logging in as root is not an option after a fresh ubuntu install.
root has no "password", hence it can not login.

login as your username, then in a terminal window type sudo su -
this will prompt you for a password, type your USERS password, not roots, and you will change into root.

This is good practice because root can never login - you need to login as a valid user first, and one that has sudo access too.

---

