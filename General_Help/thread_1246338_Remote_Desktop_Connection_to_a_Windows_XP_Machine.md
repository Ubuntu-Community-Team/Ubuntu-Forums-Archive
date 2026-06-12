---
title: "Remote Desktop Connection to a Windows XP Machine"
date: 2009-08-21
forum: General Help
---

### Post by kt_pie on 2009-08-21
This topic was already posted: [http://ubuntuforums.org/showthread.php?t=722601](http://ubuntuforums.org/showthread.php?t=722601)

But it's old and I cannot reply.

Here is what I have done:

Applications > Internet > Terminal Server Client 

Computer: (I've tried typing in the IP Address as well as the computer name)
Protocol: RDP
Username: [I]my username on the Windows machine
[/I]Password: *my password on the Windows machine*
Domaine: none
Client Hostname: Ubuntu Computer's Name

But I get an error message that says:

Autoselected keyboard map en-us
ERROR: channel_register
WARNING: initializing sound support failed
ERROR: (IP ADDRESS) unable to connect

Does anyone know what this means - or - have had the same issue but found other routes to connect from Ubuntu to Windows XP with success?

Thanks in advance!

---

### Post by kanikilu on 2009-08-21
> ERROR: (IP ADDRESS) unable to connect

This is a dumb question, but are you sure RDP is enabled and working on that Windows box? An exception in the Windows (or other) firewall may need to be added. Can you get to it from another computer?

Can you ping it from Ubuntu? If so, go to System -> Administration -> Network Tools -> Port Scan and check that host to see that port 3389 is open (default RDP port).

---

