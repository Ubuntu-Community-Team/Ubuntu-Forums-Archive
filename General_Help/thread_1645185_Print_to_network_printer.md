---
title: "Print to network printer"
date: 2010-12-14
forum: General Help
---

### Post by domtom on 2010-12-14
I have a Lexmark Z600 connected to a laptop running Puppy Linux, it prints fine from the laptop and I  would like to print to it from my Ubuntu 10.10 desktop. Cups on the Puppy laptop is set to publish and share local printers.

On the desktop I tried System-Administration-Printing-ADD-Network printer and pointing it at the IP number of the laptop. It detects the host and queue (CUPS-PDF) but not the printer by name. It then takes me into detecting a driver, but I don't have a driver that works and I'm not sure why I need one, the laptop is handling that OK, so I chose Generic Postscript. 

Test pages don't print although they do show up as completed jobs in Cups on the Puppy laptop, so maybe its just a question of choosing the right driver on the Ubuntu desktop?

---

### Post by tredegar on 2010-12-14
My printer is working. The IP of the machine it is connected to is 10.0.0.6 and it is running CUPS.

So I just connect to the printer  (System, Admin,Printing,New) using **ipp://10.0.0.6:631/printers/HPLaserJet6P**

Hope this helps.

---

### Post by domtom on 2010-12-14
I tried to direct it like that i.e. **ipp://192.168.1.65:631/printers/Lexmark_Printer** which is how its known on the server machine but Ubuntu said something like 'no printers found'.

---

### Post by tkoco on 2010-12-14
> **domtom said:**
> I tried to direct it like that i.e. **ipp://192.168.1.65:631/printers/Lexmark_Printer** which is how its known on the server machine but Ubuntu said something like 'no printers found'.

Try this thread:
[http://ubuntuforums.org/showthread.php?t=1538231](http://ubuntuforums.org/showthread.php?t=1538231)

Good Luck!

---

