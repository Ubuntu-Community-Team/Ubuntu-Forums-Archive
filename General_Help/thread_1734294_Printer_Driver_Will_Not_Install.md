---
title: "Printer Driver Will Not Install"
date: 2011-04-20
forum: General Help
---

### Post by wraithofhate on 2011-04-20
Hello everyone,

I am currently using ubuntu 10.10 and trying to install the current driver for a lexmark x2600 printer. 
I retrieved the driver from the lexmark site, to be specific the debian version.
Once I had the driver unzipped I was able to run the program to start installing it.
However the problem is that it requires root privileges in order to install. 
So I input my admin password to allow the install.
Apparently the password I use is not correct even though it is the admin/root password on my system.
Any ideas on what I may be doing wrong?

Thank you all!

---

### Post by spikoley on 2011-04-20
Do you have multiple accounts on that computer?  The first account will have admin rights.  If your user isn't an admin user then you can add it by going to System> Administration> Users and Groups> Manage Groups> select Admin and click on properties.  Do this from the account created during the install.  Then you can install software from your current user.

---

### Post by wraithofhate on 2011-04-20
Alright looked into what you said and this account is already an admin level account.
It is also the only account on the system.
I even tried making this account root using the same method but that failed as well still saying that the admin password is incorrect.

---

### Post by spikoley on 2011-04-20
It sounds like you are probably typing in the wrong password.  Use the same password you log in with.  

Don't mess with the root account.  Just use your admin account.

---

### Post by sisco311 on 2011-04-20
You have to run the installer as root. Open a terminal (Applications -> Acccessories -> Terminal), type:
```
gksu
```
then a space. Drag the .deb file in the terminal window and hit enter.

---

