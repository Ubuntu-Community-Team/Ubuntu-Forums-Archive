---
title: "I am not the owner so I cannot change these permissions"
date: 2006-05-24
forum: General Help
---

### Post by shredfitz on 2006-05-24
All I want to do is change the permissions to allow me to write a file to /usr/lib.

I have looked at wiki to follow the instructions to allow me permission to write to this folder.  I right click to properties for the folder and it tells me that only the owner can change permissions and the owner is root.   So i look for the info that tells me how to log in as root.  Then I try to change permissions to the /usr/lib and I cannot.  How is this done ?

---

### Post by aysiu on 2006-05-24
Changing permissions on a system file is not a good idea.

Read this. It will help you, I promise:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by shredfitz on 2006-05-24
thanks again to aysiu

---

### Post by LORD_PoLvO on 2006-05-24
if that dosent work u could always go root terminal and do a chmod 777?

---

### Post by Isoss on 2006-05-24
[QUOTE=LORD_PoLvO]if that dosent work u could always go root terminal and do a chmod 777?[/QUOTE]
You can also install nautilus with synaptic (a simple package ) and then run 
for example
```
sudo nautilus /var/www/
```
hit enter and enter your password and the www folder will open with a full permission to do anything whether you wanna write, edit, copy, cut, remove or change permissions and everything. But of course concerning the /usr/lib you better listen to aysiu: [quote=aysiu]Changing permissions on a system file is not a good idea.[/quote]

---

