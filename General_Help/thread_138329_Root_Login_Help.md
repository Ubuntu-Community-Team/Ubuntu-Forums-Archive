---
title: "Root Login Help"
date: 2006-03-01
forum: General Help
---

### Post by drir1990 on 2006-03-01
I do not know what my root password is, While i was trying to install Opera it asked me for my root login, I am new to Linux and first of all i do not know exactly what it was. Second I do not know what my root login is. I have tried my password and several other things like 'admin' and 'default' but i can not get it logged in. Is there anything i can do to find out what my root login is or will i never be able to install new programs into linux?

---

### Post by Ramses de Norre on 2006-03-01
How did you install it? When you're using dpkg or apt-get you just need to put sudo in front of them and give your normal user passwd.

---

### Post by glug101 on 2006-03-01
Ubuntu doesn't create a root login by default.  Everything is done using the sudo command.  If you would like a root passwd (as I do) type in the following:

```
sudo su
passwd
```

and then follow the prompts to set the passwd. 

Hope this helps :)

---

### Post by drir1990 on 2006-03-01
I'm using kpackage

---

### Post by glug101 on 2006-03-01
lol, Ramses, you beat me to the punch again :)

You might have a better solution too..

---

### Post by drir1990 on 2006-03-01
i have tried all of these solutions and i get this message everytime in kpackage, 
Password: 
su: Authentication failure
Sorry.

---

### Post by drir1990 on 2006-03-01
I got it to work, Thanks everyone!

---

### Post by Ramses de Norre on 2006-03-01
Can you use sudo with other commands in terminal?
Are you using kpackage under gnome?

---

