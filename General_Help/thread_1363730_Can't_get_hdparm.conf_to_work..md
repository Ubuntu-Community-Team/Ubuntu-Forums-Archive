---
title: "Can't get hdparm.conf to work."
date: 2009-12-24
forum: General Help
---

### Post by grandsatrap on 2009-12-24
Can someone please tell me how to get the contents of hdparm.conf to be applied when the system boots?

I don't want to have to remember to type all of my hdparm commands in at the command line after my system starts.

I have just found that there is a file here: "/etc/udev/hdparm.rules" that refers to a file here: "/lib/udev/hdparm" (which is different from the hdparm on the path - at "/sbin/hdparm")

I'm confused and can't find any documentation on this. "man hdparm" and "man hdparm.conf" don't tell me how to get hdparm.conf to work when Ubuntu boots.

Help ...  has ANYONE gotten this to work?

---

