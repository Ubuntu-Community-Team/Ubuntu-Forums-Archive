---
title: "&quot;X-Window&quot;"
date: 2009-09-16
forum: General Help
---

### Post by warudo.kun! on 2009-09-16
[CENTER][FONT=Trebuchet MS][SIZE=2]Hello. I just installed Ubuntu Server 9.0.4, and I need to know how can I run "x window" through the command prompt. I would appreciate some assistance on this. This is something new to me.

Thank you.

` warudo.kun![/SIZE][/FONT]
[/CENTER]

---

### Post by Barrucadu on 2009-09-16
You need to install the package, and then run the command "startx".

---

### Post by warudo.kun! on 2009-09-16
> **Barrucadu said:**
> You need to install the package, and then run the command "startx".

[CENTER][FONT=Trebuchet MS]Wait, what package?

Edit: I cannot do "startx", for it asks me to log in as root. But, during the installation it never asked me for a password as root, so I can't log in as root when it asks me for a password. Does anyone know the default password? I'm quite confused.

Thanks.
[/FONT] [/CENTER]

---

### Post by P4man on 2009-09-16
What are you trying to achieve? I assume you installed ubuntu server version for a reason.. if you want a full blown GUI, you need to install a desktop environment, like gnome.

```
sudo apt-get install ubuntu-desktop
```

As for the "root password"; read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Short version: if you need root permission, put "sudo" (or "gksudo" for graphical apps) in front of the command, and type your user password.

---

### Post by nothingspecial on 2009-09-16
```
sudo apt-get install xserver-xorg xserver-xorg-core
```

Then install a window manager.

```
sudo apt-get install openbox
```

or another one

---

### Post by warudo.kun! on 2009-09-17
[CENTER][FONT=Trebuchet MS]Thank you everyone, for the great help.
I have a question, if you may. 

How can I set-up a domain using samba?

Thanks.[/FONT]
[/CENTER]

---

### Post by P4man on 2009-09-17
Google is your friend:
[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

---

