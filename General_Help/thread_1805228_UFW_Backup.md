---
title: "UFW Backup"
date: 2011-07-15
forum: General Help
---

### Post by Jonny87 on 2011-07-15
Is there a way to fully backup all ufw settings and rules so that it can be easily restored on a new install and have it work exactly the same?

---

### Post by kleverbear on 2011-09-04
Also interested in this...Bump!

---

### Post by Toz on 2011-09-04
The important files to backup would be:

- **/etc/default/ufw**
- the complete contents of **/etc/ufw** 
- **/lib/ufw/user.rules** and **/lib/ufw/user6.rules**

For reference and information on these configuration files, see the Advanced Functionality section of:
[https://wiki.ubuntu.com/UncomplicatedFirewall]("https://wiki.ubuntu.com/UncomplicatedFirewall") 

and from a terminal window:
```
man ufw-framework
```

---

### Post by kleverbear on 2011-09-21
@Toz Thank you, this will come in very handy.

---

