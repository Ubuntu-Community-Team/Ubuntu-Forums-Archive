---
title: "does ubuntu have any"
date: 2006-05-19
forum: General Help
---

### Post by Somenoob on 2006-05-19
build in remote Administration/access programs?

---

### Post by rwestgeest on 2006-05-19
[QUOTE=Somenoob]build in remote Administration/access programs?[/QUOTE]

No as far as i know, BUT You can:
[LIST]
[*]ssh to an ubuntu box and start any application you like; (ssh -X to be able to start X(Gui) applications.
[*]use VNC or RDC to take over someones keyboard mouse and screen
[*]install webmin to enable web access to all much, if not all of your machines configuration
[/LIST]

---

### Post by IYY on 2006-05-19
SSH is the best, and that's built in. Another option is not built in, but very easy to install:

[http://www.ubuntuforums.org/showthread.php?t=173146](http://www.ubuntuforums.org/showthread.php?t=173146)

---

### Post by az on 2006-05-19
[QUOTE=IYY]SSH is the best, and that's built in. [/QUOTE]

You can ssh out of your box, but you cannot ssh into your box without installing the ssh server.  This is the security model that ships with ubuntu.

To install the ssh server (the app that listens to the outside world)

sudo apt-get install ssh

Or install it with synaptic.

Ssh is a login shell.  It is encrypted.  It can tunnel x applications.  Example:

ssh -X andy@192.168.0.100
gets me to a prompt in another computer in my house.  If I run firefox from there, I get the firefox window on my screen, although it is running in the other box.  I can surf the web on a pentium I, using my 2.6 GHz computer in the other room.

---

