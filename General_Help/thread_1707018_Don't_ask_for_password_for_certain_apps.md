---
title: "Don't ask for password for certain apps?"
date: 2011-03-14
forum: General Help
---

### Post by 8jwong14 on 2011-03-14
I've recently installed Ubuntu 10.10 on my mom's computer.  I've also installed a few programs like Emesene and PPStream for her to use.  My mom can get in the way of it but when she runs PPStream, she always gets a popup prompting to enter the password.  IT can get irritating at times.  I know PPStream is safe so I don't want it to have to keep asking me for the password.  I installed it from a Deb.  Can I stop the program from askign for the password and jsut work?

---

### Post by andrewthomas on 2011-03-14
Use sudo NOPASSWD option

---

### Post by 8jwong14 on 2011-03-16
> **andrewthomas said:**
> Use sudo NOPASSWD option
How do I use it on the program?

---

### Post by andrewthomas on 2011-03-17
You need to edit the /etc/sudoers file to grant the permissions.

see ```
man sudoers
```for example I have the following in my sudoers file.
```
%wheel ALL=(ALL) NOPASSWD: /sbin/iptables /usr/bin/emerge /usr/bin/eix-sync /usr/bin/revdep-rebuild /usr/sbin/dispatch-conf /usr/sbin/env-update
```You can change the %wheel to the username that you want to grant the permissions to and change the commands to the commands that you want to permit.

---

