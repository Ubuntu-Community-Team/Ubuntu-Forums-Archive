---
title: "Is there an alternative to mdconfig for 11.04?"
date: 2011-09-15
forum: General Help
---

### Post by Ron Jones on 2011-09-15
I'm building a new pfSense firewall on an embedded platform, and pursuant to the instructions contained here [http://doc.pfsense.org/index.php/Modifying_Embedded](http://doc.pfsense.org/index.php/Modifying_Embedded) I would like to mount the image file, and edit the config.xml file before inserting the Compact Flash card into the motherboard.

The aforementioned instructions involve the use of the mdconfig command. However, Ubuntu 11.04 doesn't know it, and neither apt-get, nor synaptic have heard of it. While there is an ubuntu man page [http://manpages.ubuntu.com/manpages/intrepid/man4/md.4freebsd.html](http://manpages.ubuntu.com/manpages/intrepid/man4/md.4freebsd.html) it looks like mdconfig is a FreeBSD application.

Is there something similar available for Ubuntu?

Thanks,
Jones

---

