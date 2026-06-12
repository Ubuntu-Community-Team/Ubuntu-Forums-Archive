---
title: "Modify user group settings"
date: 2011-10-13
forum: General Help
---

### Post by scweston on 2011-10-13
Dear all,

I've done a fresh install of the new 11.10 release and I have also installed virtualbox.

To enable to USB subsystem in virtualbox I need to add my user to the 'vboxusers' group. Unfortunately I can't find the settings to modify the user groups.

I go to System settings>User Accounts, but get a very basic GUI in which I can only really add or remove users. I can't seem to modify group settings!

Please help. How do I do this the unity way?  I used to be a gnome guy until 11.04, where I decided to go KDE because I just couldn't get on with Gnome Shell or Unity. This time I'm trying to get used to Unity, but I'm struggling to do basic things like this! I want to be a Unity fan, but it just doesn't seem to be working for me!

Is it going to be a command line solution only?  will take it for now if necessary.

Stephen

---

### Post by Toz on 2011-10-13
Well, the command line solution is to enter the following command at the prompt:
```
sudo usermod <userid> -a -G vboxusers
```
...where <userid> is your userid.

---

### Post by scweston on 2011-10-14
Thanks Toz

I appreciate your help and the command line worked perfectly. Is there a unity GUI way of doing this?

Thanks
Stephen

---

### Post by sisco311 on 2011-10-14
In users-admin (Users and Groups) there is a *manage groups* button.

---

### Post by Toz on 2011-10-14
To the OP, users-admin is part of the gnome-system-tools package that is not installed by default. You can find it in the Software Centre,

---

### Post by scweston on 2011-10-14
Found it and thanks again. It's being frustrating at the moment but I think I may get to like Unity.

Stephen

---

