---
title: "Ubuntu Desktop to Ubuntu Server"
date: 2011-12-05
forum: General Help
---

### Post by Kishant on 2011-12-05
Hi to all I'm new in the community so please be understanding :)

I'm trying to setup a server for a school portal and i chose ubuntu as the OS. Because of the bandwidth that the school has i having trouble installing the desktop environment of ubuntu server "sudo apt-get install ubuntu-desktop". My alternative was installing the ubuntu desktop and then later on after I setup what needs to be setup i would remove the desktop environment thus having a low memory system for my server. Is this advisable and possible? And will this be efficient?

Thank you in advance for the reply.

---

### Post by snowpine on 2011-12-05
Welcome to the forums Kishant!

A desktop environment is not necessary for Ubuntu Server. The Ubuntu Server Guide will help you step-by-step using only command-line terminal commands:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

If you need a temporary desktop environment, you don't need the full ubuntu-desktop (which includes an office suite and so on). Something lightweight like lxde, icewm, or fluxbox will give you basic functionality with a much smaller download.

---

### Post by zero2xiii on 2011-12-05
Hay,

+1 for welcome to the forums :)

I personaly run many servers (FTP, HTTP and email aswell as intranet servers) on ubuntu boxes. The heaviest load I have is on the intranet server (internal internet for company files and websites and information etc etc) and thats about 350 - 380 users at any given time and my server runs on a Quad core 2.2Ghz 4Gig ram ubuntu machine. And I haven't had issues with resources.

I suggest keeping the GUI/Desktop environment (even if lxde) since you do not sound experienced enough with linux to use a shell only environment (otherwise you would not have wanted to install a desktop environment in the first place as everything can be done via shell)

You might just set up the server to boot to a terminal instead of a GUI and then if you need to have a desktop, just do a "startx" or simmilar.

Good luck though.
Cherz

---

