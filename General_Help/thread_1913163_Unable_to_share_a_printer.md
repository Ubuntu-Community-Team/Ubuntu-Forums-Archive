---
title: "Unable to share a printer"
date: 2012-01-22
forum: General Help
---

### Post by CPL_Punishment on 2012-01-22
RE: Ubuntu 11.04

I'm trying to share my locally (USB)connected HP Photosmart with another Unbuntu 11.04 host running on my home office LAN. I can't configure the CUPS server because the printer configuration applet lacks the menus. To show you what I mean I've got a screenshot here:

[http://flic.kr/p/bgE8VZ]("http://flic.kr/p/bgE8VZ")

What the heck caused that? There ought to be five drop-down menus across the top: Server Printer Group View Help. These menus are present and functional on my other Ubuntu installation.

---

### Post by plucky on 2012-01-22
> **CPL_Punishment said:**
> RE: Ubuntu 11.04

I'm trying to share my locally (USB)connected HP Photosmart with another Unbuntu 11.04 host running on my home office LAN. I can't configure the CUPS server because the printer configuration applet lacks the menus. To show you what I mean I've got a screenshot here:

[http://flic.kr/p/bgE8VZ]("http://flic.kr/p/bgE8VZ")

What the heck caused that? There ought to be five drop-down menus across the top: Server Printer Group View Help. These menus are present and functional on my other Ubuntu installation.

Try using the CUPS interface by typing into the address bar of Firefox ```
http://127.0.0.1:631/
``` and see if you can set the sharing options there.


Good Luck

---

### Post by CPL_Punishment on 2012-01-22
Thanks, Plucky. Using the CUPS page did the trick. One change in the server config file ("Browsing Off" to "Browsing On") fixed it. Printing across the LAN is OK.

Thanks to the admins for getting rid of the SPAM.

---

