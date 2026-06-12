---
title: "required to change password immediately (root enforced)"
date: 2006-03-15
forum: General Help
---

### Post by tenev on 2006-03-15
I installed ubuntu5.05 on a powerpc and i am having trouble with the root priviliges. each time i try to go to different settings it asks for a root password and when i supply it it is not recognized.
every time i log in i am asked to change the unix password (the alert is: you are required the change your password immediately (root enforced).

i remember fixing this with a command in the past. it's a command that's recommended after fresh install. would someone help me out? i really need to set one password once so that i can get moving with my system.

thanks for your help!

---

### Post by JustRandomName on 2006-03-15
Have you tired:

```
sudo passwd
```

---

### Post by tenev on 2006-03-15
[QUOTE=JustRandomName]Have you tired:

```
sudo passwd
```[/QUOTE]

i did. the password is updated successfully but i still cannot get into my system tools, like for example, i want to get into Networking to change my network settings, and the password is not recognized.

---

### Post by njzillest on 2006-03-15
how many root accounts do you have set up?

i dont exacly understand you problem. is it that you have to re type your new password everytime you log in? or is your root password not detected when you want use a program that requires root acess?

---

### Post by tenev on 2006-03-15
[QUOTE=njzillest]how many root accounts do you have set up?

i dont exacly understand you problem. is it that you have to re type your new password everytime you log in? or is your root password not detected when you want use a program that requires root acess?[/QUOTE]

hi, it's both actually. i reset my password each time i log in (root enforced) and programs that require root access does not detect my password.

edit: only one root account.

---

### Post by engla on 2006-03-15
[QUOTE=tenev]hi, it's both actually. i reset my password each time i log in (root enforced) and programs that require root access does not detect my password.

edit: only one root account.[/QUOTE]
Do you know that ubuntu uses sudo by default (just like OSX, if you have used that)

So when the gui tools are asking for a password, it's the password of the admin user, the user you created at install.

---

### Post by tenev on 2006-03-15
hi engla, i have tried my admin password and have not had any luck... i might just reinstall the system...

---

### Post by JustRandomName on 2006-03-15
By default ubuntu creates a root account and a user account.

The root account has a random password that you do not know (and really should never have to). If you NEED to know this then do the command I mentioned earlier to reset it.

The user account has the password that you specify when you install Ubuntu.

In order to execute programs as root, you have sudo

So when you are trying to activate the network admin then the password it is asking for is the USER account one.

To demonstrate this try:

```
$ sudo network-admin
```

This should ask for a password. The password that it is asking for is the USER password. This gives your user root access for a limited amount of time, and then it expires.

If however you did this:
```
$ su
ENTER PASSWORD
# network-admin

```

The password you are asked for is the root one. And for the rest of the session (or at least until you type "exit") you will have root access. This is viewed as insecure because you could do some very silly things like this.

---

