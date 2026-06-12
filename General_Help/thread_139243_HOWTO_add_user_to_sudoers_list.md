---
title: "HOWTO add user to sudoers list"
date: 2006-03-03
forum: General Help
---

### Post by songo on 2006-03-03
hello..

i've made 3 kubuntu installation on 3 different PC. on the last one somehow the only user (myself) is enable to become root. only through 'su'. 
it goes like this (the password entered is correct and the same for 'su'):

```

songo@barra98:~$ sudo bash
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
songo@barra98:~$ su
Password:
root@barra98:/home/songo # sudo bash
root@barra98:/home/songo # 
```

more... if i enter songo's password to sudo bash i get this:
```

songo@barra98:~$ sudo bash
Password:
songo is not in the sudoers file.  This incident will be reported.

```

what's the difference between su and sudo bash anyways?
tanx

---

### Post by aysiu on 2006-03-03
When you create the user, there are permissions the user has (go to System > Administration > Users and Groups). Make sure the new users have the same permissions as the first user you created.

---

### Post by newuser111 on 2006-03-03
use visudo

---

### Post by climbjm on 2007-10-05
So when you launch visudo, what do you do next?  
What are you supposed to add? 
Just the username?

---

### Post by Discov3ry on 2007-10-05
#visudo
-put this line at the end (replace username with your username):
username ALL=(ALL) ALL
-hit ESC
-SHIFT+:
-type wq
-hit enter

---

### Post by climbjm on 2007-10-05
Awesome, thank you!
And also, thank you for the vi commands too... *(phew).*

---

### Post by anaconda on 2007-10-05
hmm.. I think using visudo for adding user to admin group is a bit difficult.

how about just:
sudo adduser existing_username_to_add_to_admin_group admin

And atleast in my feisty installation visudo actually opens nano... not vi

---

### Post by aysiu on 2007-10-05
As far as I know, this can be done properly through the GUI (graphical user interface) by pointing and clicking in both Kubuntu and Ubuntu.

I don't see any reason (unless you want to just learn how to do it for fun) to manually edit the /etc/sudoers file.

In Ubuntu, it's System > Administration > Users and Groups. I don't remember what it is for Kubuntu.

---

