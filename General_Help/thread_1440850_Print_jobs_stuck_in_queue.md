---
title: "Print jobs stuck in queue"
date: 2010-03-28
forum: General Help
---

### Post by matt531320 on 2010-03-28
I have 2 printers plugged into a Windows XP PC (an Epson Stylus Photo RX580, and an HP Laserjet 1020) with full sharing on and everything, and is shared with other Windows PCs via the network I have set up. It has worked perfect. But today I added a PC running Ubuntu 9.10 and and can't figure out for the life of me what I am doing wrong. I installed both of the printers via the GUI in Administration, and both of them are detected and Ubuntu says they're working. But when I put something in the queue to print it stays there with the status "pending". Any ideas?

---

### Post by gtbutler on 2010-04-02
I have the same problem. To me it seems that SAMBA is not looking out on the network to see the printers. I can setup the printers on the Windoz machines but not on UBUNTU 9.10. I have set up printers at home on the WINDOZ machine from UBUNTU 8.02 and CUPS finds it and installs the printer.

Any help will be greatly appreciated.

Gary

---

### Post by megahost on 2010-04-02
Happens to me a lot too. Whether its a problem between the drivers and linux compatibility, I'm not sure. Every now and then, it will print.

---

### Post by bmaring on 2010-04-07
I am seeing similar problems.  Have shared printer on win 7 machine.  I can see the shared printer from ubuntu 9.10 machine and can connect to it.  From ubuntu, it appears that a subsequent print operation is successful, however, the win 7 machine never gueues the print job and the document to print just disappears.  Nothing I can find in any logs is helpful. 

Any ideas as to what to try?

---

### Post by Rockcarver on 2010-04-08
I have almost the same problem. I have an Asus laptop with Vista and Karmic double boot, almost never boot to vista. Most thing work so well on Ubuntu, but printing is unstable. I print documents out of Open Office, of course, no problem, or very few. But images out of GIMP, sometimes they print smoothly, and sometimes unpredictably they hang up with the print job annotation "pending". I have never got  a "pending" file to print. Have to cancel it and fiddle with paper format, or other parameters, I can't even recall what, and restart the print process. Then sometimes they print.

Any ideas, anyone?

Oh yes, if it matters, my printer is Epson Stylus C87 plus

---

### Post by Scunnered on 2010-04-08
I am not too sure if this will help but I will offer up how I work in the hope that it may assist.

I use an Epson Stylus Photo R265 printer which works well for me.  The printer is connected to my Asus X51L laptop via the USB connection.  I have it set up as a shared printer via Samba and my partner can access it from her XP system. Her main print runs are A4 photos and she is able to print these with ease. 

It may be that by linking your printer to Ubuntu and sharing from there may offer a better solution.

---

### Post by Rockcarver on 2010-04-09
Scunnered: I am not on a printer-sharing lan, but in any case, when I initiate printing from GIMP, the dialog box indicates that the printer's location is ubuntu. Is that essentially what you are suggesting?

Anybody: how to get a "pending" file to print?

---

### Post by scarab on 2010-04-11
here an hp deskjet correctly identified by system and working well by itself (photocopying, etc) simply do not print:
 document print status says print job is completed, but printer appears to ignore anything that comes from the computer, anyway the system can identify when printer is disconnected, reconnected, etc.... only printer itself has problems, scanning through xsane is ok
any ideas? thanks in advance

---

### Post by Rockcarver on 2011-03-03
I found one cause: If Ubuntu does not read ink levels on the printer, then it does not notify you that the problem is that you are out of ink, and just puts "pending" in the status field. Then it sits forever till you realize that you have to change the ink cartridge, after which all goes smoothly.

---

