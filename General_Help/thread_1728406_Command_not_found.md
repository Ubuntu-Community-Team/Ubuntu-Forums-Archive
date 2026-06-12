---
title: "Command not found"
date: 2011-04-13
forum: General Help
---

### Post by ter_smurf on 2011-04-13
Why do it get this error when doing the command start, stop, restart?  I'm trying to setup a few things as I am new to Linux.  I was running:
 
sudo /etc/init.d/samba stop
 
Also:
 
sudo /etc/init.d/apache2 restart
 
Seems like when ever I try to do anything that someone posts, it never works.  There's just so many things that don't work and peoples directions are always different from eachother or my menus don't show it they show.

---

### Post by ter_smurf on 2011-04-13
Also I'm always getting the error: No such file or directory.  But the directory and files are there.

---

### Post by vivek.pandey on 2011-04-13
> **ter_smurf said:**
> Why do it get this error when doing the command start, stop, restart?  I'm trying to setup a few things as I am new to Linux.  I was running:
 
sudo /etc/init.d/samba stop
 
Also:
 
sudo /etc/init.d/apache2 restart
 
Seems like when ever I try to do anything that someone posts, it never works.  There's just so many things that don't work and peoples directions are always different from eachother or my menus don't show it they show.

]what error message do you get?

---

### Post by coffeecat on 2011-04-13
The syntax of the services commands changed around Jaunty, or thereabouts. Perhaps the post you found was old. Be wary of old posts, blogs and howtos. Things change.

I believe that instead of...

```
sudo /etc/init.d/samba stop
```You need to use the service command for /etc/init.d scripts. I.e:

```
sudo service smbd stop
```Or start or restart.

I've no experience of apache - is it an /etc/init.d script? If so, the syntax will be the same. Type 'man service' in the terminal for more.

---

### Post by earthpigg on 2011-04-13
what is the error you are getting?

---

### Post by vivek.pandey on 2011-04-13
> **coffeecat said:**
> The syntax of the services commands changed around Jaunty, or thereabouts. Perhaps the post you found was old. Be wary of old posts, blogs and howtos. Things change.

I believe that instead of...

```
sudo /etc/init.d/samba stop
```You need to use the service command for /etc/init.d scripts. I.e:

```
sudo service smbd stop
```Or start or restart.

I've no experience of apache - is it an /etc/init.d script? If so, the syntax will be the same. Type 'man service' in the terminal for more.

well i /use apache and to restart it
```
 sudo /etc/init.d/apache2 restart 
``` works

---

### Post by ter_smurf on 2011-04-14
The error I get is when it says: Command not found

---

