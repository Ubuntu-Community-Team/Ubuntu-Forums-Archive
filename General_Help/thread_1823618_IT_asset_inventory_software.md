---
title: "IT asset inventory software"
date: 2011-08-12
forum: General Help
---

### Post by chedderslam on 2011-08-12
Fairly new linux user here.

I will be volunteering at a local organization today to help with their IT stuff.  I would like to boot ubuntu from a usb and have software on it that will crawl the LAN and provide info on there installed hardware and software, and allow me to save that info to the isb for later review.  It's only a few machines, all but one is windows, with an oddball mac.

Thank you for any help.

---

### Post by dino99 on 2011-08-12
lspci will help you

example:
sudo lspci -vvnn

[http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html](http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html)

and from synaptic:
 ocsinventory-reports   (admin)
 ocsinventory-agent     (client)

or:
 fusioninventory-agent  (client)

---

### Post by haqking on 2011-08-12
> **dino99 said:**
> lspci will help you

example:
sudo lspci -vvnn

[http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html](http://manpages.ubuntu.com/manpages/natty/man8/lspci.8.html)

and from synaptic:
 ocsinventory-reports   (admin)
 ocsinventory-agent     (client)

or:
 fusioninventory-agent  (client)

That will show information from local machine, not inventory the network ?

see here under the inventory section for possible software solutions.

[http://www.debianhelp.co.uk/tools.htm](http://www.debianhelp.co.uk/tools.htm)

Edit: just saw edit of above post to include OCS ;-)

---

