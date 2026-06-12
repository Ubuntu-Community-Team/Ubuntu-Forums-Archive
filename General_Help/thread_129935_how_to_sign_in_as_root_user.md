---
title: "how to sign in as root user?"
date: 2006-02-15
forum: General Help
---

### Post by wcks48 on 2006-02-15
the installation never ask the root password and user name. but i just put a simple normal user account and get into kubuntu. but during some settings, need my pasword, and all still okay. when dealing with the connection, when i want to connect to the LAN, the network setting menu doesn't allow me to make change and saying requires root access and click the below button. but when browse the bottom of the window, even the three button "configure, enable, and disable" buttons also not fully display. of coz, some more functions below than that also can't shown up on the screen. the sysem stting menu also felt like jammed up there. all i can do is just close it and open again.. anything wrong?

---

### Post by anirban.sam on 2006-02-15
everything is perfectly normal, just use sudo before such commands, it works with yr user passwd, in case you want a root, issue; sudo passwd root->give the new passwd->reconfirm and you have a root user

---

### Post by Zach1188 on 2006-02-15
Also, type "kdesu" in the terminal before some commands, and it will open the application as root. Example:

"kdesu konqueror"
will open Konqueror as root (It should ask for your user password).

---

### Post by jbinc1 on 2006-02-15
From a terminal session you can also type
```
 sudo -H -s
```it will ask for your password and it will change you to root for that terminal session.

---

### Post by Adrian on 2006-02-15
Check out this document:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-02-15
Read the third link of my signature.

---

### Post by afx on 2006-02-15
If you wanna be able to login as root into kde change the AllowRootAccess variable to true in file /etc/kde3/kdm/kdmrc
:cheers:

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=jbinc1]From a terminal session you can also type
```
 sudo -H -s
```it will ask for your password and it will change you to root for that terminal session.[/QUOTE]
and one more reply from me -you can also use ```
sudo -i
```
I still cannot grasp the difference btw -H -s and -i , which is somewhere in man sudo, but sudo -i is easier to remember :Pp

---

