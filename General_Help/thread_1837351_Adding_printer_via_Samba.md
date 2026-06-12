---
title: "Adding printer via Samba"
date: 2011-09-01
forum: General Help
---

### Post by marsgorski on 2011-09-01
Hi,

I am trying to add/configure a network printer in my college campus, but unfortunately the IT people in my college are not very helpful to Linux users. I have an address for the printer that is in the form \\[print server]\[printer], but in the configuration window I need an address of the form smb://[workgroup]/server[:port]/printer. Does anyone know how to add such a printer? Specifically what kind of information do I need from the printer?

---

### Post by Morbius1 on 2011-09-01
Unless your admin has made this unnecessarily complicated all you need is :
```
smb://[print server]/[printer]
```All that stuff about workgroup and port is very precise and it may be necessary but it most likely is not required.

---

### Post by marsgorski on 2011-09-02
Thanks, I tried configuring the printing using that smb address. When it asked for a driver I selected the recommended ones (generic and text only.) But when I tried to print a .pdf file I received the error message 
```
The following error occurred while printing...
'lpr: Unsupported format 'application/vnd.adobe-reader-postscript'!'
```

I also tried printing it with Document Viewer. I did not get an error message but it did not print.

I don't know if this helps but looking at the configuration under Windows, the driver used is "HP Universal Printing PCL 6 (v5.3)". It also specifies two ports in the form "xxx.xxx.xxx.xxx" and "xxx.xxx.xxx.x". The printer model is "HP LaserJet P4015dn"

---

