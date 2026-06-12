---
title: "problems with login"
date: 2006-03-25
forum: General Help
---

### Post by dragoshte on 2006-03-25
hello!
I have Ubuntu 5.10...so I have a problem with login as root: i cannot login as root just like normal user without the rights of root...but if i want tu login in terminal as root is working!
Can someone explain me what to do?

Thank U!:-k

---

### Post by ComplexNumber on 2006-03-25
its ok, there's absolutely nothing to worry about because everything is normal. thats the way its meant to be in ubuntu. you're not meant to be able to login as root via the login screen..the philosphy being to minimise the risk to the system.

---

### Post by trent dillman on 2006-03-25
But...if you absolutely need a root terminal, try

```
sudo -s
```

This gives you a root shell.

---

### Post by dragoshte on 2006-03-25
thank you 4information!!!

Ubuntu rullzzz!!:KS

---

### Post by chocolatetoothpaste on 2006-03-26
If you want to login in from the GDM, first you should set a root password via the command line.  Then go to System->Administration->Login Screen Setup.  Click the Security tab, and check the box that says "allow root to login with GDM".  If you do remote logins, check that one too.

Edit:
To set root password, type ```

sudo passwd root

```
Enter your password to allow a sudo command, then enter the new root password.

---

