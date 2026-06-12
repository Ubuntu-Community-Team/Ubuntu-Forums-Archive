---
title: "I want to chnage /var/www to another folder."
date: 2009-12-23
forum: General Help
---

### Post by klnyc on 2009-12-23
Hello guys,

  okay, by default Apache would look for /var/wwww/index.html( It WOrks! screen). Now, if I want Apache point to different path. Where and how I config this?  I google some thing about "sudo a2dissite", I dont know too much about this syntax.

Thank you!!

---

### Post by audiomick on 2009-12-23
Hallo,
I don't know about apache.

The command "sudo" that you have found gives you root privileges.
The directory /var belongs to root, so you need root privileges to edit stuff in there.

You will be asked for a password. This is the one you log on with. You will not see what you are typing. The terminal doesn't show passwords when you enter them.

Be very careful with "sudo". Because it gives you root privileges, it puts you in a position to change system files, which can break your system if you get it wrong.

---

### Post by sisco311 on 2009-12-23
> **klnyc said:**
> Hello guys,

  okay, by default Apache would look for /var/wwww/index.html( It WOrks! screen). Now, if I want Apache point to different path. Where and how I config this?  I google some thing about "sudo a2dissite", I dont know too much about this syntax.

Thank you!!

[uhelp]community/ApacheMySQLPHP#Virtual Hosts[/uhelp]

---

### Post by klnyc on 2009-12-23
> **sisco311 said:**
> [uhelp]community/ApacheMySQLPHP#Virtual Hosts[/uhelp]

Thank you!!  Let me try it out. LOL, now I know whats  "a2dissite" mean(apache2disable site).

If I put a folder in root. What permission i need?

---

### Post by junapp on 2009-12-23
edit the 
/etc/apache2/sites-available/default
file and change references to the /var/www to the path you want to use.

use 
sudo /etc/init.d/apache2 restart
or maybe
sudo /etc/init.d/apache2 reload

to get the changes to take hold.

---

### Post by konqueror7 on 2009-12-23
you may change the config of apache, forgot what was it. :P

anyway, you can change the folders permission by issuing, 
```
sudo chown -R $USER:$USER /var/www
```
this will change the owner to you and your group.

another thing you may want to try is if you already have a source folder is to create a *symbolic link* to it but in */var/www*'s name, say my source folder is at */media/Code/PHP*, i would execute the command,
```
sudo ln -s /media/Code/PHP /var/www
```

for more info, you may read the [ApacheMySQLPHP Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP#Edit%20Apache%20Configuration")

---

### Post by junapp on 2009-12-23
> **klnyc said:**
> If I put a folder in root. What permission i need?
any reason why you don't want it under your own home folder somewhere?

you can create a folder anywhere (sudo mkdir /www), but under root may not be the best choice.

---

### Post by klnyc on 2009-12-24
> **junapp said:**
> any reason why you don't want it under your own home folder somewhere?

you can create a folder anywhere (sudo mkdir /www), but under root may not be the best choice.

Yah, I skip the root ideal. I put it in my home dir.

---

