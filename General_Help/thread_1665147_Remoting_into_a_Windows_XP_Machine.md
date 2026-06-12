---
title: "Remoting into a Windows XP Machine"
date: 2011-01-11
forum: General Help
---

### Post by sandyp on 2011-01-11
I'd like to connect into a Windows XP machine that is on the home network.

I believe the settings on the XP box are correct as I have no problem using remote desktop to log into it from another Windows machine.

When I use Remote Desktop Viewer on Ubuntu and connect to the IP address (192.168.1.5), I get the message "Connection closed.  Connection to host 192.168.1.5 was closed".

Thank you

---

### Post by hogfan on 2011-01-11
rdesktop is good for accessing Windows machines.  Google is your friend. :)

Open Terminal and type:

sudo aptitude install rdesktop


-hogfan

---

