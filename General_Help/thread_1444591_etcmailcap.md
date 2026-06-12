---
title: "/etc/mailcap"
date: 2010-04-01
forum: General Help
---

### Post by gasull on 2010-04-01
Hi.

I've been configuring /etc/mailcap, but it is overwritten.  I'm not sure if this happens with automatic upgrades or when I reboot the system.

How can I prevent my /etc/mailcap from being overwritten?

Thank you.

---

### Post by blueridgedog on 2010-04-01
update-mime, run during package installation and removal may be overwriting your mailcap file.  The man page shows how to put your entries in permanently with entries in /usr/lib/mime/packages:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?update-mime+8](http://unixhelp.ed.ac.uk/CGI/man-cgi?update-mime+8)

You may also want to consider putting your customizations in ~/.mailcap

---

