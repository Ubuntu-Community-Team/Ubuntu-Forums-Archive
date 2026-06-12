---
title: "Accidently deleted home folder . Cannot login"
date: 2009-09-23
forum: General Help
---

### Post by praveesh on 2009-09-23
I accidently deleted the directory /home/myname . Now , when I log in using GDM , It replies that my home directory is missing and if I want to log in with / as home directory . When I answer yes, it shows some error messages (screensaves could not be initiated, nautilus could not be opened etc ). After that, the Gnome desktop is displayed without any panels. So no application menu . Nothing could be done . No applications can be opened. Alt+f2 doesn't work. So it's not possible to create another user(I thing if I create a new user account, the problem will be rectified) . Please help . I am having Gnome and kde4.3 . KDM and GDM are installed GDM is the default display manager.

---

### Post by scheuri on 2009-09-23
Hi there

Probably the easiest way is using ctrl-alt-F1 to change to the console (CLI).
You will be greeted by white letters and a black background.

You might be able to log in now, but I stress you do not alter anything...only making a new user (or making a new home directory).

To make a new user, you need to do following command
sudo adduser [username]
You will be asked your passwort, then it will make the user and ask what password you want for that new user.

Should all be done now, either press ctrl-alt-F7 to return do GDM or reboot.

hope that helped.
cheers
scheuri

---

### Post by scragar on 2009-09-23
ctrl+alt+F1 = terminal, log in
```
sudo useradd -m **tmp**
sudo cp -rf /home/tmp "/home/$USER"
sudo chown -r $USER: "/home/$USER"
```
Restart and it should all work fine.

---

### Post by lightstream on 2009-09-23
The above two suggestions will create a new user for you. You just want to restore your existing user's ability to log in.

Ctrl-Alt-F1, log in, then type:

```
sudo mkdir /home/EXISTINGUSERNAME
sudo chown EXISTINGUSERNAME:EXISTINGUSERNAME /home/EXISTINGUSERNAME
```

Obviously you'll have no subfolders or files in the new home directory, so you will not have any settings for your programs, including Gnome and compiz. However those programs should create settings files when needed, thus allowing you to save your preferences from then on.

---

### Post by scragar on 2009-09-23
> **lightstream said:**
> The above two suggestions will create a new user for you. You just want to restore your existing user's ability to log in.

Ctrl-Alt-F1, log in, then type:

```
sudo mkdir /home/EXISTINGUSERNAME
sudo chown EXISTINGUSERNAME:EXISTINGUSERNAME /home/EXISTINGUSERNAME
```

Obviously you'll have no subfolders or files in the new home directory, so you will not have any settings for your programs, including Gnome and compiz. However those programs should create settings files when needed, thus allowing you to save your preferences from then on.

$USER

is always your username, so just run:```
sudo mkdir /home/$USER
sudo chown $USER: /home/$USER
```Oh, and "bob:" in chown is the same as "bob:bob" it's just easier to type :p

---

### Post by sisco311 on 2009-09-23
> **scragar said:**
> ```
sudo mkdir /home/$USER
sudo chown $USER: /home/$USER
```
+1

The /etc/skel directory contains files and directories that are automatically copied over to a new user's home directory when such user is created by the useradd program.

```

cp /etc/skel/* /home/$USER
cp /etc/skel/.[a-zA-Z0-9]* /home/$USER
```

---

### Post by praveesh on 2009-09-23
> **lightstream said:**
> The above two suggestions will create a new user for you. You just want to restore your existing user's ability to log in.

Ctrl-Alt-F1, log in, then type:

```
sudo mkdir /home/EXISTINGUSERNAME
sudo chown EXISTINGUSERNAME:EXISTINGUSERNAME /home/EXISTINGUSERNAME
```

Obviously you'll have no subfolders or files in the new home directory, so you will not have any settings for your programs, including Gnome and compiz. However those programs should create settings files when needed, thus allowing you to save your preferences from then on.

the problem is rectified. Thanks for all . I would like to know what a chown command do. Can anyone please explain. More over, the command adduser create only a normal user account . Any way to create an administrator account?. I used --system option for that . But it created the account without setting a password.

---

### Post by sisco311 on 2009-09-23
> **praveesh said:**
> Any way to create an administrator account?.

Add the user to the admin group:
```
sudo gpasswd -a username admin
```
or
```
sudo adduser username admin
```

> **praveesh said:**
> I would like to know what a chown command do. Can anyone please explain.

You need to create the new directory as root(**sudo** mkdir ...), hence it's owned by root. You can change the owner/group of a file/directory with the chown/chgrp command.

Please read:
[https://help.ubuntu.com/community/FilePermissions#Changing the File Owner and Group]("https://help.ubuntu.com/community/FilePermissions#Changing the File Owner and Group")

---

### Post by scragar on 2009-09-23
> **sisco311 said:**
> Add the user to the admin group:
```
sudo gpasswd -a username admin
```
or
```
sudo adduser username admin
```

Can I add that it's often a good idea to call using **-m** unless you've got a reason to do otherwise, since -m says to always create the home directory, and it's very rare you'll have a reason not to.

---

### Post by praveesh on 2009-09-23
Thanks for all

---

### Post by sisco311 on 2009-09-23
> **scragar said:**
> Can I add that it's often a good idea to call using **-m** unless you've got a reason to do otherwise, since -m says to always create the home directory, and it's very rare you'll have a reason not to.

*adduser user group* adds an existing user to an existing group
if the group or user doesn't exist it throws an error.

-m is flag for useradd. adduser and addgroup are frontends for the low level tools like useradd, groupadd and usermod.

---

### Post by scragar on 2009-09-23
> **sisco311 said:**
> *adduser user group* adds an existing user to an existing group
if the group or user doesn't exist it throws an error.

-m is flag for useradd. adduser and addgroup are frontends for the low level tools like useradd, groupadd and usermod.

Sorry, you can understand where my confusion came from though, right? adduser and useradd? I can't have been the first person to make that mistake.

---

### Post by sisco311 on 2009-09-23
> **scragar said:**
> Sorry, you can understand where my confusion came from though, right? adduser and useradd? I can't have been the first person to make that mistake.

:)

don't worry, it happens to me too. i always have to read the man page.

---

