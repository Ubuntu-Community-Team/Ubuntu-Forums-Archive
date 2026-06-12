---
title: "lpr printing"
date: 2006-03-15
forum: General Help
---

### Post by mbeach on 2006-03-15
Is it possible to print to a remote printer using lpr without setting the printer up in the /etc/cups/printers.conf file?  By this I mean if there is a server out there hosting hundreds of printers, allowing lpr, can I print to one of them using a call like (this doesn't work, just showing what I'd like to be able to do):

**lpr -p //printserver/printernameonserver myfile.ps**

So far I've only been able to accomplish this if I setup the printer locally.  In a similar situation on a Windows box using MKSToolkit (allows windows to have a unix shell and commands etc), it uses:
**lpr -S printserver -P printername myfile.ps**

I'm at a bit of a loss and don't know how to proceed.  Basically I need to print a postscript or pcl file to a printer (which can be to one of 200 printers) without setting up each of the printers on the local machine.

---

