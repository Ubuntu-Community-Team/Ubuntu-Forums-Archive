---
title: "Missing in Unity"
date: 2011-11-03
forum: General Help
---

### Post by asus701user on 2011-11-03
Where can I find Users and Groups in Unity? It used to be in System - Administration?

---

### Post by gandaran on 2011-11-03
system settings.

---

### Post by asus701user on 2011-11-03
I have checked there but no luck - there is an option called User Accounts but it does not show what was in Users and Groups. In particular there used to be the options Manage Groups and Advanced Settings. I would like to check/change whether user(s) are a member of sambashares. (My 11.10 machine won't share/connect to folders on my other 10.10 machine.)

---

### Post by mjuhasz on 2011-11-03
I did not find it anywhere either. For the time being you can use commandline, e.g. to add an existing 'joe' user to an existing 'vboxsf' group type:

```
usermod -a -G vboxsf joe
```

---

### Post by gwm on 2011-11-03
Me too. I need it for virtualbox USB access. The error message says to add myself to the vboxusers group.
I tried the command line suggested and this was the result.
```
usermod -a -G vboxusers gwm
usermod: cannot lock /etc/passwd; try again later.
```
I only have FireFox and the Terminal window open.
????
Update: I thought to try 
```
sudo usermod -a -G vboxusers gwm
```
This seemed to work. (I don't know how to check the groups and there memberships.)
Anyway,I rebooted and now I can use USB. So, I suppose I have been added to this group.

---

### Post by gordintoronto on 2011-11-03
cat /etc/group

will list the groups and users.

---

### Post by roger_1960 on 2011-11-04
Hi

I have the same problem, its missing from system settings, but the GUI does appear if you search for "users" in the dash - strange, I thought I was in system settings a few days ago...

---

### Post by asus701user on 2011-11-04
I think I have found (via another member) the solution to this.

You have to install gnome-system-tools e.g. via Ubuntu Software Centre. It seems this is not installed in a standard installation, although it was in 10.04 I think.

It then shows up in Dash as Users and Groups separately from Users.

Also you can then can see a user's group membership from the terminal with the following command.
 ```
groups user 

```Regards

---

### Post by calydon on 2012-06-19
Thanks for the information in this post. It was very helpful.

 I don't mean to be a troll, especially since I'm new to the forums, but why do things like this regularly happen with Linux distros? This change was disruptive and annoying, and hard to figure out. 

These types of annoying 'gotchas' are the main reason that Linux/Ubuntu does not gain widespread acceptance among less technical users.

---

