---
title: "Windows 7 won't print to Ubuntu but Vista will?"
date: 2011-01-09
forum: General Help
---

### Post by nick_xj on 2011-01-09
I have a HP c4100 series printer connected to my **Ubuntu** computer. This computer prints **just fine**.
 
I also have a **Windows Vista** computer that's connected to the Ubuntu HP via CUPS (by installing network printer with path of [http://xxx.xxx.xxx.xxx:631/printers/printername](http://xxx.xxx.xxx.xxx:631/printers/printername)). This computer also prints **just fine**.
 
My problem is I just got a new **Windows 7** laptop, and connected it to the HP via CUPS the same way as the Vista machine. It installed fine. However the Win7 Laptop **will not print**. When I try to print, it acts like it is going to print, but never gives an error and the file never makes it into the printer queue (on either the win7 or ubuntu machines, i have tried printing with both queues open to see what happens).
 
 
 
*Things I have already changed:*

**On the Ubuntu machine:**
[LIST]
[*]Changed all the printer settings on printer to allow any and all connections including printing from the internet.
[*]Edited the /etc/samba/smb.conf to allow CUPS printing and allow guest access
[/LIST]**On the Win7 machine:**
[LIST]
[*]Fixed my LAN security settings (disabled require 128bit encryption, send LM and NTLM responses)
[*]Reinstalled printer several times.
[/LIST]
I have googled this issue almost every day for a month and tried every setting that I have came across (changed them back if it didn't help). So far nothing has worked for me, and this is my last ditch effort to get this printer working.
 
Does anyone know why I can not print from my Windows 7 machine to a printer connected to my Ubuntu machine?
 
*especially when I CAN print from the UBUNTU and Vista machines.*

---

### Post by nick_xj on 2011-01-17
edit: check reply 3
 
(apparently lag causes double post?)

---

### Post by nick_xj on 2011-01-17
edit: check reply 3
 
(apparently lag causes double post?)

---

### Post by nick_xj on 2011-01-17
Just another thought
 
Do I have to install extra network protocols on the Windows 7 machine (such as ipx/spx) to make it talk to the Ubuntu computer?
 
On the Win7 machine I can ping the Ubuntu computer via it's IP, but I cannot ping it via its Computer Name.
 
I also cannot access the files via Samba from the Win7 machine, but I can from the Vista machine.

---

### Post by drdos2006 on 2011-01-17
Windows 7 desktop needs a Windows server with attached printer.
Windows has removed the Internet Printing Protocol from Windows 7.
There is a patch from Microsoft but I could never get the patch to work.
You need to google on "windows 7 printing".

regards

---

### Post by piquat on 2011-01-18
> **drdos2006 said:**
> Windows 7 desktop needs a Windows server with attached printer.
Windows has removed the Internet Printing Protocol from Windows 7.
There is a patch from Microsoft but I could never get the patch to work.
You need to google on "windows 7 printing".

regards

I have a Win7 machine that prints to an HP printer that's connected to a Ubuntu machine.  I didn't do anything special to the 7 machine to get it to print other than going through the motions of installing a network printer on it.

> Windows has removed the Internet Printing Protocol from Windows 7.Does this prevent it from printing on a LAN?

I will say though, I've had to reboot the Ubuntu machine a few times and when I have to do it.... it's got the exact same symptoms the OP has.  Everything looks fine and dandy and then it doesn't print.

---

### Post by piquat on 2011-01-18
Hmmmm, Samba and CUPS.  Heh, I may have messed around with that a bit...

Try these two links, coincidentally, post #6 in both threads:

[http://ubuntuforums.org/showthread.php?t=1339956](http://ubuntuforums.org/showthread.php?t=1339956)
[http://ubuntuforums.org/showthread.php?t=1647954](http://ubuntuforums.org/showthread.php?t=1647954)

---

