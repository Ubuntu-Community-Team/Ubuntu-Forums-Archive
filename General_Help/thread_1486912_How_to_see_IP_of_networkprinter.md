---
title: "How to see IP of networkprinter"
date: 2010-05-18
forum: General Help
---

### Post by rasmus91 on 2010-05-18
Hi There

I need to locate the IP of a network printer, as i need to add it to my Ubuntu computer. 

Unfortunately the only computer i have access to, with connection to the printer run windows 7. And i have no idea how to obtain some real information from this computer.

Please tell me how to get this.

Thanks Rasmus

---

### Post by AshRice on 2010-05-18
Try printing a test page. That has the IP address on it. At least it did in XP.

---

### Post by howefield on 2010-05-18
If that doesn't work, try logging into your router and find the attached devices in the configuration pages.

Some network printer models can display and print the network settings ?

---

### Post by wired99 on 2010-05-18
You can also find the info with "Windows Explorer"
just navigate to the "Network" and find the printer,
then select "Properties" for the printer, it should give you the info you need

Or even look under "Control Panel > Hardware and Sound > Devices and Printers" and find the printer, then select Printer Properties and you should have the info as well

---

### Post by rasmus91 on 2010-05-18
> If that doesn't work, try logging into your router and find the attached devices in the configuration pages.


Router stuff won't work, School.

> Or even look under "Control Panel > Hardware and Sound > Devices and Printers" and find the printer, then select Printer Properties and you should have the info as well 

Sorry, tried it, it doesn't quite work.

> Try printing a test page. That has the IP address on it. At least it did in XP. 

ah, simple. will try.

---

### Post by sgosnell on 2010-05-18
If you have physical access to the printer, it should tell you via the menus on the printer itself, usually under "Network" or some such.

---

### Post by rasmus91 on 2010-05-19
> If you have physical access to the printer, it should tell you via the menus on the printer itself, usually under "Network" or some such.

Tried it, it didn't work, as this is a crappy Konica Minolta.

Well, i've succeeded in finding the printer at: smb://thiusr2/Mita_HTX

My computer find the printer and everything, only one problem: it needs authentication to print. now this shouldn't be a problem, because i have a user name and password to the network, and there by also to the printers, but it doesn't it just kep throwing this authentication window at me.

Im so annoyed by this, can anyone tell me what i may be doing wrong?

---

### Post by sgosnell on 2010-05-19
Ask the admins at the school.  They should be able to give you the password.

---

