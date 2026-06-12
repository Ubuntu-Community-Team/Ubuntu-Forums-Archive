---
title: "ubuntu server 10.4 printing - without cups"
date: 2010-11-30
forum: General Help
---

### Post by wcollins3 on 2010-11-30
I'm not looking to setup a print server.  I want to print documents TO an existing network printer while I'm logged in via ssh to my Ubuntu Server 10.4 command line shell.  Things like admin emails, pdf docs, etc.

All the clients on my LAN are able to print directly to the network printer without any help from the Ubuntu Server.  I don't want to setup CUPS on the server unless that's the only way to print from the server itself to a networked printer.

Do I need CUPS or can I print from the command line in some other way?

---

### Post by Wayne_V on 2010-11-30
it all depends on the network printer and what protocols it has enabled.   see here for a start:  [https://help.ubuntu.com/10.04/printing/C/printing.html](https://help.ubuntu.com/10.04/printing/C/printing.html)

---

### Post by wcollins3 on 2010-11-30
> **Wayne_V said:**
> it all depends on the network printer and what protocols it has enabled.   see here for a start:  [https://help.ubuntu.com/10.04/printing/C/printing.html](https://help.ubuntu.com/10.04/printing/C/printing.html)

Thanks for the reply. :)

I looked at that page previously and couldn't figure out how to translate it so I could do things from the command line.  I do not have any GUI on my server, as is recommended in the server administration documentation.

Is there a sort of "translation guide" so I can know what to do when the documentation says something like "Choose System &#8594; Administration &#8594; Printing"?  Tough to do that when I don't have any menus at all. ;)

Oh, and by the way, it's a TCPIP network printer with its own print server built in.  It's not attached to any computer.  It's connected to the LAN directly, via an ethernet cable.

---

### Post by Wayne_V on 2010-11-30
this should help: [http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

you need some sort of print server on the Ubuntu server,  I would recommend CUPS as the most versatile & best supported.

---

### Post by wcollins3 on 2010-11-30
> **Wayne_V said:**
> this should help: [http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

you need some sort of print server on the Ubuntu server,  I would recommend CUPS as the most versatile & best supported.

Thanks again Wayne.  I was able to get CUPS running, and then printed my document using 'lp'.

---

