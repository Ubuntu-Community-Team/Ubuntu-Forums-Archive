---
title: "Ubuntu software center never gets past &quot;waiting for apt-get to exit&quot;"
date: 2010-10-15
forum: General Help
---

### Post by Artemis Fowl on 2010-10-15
Whenever I attempt to install something ever sense I upgraded to maverick, ubuntu software center does not install and never gets past "waiting for apt-get to exit". This is very annoying. Please help me.

Edit:
Interestingly, terminal's apt-get still works. Go figure.

---

### Post by Artemis Fowl on 2010-10-15
Does anyone need any more details? This happens with all applications.

---

### Post by drs305 on 2010-10-15
Just to be sure, if you run "apt-get update" and "apt-get upgrade" everything is normal? How about installing something (I always use "sudo apt-get install 2vcard")? 

No error messages? And trying to open synaptic via command line (gksudo synaptic)?

---

### Post by VMC on 2010-10-15
> **Artemis Fowl said:**
> Does anyone need any more details? This happens with all applications.

Run it from a terminal and see what messages appear before and after you try to you it and then close it down.

From a Terminal:
```
software-center
```

---

### Post by DMaretta on 2010-10-18
Just running *sudo apt-get upgrade* from the terminal solved my problem.
Thanks for the tip.:)

---

### Post by janhalik on 2010-10-25
hi people,
apparently, i have the same problem. i tried your solutions as suggested, but i won't work for me. 
i tried to install new [Symphony ]("http://symphony.lotus.com/software/lotus/symphony/home.nsf/home")Office Suit. clicking on .deb file sends me straight to Ubuntu Software Centre but it gets stalled like this
[[IMG]http://img80.imageshack.us/img80/1753/screenshotkcs.th.png[/IMG]]("http://img80.imageshack.us/i/screenshotkcs.png/")


any ideas?
[URL="http://imageshack.us"]
[/URL]

---

### Post by jeremy.wn.shaw on 2010-11-02
This worked for me: [http://en.kioskea.net/faq/810-unblocking-apt-get](http://en.kioskea.net/faq/810-unblocking-apt-get)

---

### Post by davicus on 2011-01-03
I believe the problem is that apt-get is waiting for the cd-rom. From the terminal I got: 

Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

To fix this for the update manager you can edit your sources.list and remove (or map the cd-rom to the installation files), or open Synaptic, Settings, Repositories, Under the 'Ubuntu Software' Tab, Installable from CD-ROM/DVD section, uncheck the Cdrom with Ubuntu 10.10... entry. 

Rerun your update and it should work!

---

