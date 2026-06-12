---
title: "How to create new Administator account"
date: 2010-03-30
forum: General Help
---

### Post by Aaron Durant on 2010-03-30
Hello all,

Whilst playing around with my computer the other day i accidentally set the workspace feature to have 36 workspaces. This subsequently caused my computer to run very slowly and both panels and the bar at the top of the windows (with the close and minimise things) to dissapear. This means that i can no longer open programs easily (i have to open a folder from the desktop and then navigate to filesystem/usr/shared/aplications and then open them from there and only a few have full functionality. They also run very slowly. I have been looking for options to change it back but cannot. I have managed to use terminal to create a new working account although it is not an administrator account which i need it to be.
Please could someone tell me how to do one of the following:
A) Fix the first account (restore it to working order)
B) Make the new account an administrator in terminal (I have tried to using users and groups but it freezes)
C) Create a new administrator account in terminal

Thanx

Aaron

---

### Post by Directive 4 on 2010-03-30
you could try to right click in the bottom right (over the 36 boxes)

select preferences and adjust.

---

### Post by sisco311 on 2010-03-30
A) ```
gconftool-2 --type int --set /apps/metacity/general/num_workspaces 2
```

B) ```
sudo gpasswd -a **username** admin
```
where **username** is the login name of the user.

---

### Post by Aaron Durant on 2010-03-30
Directive 4: Thanx but i had alreay said that both panels had dissapeared and so i can not do this 
Sisco311: thanx, The first bit of code worked. Do i have to start my PC for the second one to take effect?

Thanx

Aaron

---

### Post by sisco311 on 2010-03-30
> **Aaron Durant said:**
>  
Sisco311: thanx, The first bit of code worked. Do i have to start my PC for the second one to take effect?


Nope, just log out the user (if it's logged in) and log it (back) in.

---

### Post by Aaron Durant on 2010-03-30
I have logged out and in again but when i try to open users and groups it says:
> You are not allowed to access the system configuration
This suggests that it is not a full administrator... which is a problem as i wanted to delete the first account seeing as i still have some seemingly unfixable problems with it and keep my second account as administrator (partly because it works and partly because it looks nices as it is setup as a 10.04 account). Is there an easy way to do this


Thanx

Aaron

---

### Post by NovaWasp on 2010-03-30
```
sudo useradd -G admin {your user name}
```
 
that should do it.

---

### Post by Aaron Durant on 2010-03-30
> **NovaWasp said:**
> ```
sudo useradd -G admin {your user name}
```that should do it.

Does that create a new admin user or make the one i already have admin?

Thanx

---

### Post by sisco311 on 2010-03-30
> **Aaron Durant said:**
> Does that create a new admin user or make the one i already have admin?

Thanx

It creates a new admin user.

But adding the user to the admin group should do the trick.

What's the output of:
```
id **newuser**
```and
```
sudo cat /etc/sudoers
```

---

### Post by Aaron Durant on 2010-03-30
> **sisco311 said:**
> It creates a new admin user.

But adding the user to the admin group should do the trick.

What's the output of:
```
id **newuser**
```and
```
sudo cat /etc/sudoers
```

I cannot run terminal because i get the same error as when i try to open users and groups... Should i create a new account using the code above and try it then?

---

### Post by estyles on 2010-03-30
Assuming your old user still exists, login as the new user and in terminal do: ```
su {old user name}
```

After you enter your {old user name}'s password, you will be logged in as your old user and can do the sudo commands listed in this thread.

---

### Post by Aaron Durant on 2010-03-30
I cant access terminal in the new user...

---

### Post by estyles on 2010-03-30
Then you have much bigger problems.  If you can boot into recovery mode, you should be able to add a new user and add them to the admin group.  If the new user can't open a terminal, then simply adding him to the admin group is unlikely to fix whatever issues you have.

---

### Post by Aaron Durant on 2010-03-31
I have now managed to resore my orignal account to a mostly working state. I am now trying to create a new administrator user to switch to. Whenever i do this using the users and groups application it seems to create the account and i can set it to administrator, but when i try to log in, it tells me that the password i entered is incorrect. I have tried creating many different users and passwords, all with the same problem. i have also changed the password for one on the working user but i still get the same thing. I have logged in by using the setting that says do not ask for password at loggin, but then i cannot administer anything. 

Any suggestions?

Thanx

Aaron

---

