---
title: "Printer Help"
date: 2010-03-15
forum: General Help
---

### Post by sheepsy on 2010-03-15
Hi,

I am trying to print to a network printer from my 9.10 install. 

The printer is Canon_MF4360-4390, when browsing for printers, cups finds it immediately. I found drivers for this printer online (driver is called UFR_II_Printer_Driver_for_Linux_V200_uk_EN). The drivers installed without any problems. 

I can go through cups and add the printer successfully. I can even print a test page that shows up in the queue as completed. However, nothing comes out of the printer. 

Also, there is nothing in /var/log/cups/error_log to show that an error has occurred.

Can someone help me in debugging this or at least point me in the right direction for figuring out the problem? 

I looked at general wiki pages like this [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

But they have not given me any clue as to have to resolve this.

---

### Post by sheepsy on 2010-03-15
Is there a better place to post this question?

---

### Post by mfa on 2010-03-15
I had exactly similar symptoms when i tried to install a printer on linux. Only i knew there were problems with the driver (i can't remember the details, sorry). The curious thing was that the system didn't seem to find any problems and reported success on every printing job, while the printer just sat quiet doing nothing. Could it be that the driver isn't compatible with ubuntu 9.10?

---

### Post by sgosnell on 2010-03-15
Sounds like a wrong driver.  I have no personal experience with Canon printers, but I've heard they can be problematic under Linux.

---

