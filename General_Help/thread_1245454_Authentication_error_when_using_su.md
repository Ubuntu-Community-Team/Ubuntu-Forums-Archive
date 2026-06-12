---
title: "Authentication error when using su"
date: 2009-08-20
forum: General Help
---

### Post by masoud23 on 2009-08-20
Hello

I get  Authentication error when using su. my password is right and works with other commands. I have only one password in my ubuntu. 

masoud@masoud-desktop:~$ su
Password: 
su: Authentication error

---

### Post by michy99 on 2009-08-20
In Ubuntu, you use sudo to give yourself root permissions. Read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to switch to root in a terminal, use```
sudo -i
```

---

### Post by Immolatus on 2009-08-20
Ubuntu generally uses "sudo" as opposed to "su", unless of course you set up a "real" root user. Is this what you have done??? If not, use "sudo" as you said you set up only one password. So, "sudo" and your regular user password should work.

---

### Post by t0p on 2009-08-20
When you run su like that, ubuntu asks for the root password.  But you haven't set a root password.  So when you type in your user password, it comes back as wrong.

As everyone else said: use sudo.

---

