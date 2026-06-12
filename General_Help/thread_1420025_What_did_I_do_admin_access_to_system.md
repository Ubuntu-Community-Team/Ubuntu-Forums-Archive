---
title: "What did I do?? admin access to system"
date: 2010-03-02
forum: General Help
---

### Post by dmzx on 2010-03-02
While messing around with file permissions and ownership of /var/www/ i seem to have locked myself out of being able to administer users on my 9.10 system. 

when I go to the user administration screen in the icon with the keys is grayed out. with the message "not authorized to make changes". My account seems to have lost admin access. But, I'm the only user on the system. 

I presumed I somehow changed my group status from the root group to something else

but, sudo usermod -g root [my name] just returns "no changes made"

Anyone have any smart ideas? All I can do for now is run as the su from the terminal. Is it possible to log into gnome with a root account?

ugh

---

### Post by sisco311 on 2010-03-02
Hi and welcome to the forums!

Boot in the *Recovery Mode* & add your user to the *admin* group:
[http://www.psychocats.net/ubuntu//fixsudo](http://www.psychocats.net/ubuntu//fixsudo)

Next time use the -a option to add the user to _the supplementary group(s)_:
```
usermod -aG group user
```
or the gpasswd command:
```
gpasswd -a user group
```
or (on a debian based system)
```
adduser user group
```

---

### Post by dmzx on 2010-03-02
Thanks, one of those commands works.

edit: dumbness

---

