---
title: "Printers disappeared after update"
date: 2010-05-11
forum: General Help
---

### Post by Warthaug on 2010-05-11
I installed ubuntu 10.04 just after the first release was available.  I configured everything - including my printers - and all was working 100% perfectly.  Last friday (or perhaps thursday) I did the first update (it was big, ~60megs), and since then I have lost my printers.  They are no longer listed on the "Printers" information panel.

In fact, I can no longer add printers (the option is grayed out).  In fact, the only option I can select is the connect to server.  If I try local, I get the error that the server cannot be found.

Any ideas what happened, and how I can fix it?

Thanx

Bryan

EDIT: the original printers are networked printers, accessed via an IP address.

---

### Post by anglican on 2010-05-11
> **Warthaug said:**
> I installed ubuntu 10.04 just after the first release was available.  I configured everything - including my printers - and all was working 100% perfectly.  Last friday (or perhaps thursday) I did the first update (it was big, ~60megs), and since then I have lost my printers.  They are no longer listed on the "Printers" information panel.

In fact, I can no longer add printers (the option is grayed out).  In fact, the only option I can select is the connect to server.  If I try local, I get the error that the server cannot be found.

Any ideas what happened, and how I can fix it?

Thanx

Bryan

EDIT: the original printers are networked printers, accessed via an IP address.
Grayed out "Add printer" and failure to connect to server seems to be telling you that cups isn't running. The package may need reconfiguring, but you could try just starting it with:

```
sudo service cups start
```Otherwise, to reconfigure:

```
sudo dpkg-reconfigure cups
```H

---

### Post by Warthaug on 2010-05-11
angelican, that did the trick (the reconfigure).  Thanx a million!


Bryan

---

### Post by satyamo on 2010-05-18
Thank you! Got exact the same problem! For me your
sudo service cups start

was the solution!

---

### Post by mickier on 2010-05-25
well for me, every time I hook up my hp 2660 (usb) cable, there's no printer - it's just gone...

the restart cups does work, but only until "tomorrow" then I have to do it again... (!)

didn't have this problem with 9.04 or 9.10... :confused:

---

### Post by Georgia boy on 2010-05-27
I have a HP PSC 750. Just did the update. Printer showed back up. Didn't show this morning. So will monitor and see how long this lasts.

Thanks everyone!

Tom

---

### Post by dcviana on 2010-07-20
Same problem here, have Lucid with the latest updates as of july 20 but sometimes the printers disappear. Restarting cups does solve it but why is it not starting (or starting but stoping) in the first place?

---

### Post by joshzam on 2010-08-06
Was surprised to find my printer missing, as well. The "sudo service cups start" solved it right away. Thanks!

---

### Post by mbergandi on 2011-03-16
This bug has been reported here:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/577859](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/577859)

Please take a moment to visit that page and at a minimum click here: ["This bug affects you and XXX other people"]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/577859/+affectsmetoo") or the same link at the top that page. You will be asked if it affects you as well and can click the appropriate response so that this bug will get assigned and fixed. 

You can also post more information or just a statement of support as well as subscribe to get notifications of activity and status info on this particular bug, if you so desire.

Ubuntu put this system in place for us to use to help them create a better product for us. 

Let's use it!

---

