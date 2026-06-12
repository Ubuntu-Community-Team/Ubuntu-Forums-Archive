---
title: "connection to a machine remotely from web or VNC"
date: 2011-12-08
forum: General Help
---

### Post by N4ILZ on 2011-12-08
Hi All,

got a simple question. Currently, all of the machines in my house run Ubuntu (6). I'm trying to setup an Apache web server to run on my intranet (no outside Internet access) so that any one of the machines and guests machines can view the website on their browser and check out the data hosted on the site. The machine I'm trying to get to the Apache server is running fine, with monitor, keyboard, mouse, ethernet and power. I want to take this machine and put it in the entertainment center of our house (closest to the DSL modem). I don't want to have anything but a power cord and ethernet cable connected to it (the machine) as it will just host the site. Now, in order to install new recipes/data to the web server I want to connect remotely via my laptop. But as soon as I remove the monitor, keyboard and mouse cables the machine boots up, logs into Ubuntu but I can't connect remotely (but the web server and site run just fine). Any ideas on what programs will allow me to accomplish this? All machines are running Ubuntu 10.04.

---

### Post by phidia on 2011-12-08
The site/how to I'm linking [here]("http://news.metaparadigma.de/linux-setting-up-a-debian-vnc-server-237/") are for debian but the vnc setup is all the same.

---

### Post by N4ILZ on 2011-12-09
That is a great article. On your server that you're connecting too, do you have keyboard, mouse and monitor cables plugged into it?  Currently, I'm using VNC to connect to my server, but I need the cables plugged in. I don't want those cables plugged in as the machine will be seen by all.

---

### Post by NautilusUK on 2012-03-18
> **N4ILZ said:**
> Hi All,

got a simple question. Currently, all of the machines in my house run Ubuntu (6). I'm trying to setup an Apache web server to run on my intranet (no outside Internet access) so that any one of the machines and guests machines can view the website on their browser and check out the data hosted on the site. The machine I'm trying to get to the Apache server is running fine, with monitor, keyboard, mouse, ethernet and power. I want to take this machine and put it in the entertainment center of our house (closest to the DSL modem). I don't want to have anything but a power cord and ethernet cable connected to it (the machine) as it will just host the site. Now, in order to install new recipes/data to the web server I want to connect remotely via my laptop. But as soon as I remove the monitor, keyboard and mouse cables the machine boots up, logs into Ubuntu but I can't connect remotely (but the web server and site run just fine). Any ideas on what programs will allow me to accomplish this? All machines are running Ubuntu 10.04.

Have you ensured the VNC server is set to start at boot?

---

### Post by N4ILZ on 2012-03-18
I have actually switched OS's since this post.  I switched to Vector 7, haven't had any problem with VNC.

---

