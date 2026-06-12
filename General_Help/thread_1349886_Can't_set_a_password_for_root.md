---
title: "Can't set a password for root"
date: 2009-12-08
forum: General Help
---

### Post by Weballergy on 2009-12-08
Hi friends !

I've got a problem. Well, I recently installed the ubuntu 9.10, and I've got a problem setting a password for root.

I cannot log as root cause he don't have a pass. Well, I go to users and groups and I try to set a pass for root, click accept, but when I check the root user, the password aren't there, and I still cannot log in as root... 

What's the problem and how can I solve it ??

thanks !

---

### Post by Clancy_s on 2009-12-08
Ubuntu doesn't use a seperate root account as such, I guess they've disabled the password for root.

To do things as an administrator log in as the first user you created (or any other that has administrative privileges) and use 'sudo', either command line all the way or to open a gui of whatever with root priviledges (I use sudo nautilus a fair bit)

---

### Post by Joeb454 on 2009-12-08
Generally, running ```
gksu nautilus
``` to get a root file browser (or whatever app of your choosing), is all you need. If it's a command line app, you would just run sudo, i.e. ```
sudo ifup eth0
```

---

### Post by lisati on 2009-12-08
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SteveHillier on 2009-12-08
Whenever I have done this it has been simple enough.
Load the terminal.
Type in ```
sudo passwd root
```
Enter the password for the sudo user, then enter the password for root and confirm.

---

### Post by Weballergy on 2009-12-08
> **Joeb454 said:**
> Generally, running ```
gksu nautilus
``` to get a root file browser (or whatever app of your choosing), is all you need. If it's a command line app, you would just run sudo, i.e. ```
sudo ifup eth0
```

Joeb I did sudo ifup eth0, and Terminal says that root is ignored?? how can I revert that??
Now everytime I log as root says:

"To run a command as administrator (user "root"), use "sudo <command>" See "man sudo_root" for details.

How can I make this text don't appear next time??

---

