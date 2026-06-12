---
title: "creating a new user account in ubuntu 9.10"
date: 2010-02-03
forum: General Help
---

### Post by computerguts on 2010-02-03
I recently created a new user account in ubuntu linux, and created a file called xsession so that I can boot directly into xmbc when I log into that account. Is there anyway to delete the home folder for that account. I can view the file but when I try to delete it is says I do not have apporite permisions to delete the file. Please help 

I removed the account and deleted the group but it still shows up when I type in the address /home/xmbc
Is there anyway I can delete this file. It also will not let me create any new user accounts is there any way I can fix these prolbems without totaly reinstalling the system.

---

### Post by t4thfavor on 2010-02-03
You need to have root priveliges when creating users, or deleting folders that do not belong to you.

Doing it from the commandline you would need to prefix your command with sudo.

or click the unlock button at the bottom of most of the gui applications.


you can launch an application as root by pressing Alt+F2 then typing gksu appname


Hope this helps.

---

### Post by warfacegod on 2010-02-03
```
gksudo nautilus
```

---

