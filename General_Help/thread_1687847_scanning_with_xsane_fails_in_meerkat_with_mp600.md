---
title: "scanning with xsane fails in meerkat with mp600"
date: 2011-02-14
forum: General Help
---

### Post by kkruecke on 2011-02-14
I am running Ubunut 10.10. I have a Canon MP600. I can print fine, but can't scan.

Applications->Graphics->XSane Image Scanning Program

As soon as I click the Scan button, I get "operation cancelled". 
The version of xsane (shown in the titlebar) is xsane 0.997 Canon PIXMA MP600".

---

### Post by corncob on 2011-02-14
I'm using Simple Scan on my eeebox with a mp640 and it does all I want to do.  It seems it came with 10.10 but if not:
```
sudo apt-get install simple-scan
```
Are you by chance using a 64 bit system?  There I do have trouble with the printer.

---

### Post by kkruecke on 2011-02-14
Thanks for the reply. Yes, Simple Scan seems to work, but I need to save the scan as a PDF, and I eventually want to share the scanner on my in-home network. Printing works fine. Has for a long time.

---

### Post by kkruecke on 2011-02-14
Ok, I see I can save as PDF using Simple Scan, if I chose Text as the type of item being scanned. 

Now how do I share the scanner and scan from a Windows Vista client?

---

### Post by corncob on 2011-02-15
> **kkruecke said:**
> Ok, I see I can save as PDF using Simple Scan, if I chose Text as the type of item being scanned. 

Now how do I share the scanner and scan from a Windows Vista client?

I have the mp640 connected to the router via ethernet cable (as is my eeebox).  My wife says she uses the scanner all the time from her Windows 7 notebook on wireless from the other room.  Where it doesn't work is on her 64 bit Ubuntu installation.  Canon, last I looked, doesn't supply a 64 bit Linux driver for the printer.  I've seen a force-architecture workaround but never did get that to work.

---

### Post by kkruecke on 2011-02-15
I just realized I can use Simply Scan, then save it to a Windows client machine wirelessly connected to my in-home LAN. Funny, I had never realized I could go to Places->Network->Windows Network and see Windows clients that have shared drives. I had been booting into Windows. Problem solved: fax locally, then save to shared folder on a network-connected windows client machine.

---

