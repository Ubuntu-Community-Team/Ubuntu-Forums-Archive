---
title: "Protecting a folder"
date: 2011-05-14
forum: General Help
---

### Post by TimmyK. on 2011-05-14
Is there any way to password protect a whole folder?

---

### Post by doas777 on 2011-05-14
its not exactly what you have described, but I recommend [Truecrypt ]("http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/")for this use case. 
it lets you create encrypted volumes (essentially a folder) that are very secure, and can be easily moved from system to system (since truecrypt is available for most OSes), and you don't risk losing access if you have an emergency and have to rebuild your OS. just don't forget your password.

---

### Post by Thewhistlingwind on 2011-05-14
As far as I know you have two options:

Encrypt it
Implement some form of MAC like Apparmor or Selinux

---

### Post by Rubi1200 on 2011-05-14
Another option to consider is this:
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

