---
title: "VirtualBox Remote Deskio"
date: 2011-03-24
forum: General Help
---

### Post by cyberprodigy on 2011-03-24
I am using VirtualBox on my Ubuntu server.
I have a one virtual Ubuntu server running inside that, and I am able to launch virtual server with remote desktop capabilites, by running the command like that
 
root@h1540414:~# VBoxHeadless --startvm "VirtualUbuntu"
Oracle VM VirtualBox Headless Interface 3.2.12
(C) 2008-2010 Oracle Corporation
All rights reserved.

Listening on port 3389.


However as soon as I close the console from wich I launched the command, virtual server stops, but I need it keep running.
 
Is there a way to accomplish it?

---

### Post by Another Monkey on 2011-03-24
It terminated because the process is "tied" to that terminal window.
Try putting an ampersand ("&") at the end of the line.  That will "fork" the VirtualBox process away from the terminal instance.

---

### Post by cyberprodigy on 2011-03-28
> **Another Monkey said:**
> It terminated because the process is "tied" to that terminal window.
Try putting an ampersand ("&") at the end of the line.  That will "fork" the VirtualBox process away from the terminal instance.

Hey. Thank you for the response. I was able to accomplish the task by running 

**user@h1840414:~$ nohup VBoxHeadless --startvm "<VM name>" &**

---

