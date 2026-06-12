---
title: "How to get printer to work in Opera 8.51"
date: 2006-02-16
forum: General Help
---

### Post by Red Knuckles on 2006-02-16
I'm confused by the printer dialogue in Opera. It asks for a "printer program". What is the "printer program" in Ubuntu 5.10???:confused:  I have a printer [HP 3940] configured and set as default already. Firefox and Epiphany just worked as did Thunderbird. The choose box goes to /usr/bin by default but I haven't found anything in there that works. I also tried just typing in CUPS and that didn't work. Also typed in hpijs which is the driver for this printer. Didn't work. Dadgummit.

---

### Post by sabitha on 2006-02-16
copy your printcap file in /var/run/cups/ to /etc/

code :

$ sudo cp /var/run/cups/printcap /etc/

hope this can help you
:-D

---

### Post by bazcor on 2006-02-16
Well I have little clue as to why it works, but it certainly did for me!

---

### Post by wrtrdood on 2006-02-16
FWIW  - if you use KDE just put kprint --stdin here.  Works great.

---

### Post by Red Knuckles on 2006-02-16
[QUOTE=sabitha]copy your printcap file in /var/run/cups/ to /etc/

code :

$ sudo cp /var/run/cups/printcap /etc/

hope this can help you
:-D[/QUOTE]

Thanks, that helped, I can now print web pages. I can't, yet, get it to print e-mail. Does anyone know how to get it to do that???:confused:

---

### Post by Red Knuckles on 2006-02-16
[QUOTE=Red Knuckles]Thanks, that helped, I can now print web pages. I can't, yet, get it to print e-mail. Does anyone know how to get it to do that???:confused:[/QUOTE]

Woops, I spoke to soon. I rebooted and now Opera is printing e-mail. Problem solved. Thanks Sabitha.:)

---

