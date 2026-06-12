---
title: "Trouble printing to a remote CUPS server"
date: 2011-12-14
forum: General Help
---

### Post by BattlePanic on 2011-12-14
I would like to use the lpr command to send a print job to a CUPS server on another machine on my network.

On the remote machine I have shared all printers using the CUPS web interface.

On the local machine, I have edited /etc/cups/client.conf to only include the line "ServerName 192.168.1.20".  192.168.1.20 is the ip address of the host running the CUPS server.

This configuration produces mixed results.  For example, Evince can now see and use these printers when I open the print dialog, but lpr chokes with the error "The printer or class is not shared!"

Can anyone explain how I might configure things in such a way that lpr will deal with a remote CUPS server?  I would have assumed it would simply look at client.conf to know which server to talk to.

---

