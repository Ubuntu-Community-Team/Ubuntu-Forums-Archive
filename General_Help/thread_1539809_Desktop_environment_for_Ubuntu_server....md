---
title: "Desktop environment for Ubuntu server..."
date: 2010-07-27
forum: General Help
---

### Post by siteregsam on 2010-07-27
Hi,
 
  I am totally new to server environment. I have to form a cloud  environment in our lab. I installed Ubuntu Enterprise cloud edition. The  interface is textual(commands). 
I need to install [COLOR=RoyalBlue]x server[/COLOR]. 
Kindly help me to get a GUI environment.

And if there is any manual regarding cloud environment setup, i am very  much eager to know abt it...

Thanks in advance...

---

### Post by heimo on 2010-07-27
I don't know about Enterprise cloud edition, but if it's like any other Ubuntu, then you can get complete desktop environment (with Gnome) by installing ubuntu-desktop package (sudo aptitude install ubuntu-desktop).

---

### Post by wojox on 2010-07-27
Use Webmin instead [Install Webmin on Ubuntu Server or Desktop 9.10 Karmic Koala]("http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/")

---

### Post by heimo on 2010-07-27
> **wojox said:**
> Use Webmin instead [Install Webmin on Ubuntu Server or Desktop 9.10 Karmic Koala]("http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/")

I second wojox, it's generally not good idea to install desktop / lot's of unneeded software on a server. Webmin is better idea.

---

