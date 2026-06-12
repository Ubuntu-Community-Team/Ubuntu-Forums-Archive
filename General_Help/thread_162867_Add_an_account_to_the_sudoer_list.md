---
title: "Add an account to the sudoer list?"
date: 2006-04-19
forum: General Help
---

### Post by darundal on 2006-04-19
Hi, I have been trying like crazy to add an account to the sudoers list. I looked through the man file, and that didn't help all that much...neither did a quick google or forum search. HELP!

---

### Post by gborzi on 2006-04-19
All users in the admin group are sudoers. So, user you want to have sudo capability needs to be added to that group, i.e. among the secondary groups of that user you have to add admin.

---

### Post by darundal on 2006-04-19
How do I do this from the terminal? I can't do this through the regular interface...

---

### Post by jrib on 2006-04-19
on your account that has sudo:

```
sudo adduser name_of_user admin
```

---

### Post by darundal on 2006-04-19
And if there is a root account, and a regular account (that does not have sudo capability) and one can't figure out how to get into the root account to change it?

---

### Post by gborzi on 2006-04-20
Start your ubuntu in recovery mode. In this way you will be logged in as root, without the need to type a password. If the recovery mode is not available, use a live distribution, mount the root partition and manually add the user you want in /etc/group in the line for the admin group, like this
```
admin:x:106:youruser,anotheruserifyouneedanother,whynot,etc
```
Note: the number 106 can be different on your computer.

Good Luck !

---

### Post by cwmccabe on 2006-04-25
**EDIT**: Ignore this, I didn't read #5 above until after I posted it.  (but I'll leave the info below in case it might help anyone)

[QUOTE=darundal]How do I do this from the terminal? I can't do this through the regular interface...[/QUOTE]

I'm assuming that you originally wanted to do it through a graphical interface.  If so, you can do this.  When logged in as a user with sudo privileges:

Go to System >> Administration >> Users and Groups.

Then:

(1) Click on the name of the user that you want to elevate.
(2) Click on the properties button to open a new settings window.
(3) In the new window, click on the User Priviledges tab.
(4) Check the box next to "Executing system administration tasks".

Click OK all the way out, and that user should now be able to sudo.

---

### Post by timoioi on 2006-08-28
Hey there.  I'm having the same authentication failure when attempting to su, however when I add my user account to sudo via 'sudo adduser <username> admin' it comes back saying that I'm already a member of 'admin.'  I just installed Ubuntu yesterday and I most definitely did not forget my password.   Any other tricks that I can try to get my user to be able to su?? 

thanks!

---

### Post by timoioi on 2006-08-28
nevermind, I just realized the issue.  I'm checking out Ubunto after using Slackware for a long time.  Just issuing 'su' seems to get the password error, so I could never issue 'vi xorg.conf' and save changes.  Instead under Ubuntu it seems I must do a 'sudo vi xorg.conf.'

---

### Post by watsoncj on 2007-05-16
yes and 'sudo -s' will give you the same behavior as 'su'

---

### Post by Randall311 on 2008-05-06
> **darundal said:**
> Hi, I have been trying like crazy to add an account to the sudoers list. I looked through the man file, and that didn't help all that much...neither did a quick google or forum search. HELP!

Log in with your user account (not as root) Where **useraccount** is the name of your user account you want to add to the sudoers list (the same account you logged in as). Fire up the trusty old command prompt and type:
```
[useraccount@ubuntu ~]# sudo
Password:
[root@ubuntu ~]# chmod +w /etc/sudoers
[root@ubuntu ~]# echo '**useraccount** ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
[root@ubuntu ~]# chmod -w /etc/sudoers
```Done!  Now your account should have sudo privlages.  Remove the NOPASSWD:ALL part if you want to have to put your password in when you 'sudo'.  (Good security practice anyway). Good luck!

---

