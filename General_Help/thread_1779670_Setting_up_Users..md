---
title: "Setting up Users."
date: 2011-06-10
forum: General Help
---

### Post by ItsAsh on 2011-06-10
Good Evening.

I understand basic command line behaviour, however I am not really experienced with administration. I have a few problems and I was hoping I could get some advice.

I have got a new dedicated server online, and I have logged in as root. I now want to achieve the following; I have spent hours looking around the web, searching, trying to follow tutorials and i'm stuck. Below I will number instructions and preceed with commands i have executed, I will then elaborate accordingly.

1. I would like to create a group called "admin".
```
$ groupadd admin
```

2. I would like to create a user called "ash". 
```
$ useradd ash
$ passwd ash
```

3. I then would like to add ash into admin.
```
$ usermod -g admin ash
```

4. I would like the "admin" group to have sudo access.
```
EDITOR=vi visudo
```

i) %admin ALL=(ALL) ALL
ii) ash ALL=(ALL) ALL

**Question: How can i give accounts sudo access by GROUP without having to define accounts individually inside this file?**

-----------------------------------

5. When I create a new user, and login ssh via that user. the Tab key doesn't work (normally it predicts the file/dir).

**Question: How can I have the root styles/themes/settings as the default ones for all created accounts?**

6. The "ll" command doesn't work. I also have to "ls -la" where as  in root i simply run "ll".

**Question: How can i get this command to work?**

-----------------------------------

I want to disable root, and only have sudo/staff accounts. How can the above best be acheived?

Thanks!

---

### Post by sisco311 on 2011-06-10
2. Insead of useradd you should use adduser. See:
```
man adduser
```

3. The proper syntax is:
```
usermod -aG group1,group2(,and so on) user
```
or you could use **gpasswd** to add a user to a group:
```
gpasswd -a user group
```


> **ItsAsh said:**
> 
**Question: How can i give accounts sudo access by GROUP without having to define accounts individually inside this file?**


If you add **%admin ALL=(ALL) ALL** to the sudoers file, then any user who is member of the admin group will have full sudo rights.

> **ItsAsh said:**
> 
5. When I create a new user, and login ssh via that user. the Tab key doesn't work (normally it predicts the file/dir).

Change the user's default login shell to /bin/bash
```
chsh -s /bin/bash username
```

NOTE: adduser defaults to set the user's shell to bash.

> **ItsAsh said:**
> 
**Question: How can I have the root styles/themes/settings as the default ones for all created accounts?**


Use adduser instead of useradd.

> **ItsAsh said:**
> 
6. The "ll" command doesn't work. I also have to "ls -la" where as  in root i simply run "ll".

**Question: How can i get this command to work?**


Copy the files from /etc/skell to the user's home and change the user's shell to bash.

NOTE: adduser does this by default.

> **ItsAsh said:**
> I want to disable root, and only have sudo/staff accounts. How can the above best be acheived?


If you are 100% sure that at least one user has full sudo rights, then you can disable the root account password with:
```
sudo passwd -dl root
```
If you want to re-enable the account simply set up a new root password.

See: [uhelp]community/RootSudo[/uhelp]

HTH

---

### Post by ItsAsh on 2011-06-11
Hi sisco311,

Thank you for your response. Everything appears clear why I have had problems. This response is very helpful!

---

