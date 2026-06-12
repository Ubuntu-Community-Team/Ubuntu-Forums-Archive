---
title: "Help with Xephyr"
date: 2011-05-30
forum: General Help
---

### Post by Éderson on 2011-05-30
I don't know it's so difficult to make it work. I'm in natty and can't find anyway to make it work. I tried all options posted in this forum but nothing. I only want to open a new window but login into a different user. It is easy and ready under Linux Mint Debian, but I use Ubuntu. Any help?

---

### Post by bodhi.zazen on 2011-05-30
I moved your post.

tips and tutorials is not necessarily for support.

Simply stating that it is not working is insufficient information.

What do you want to do ? What commands have your entered ? What error messages did you receive ?

---

### Post by JRV on 2011-05-30
To enable XDMCP server in Ubuntu 9.10 (Karmic) and after: 

   gksudo gedit /etc/gdm/custom.conf

Add the following lines:

[xdmcp]
Enable=true
MaxPending=4
MaxSessions=16
MaxWait=15

Then, restart gdm with the command:

   sudo /etc/init.d/gdm restart

or reboot the PC.
-------------------------------------------------------

To use an XDMCP client you must install Xephyr with the command:

   sudo apt-get install xserver-xephyr

XDMCP will then be available after login from the command line, use:

 Xephyr :1 -query HOSTNAME -fullscreen -once

---

