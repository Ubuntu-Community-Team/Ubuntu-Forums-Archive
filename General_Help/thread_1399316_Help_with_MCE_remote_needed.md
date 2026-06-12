---
title: "Help with MCE remote needed"
date: 2010-02-05
forum: General Help
---

### Post by thedon_1 on 2010-02-05
I have an HP MCE remote as seen in this [link]("http://cgi.ebay.com/HP-MCE-KIT-REMOTE-CONTROL-USB-IR-RECEIVER-EMITTER-VISTA_W0QQitemZ140337443518QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item20acc372be")

I need help seting it up. In lirc i have set it as an Microsoft MCE remote but it doesn't work

When i type lsmod | grep lirc* i get the following

lirc_mceusb 15264 0
lirc_dev 10804 1 lirc_mceusb


I tried changing the etc/lirc/hardware.conf file so remote device = "/dev/lirc1"

No luck, anyone got any ideas?

---

### Post by falconindy on 2010-02-05
What do you mean when you say 'no luck'? Do you have an /etc/lirc/lircd.conf setup for mapping buttons? If you run irw, do you get any output when pressing buttons on the remote?

---

### Post by thedon_1 on 2010-02-05
I don't have an /etc/lirc/lircd.conf setup

I run irw but none of my key presses are registered.

---

