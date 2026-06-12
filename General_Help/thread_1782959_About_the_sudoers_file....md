---
title: "About the sudoers file..."
date: 2011-06-15
forum: General Help
---

### Post by Krauser Joestar on 2011-06-15
hey there everyone


I'm trying to give limited permissions to a user on my local pc, and i want him to be able to use sudo commands but not access to other people files and permissions.(i.e, i want him to be able to restart the pc).


If you guys could answer this in a straight and simple way i would appreciate.

thanks in advance.

---

### Post by grahammechanical on 2011-06-15
Have you examined the Users and Groups utility? It might be helpful if you told us what sudo commands you want this user to be able to use. Any user can restart the computer and log in using their log in password.  A user does not need to be Administrator to do that. Ubuntu lets you switch users as well. If you want other users to have Internet access without you needing to be sudo to authenticate the action, you can set WiFi up to connect automatically and to be available to all users. You can set users up to have a custom account and not just either administrator or user.

Regards.

---

### Post by Krauser Joestar on 2011-06-15
> **grahammechanical said:**
> Have you examined the Users and Groups utility? It might be helpful if you told us what sudo commands you want this user to be able to use. **Any user can restart the computer** and log in using their log in password.  A user does not need to be Administrator to do that. Ubuntu lets you switch users as well. If you want other users to have Internet access without you needing to be sudo to authenticate the action, you can set WiFi up to connect automatically and to be available to all users. You can set users up to have a custom account and not just either administrator or user.

Regards.


No, they can't, at least with my current settings. It always ask for the admin password.


I know how to give users sudo powers, that's easy but i don't want them to sudo bash, etc, only to be able to restart and turn off the machine.

---

### Post by ruffEdgz on 2011-06-15
I think you will have to look for two things when it comes to managing your system:

[LIST]
[*]Setting up sudoers for command restrictions
[*]Placing acls on your file system for permission control
[/LIST]

Lets start with the sudoers.
The /etc/sudoers will be able to help control users or groups with which commands they can have temporary root access. For example, if you want John to be able to run the shutdown command only using the sudo, placing this line in the /etc/sudoers file will complete that:
```
john  ALL = (ALL) /sbin/shutdown -h now
```
This will allow the user 'john' to use the command 'shutdown -h now' only. To read more about sudoers, visit this wiki page here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

As for the permissions to access certain users files, acls will be able to help you. I would take a look at this document about file permission to help you wish acls but there are other tips as well you can us to help with your dilemma: [https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)

---

### Post by Krauser Joestar on 2011-06-16
@ruffEdgz

Thank you, it worked.

---

