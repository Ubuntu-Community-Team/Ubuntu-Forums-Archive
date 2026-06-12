---
title: "Printer sharing in Oneiric 11.10?"
date: 2011-10-23
forum: General Help
---

### Post by sgarman on 2011-10-23
Hello,

The last version of Ubuntu I used was Maverick, which had a different printer setup tool than is now included in Oneiric. I cannot figure out how to share a printer over the network.

If I go to System Settings -> Printers, my USB-connected printer shows up automatically and I can print fine from my host. 

There is an Options configuration area that asks for "Allowed users" - I have no idea what to put in this to allow all users on my LAN to print. Can anyone tell me what I need to do?

Thanks,

Scott

---

### Post by PeterJCLaw on 2011-12-29
I've also got this same issue. I've installed samba, since I'm trying to share to a windows machine, but I can't seem to set that up to allow guest access properly either.
This used to be **really** simple!

---

### Post by PeterJCLaw on 2011-12-29
Well I've got some of the way towards this... In the print server settings, you need to enable publishing so that other computers can see the shared printer:

System > Administration > Printing > Server > Settings > Publish shared printers connected to this system

Not sure why you need to have this as a separate step, but I wonder if once shared they can be used if you know that they're there?

In samba (I'm using system-config-samba to simplify things) I've then enabled guest access using the nobody account, and set the print$ share to allow everyone access (under the Access tab). However, the XP machine I've got that's trying to print is still being challenged for a password!

---

