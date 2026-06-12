---
title: "Printing using Printer on Windows"
date: 2011-05-01
forum: General Help
---

### Post by monkeychef on 2011-05-01
Hi Everyone,

So I just installed 11.04 on an old Compaq tower and I am having some trouble connecting to a printer on the network. I have tried looking for some type of guide/tutorial or any other type of help, but it is all very old, and many of the guides don't make much sense.

BTW, I am fairly new to Ubuntu. The most I did was compile a kernal for a wireless card driver in an old laptop, and that took FOREVER.

Any type of help is gladly appreciated. If it really comes down to it, then I'll just keep switching the cable between the computers (but I would really rather not).

Setup:
Compaq 5000 Tower running 11.04
HP D4200 connected to Win 7 Home Edition custom Tower
All through Netgear router (the connection between the two computers is not wireless however).

Thanks.

---

### Post by marshag63 on 2011-05-01
Please describe your setup - is the printer attached to another computer?  If so, what operating system is it running.  Will you be accessing this printer wirelessly?

Once we have these details, we can better help you.

MDG

---

### Post by monkeychef on 2011-05-01
> **marshag63 said:**
> Please describe your setup - is the printer attached to another computer?  If so, what operating system is it running.  Will you be accessing this printer wirelessly?

Once we have these details, we can better help you.

MDG
 Wow, don't I feel like an idiot. I post problems all the time, and this just happens to be the one that I forget to post my setup. Sorry, I'll edit the first post.

---

### Post by marshag63 on 2011-05-01
In Windows 7, I'm guessing you made the computer available as a network printer (sorry I only have windows 7 Starter).  On your Ubuntu computer, you need to tell cups to check for network printers.

.... grabbing my windows 7 Starter netbook to check settings.  I don't have a printer actually attached to my windows 7 starter netbook - I use wireless network. (Menu > Administration > Printing > Server >  Settings > "Show Printers Shared By Other Systems"

MDG

---

### Post by monkeychef on 2011-05-01
Alright, I guess I'll keep trying my luck or someone else will attempt to help. Thanks anyway.

---

### Post by marshag63 on 2011-05-01
This says for "vista" but it appears it will work in Windows 7 (i found it on my windows 7 starter netbook)

[http://windows.microsoft.com/en-US/windows-vista/Share-a-printer](http://windows.microsoft.com/en-US/windows-vista/Share-a-printer)

Then do this: I know its says XP - but it too works.

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Good luck!

MDG

---

### Post by monkeychef on 2011-05-01
That was the first thing I did. smb worked up to the point when I needed to enter my authorization password (I assumed it was my workgroup password) but the password didn't work. I tried to use the LPD method, but it completely lost me.

---

### Post by marshag63 on 2011-05-01
[http://superuser.com/questions/227635/accessing-windows-7-printer-from-ubuntu-linux-via-lpr-lpd-or-samba](http://superuser.com/questions/227635/accessing-windows-7-printer-from-ubuntu-linux-via-lpr-lpd-or-samba)

MDG

---

