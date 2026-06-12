---
title: "Installing a Network Printer"
date: 2009-10-20
forum: General Help
---

### Post by PropheticAngel on 2009-10-20
I am trying to figure out how to use a networked Xerox Workcentre 5030 with Ubuntu 9.04

After grabbing the driver set-up from the xerox web-site, I get the message:
xpqadmin: can't open file, /etc/printcap : No such file or directory

when trying to run the setup.

Help?

---

### Post by halitech on 2009-10-28
Did you download the Printer Model Package or the Linux Intel Driver? If you downloaded the Linux intel driver, delete it and get the Printer Model Package. Extract that file and then use CUPS to add a printer and go with the select a printer PPD file and browse to where you extracted the files to and look for the PPD folder. If it was the Printer Model Package, look inside the folder and use the PPD file as instructed.

---

### Post by PropheticAngel on 2009-11-10
CUPS is where I'm now getting some problems.  I've tried simply adding the printer by opening up administration->printers.  I tried connecting to the printer by entering its IP address.  I get an error 'server-error-operation-not-supported'.  

I'm very confused because my friend in the house running Intrepid was able to add the printer through CUPS with no problem.

---

### Post by halitech on 2009-11-11
when you added the IP address, did you preface it with IPP:// ?

---

### Post by PropheticAngel on 2009-11-16
No, I didn't.  However, going back and trying yields a httpConnectionEncrypt failed.

When using the search function, It popped up as "Location of the LPD network printer" and I still got the service not supported error.

---

### Post by halitech on 2009-11-16
is the machine a standalone networked machine or is it hooked to another machine and networked that way?

---

### Post by PropheticAngel on 2009-11-16
I fixed it, I restarted CUPS and it started working.

---

