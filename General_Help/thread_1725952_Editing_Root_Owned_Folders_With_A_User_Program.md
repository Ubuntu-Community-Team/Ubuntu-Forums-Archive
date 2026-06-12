---
title: "Editing Root Owned Folders With A User Program"
date: 2011-04-10
forum: General Help
---

### Post by micha8l on 2011-04-10
Hello,

I'm using the IDE Netbeans (text editor) on my /home/michael Ubuntu account. I'm trying to open a file with Netbeans that's owned by root, I can't do this as I expected. So is there a way to run NetBeans as root, or is there a way to give netbeans permission to open/save files owned by root. 

Appreciate any help,
Mike

---

### Post by Vaphell on 2011-04-10
is there any reason for why there is a root owned piece of code? Root is for administration tasks, not for programming.
you should change files ownership to normal user with chown
```
sudo chown user:group file(s)
```

to run with admin privileges in general, use sudo <cmd> for cli programs, gksu <cmd> for gui ones.

---

