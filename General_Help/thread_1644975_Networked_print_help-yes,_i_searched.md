---
title: "Networked print help-yes, i searched"
date: 2010-12-14
forum: General Help
---

### Post by artshark on 2010-12-14
I am on a 11.04 system in a windows house so to speak. i dont know if its with samba or whatever, but our printer is mounted on a NAS with a print server. when i do search for a cups server, it finds the NAS' network ID, and an arrow appears to show further entities off that NAS exist, but after that it times out. any tips? it clearly recognizes the print/server at some level, but not sufficiently.
thanks,
Art

---

### Post by bobcollard on 2010-12-14
Open your browser and in the address line enter "http://localhost:631"  (without the quotes).  This will get you the cups menu, you will need your username and password, the same as you use on your computer.  From there "Add Printer" and follow along to see if it recognizes the printer of choice on your network that you are hooked up to.

---

### Post by artshark on 2010-12-15
> **bobcollard said:**
> Open your browser and in the address line enter "http://localhost:631"  (without the quotes).  This will get you the cups menu, you will need your username and password, the same as you use on your computer.  From there "Add Printer" and follow along to see if it recognizes the printer of choice on your network that you are hooked up to.
does it have any autodiscovery features? it prompts me for a URL but my NAs is not helpful in acquiring the exact address of the printer

---

### Post by bobcollard on 2010-12-15
> **artshark said:**
> does it have any autodiscovery features? it prompts me for a URL but my NAs is not helpful in acquiring the exact address of the printer
You might check one of the Windows computers for an address.  Seems to me you should be able to reach it through System>Administration>Printing then click on Add>Network Printer, wait for a minute and see if it does  find it for you.  I never had any problems with my network but it is not NAS (Network Assisted Storage.)  BTW, you have to have cups installed to use Localhost:631

---

### Post by artshark on 2010-12-15
cups itself works.

---

