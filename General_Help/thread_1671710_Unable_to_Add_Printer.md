---
title: "Unable to Add Printer"
date: 2011-01-20
forum: General Help
---

### Post by Dhrystone on 2011-01-20
Hi everyone,

I'm relatively new to Linux, and have Ubuntu 9.10 installed on my laptop.
I installed Samba, but haven't installed CUPS yet. I'm trying to get a Windows shared printer added, and am having issues.
I went into Server > Settings, and checked the box to publish shared printers. However, when I try to add the printer, I'm able to see the network the printer is attached to, but when I click the arrow to the left of the network name, the whole print window just disappears.
I'm at a loss for what else to try. Can someone please help me get this printer added? Not sure what I'm missing here.
Just an FYI: I'm in the process right now of upgrading to Ubuntu 10.04.

Thanks,

Dhrystone

---

### Post by MiKOTRON on 2011-01-20
Yeah you need CUPS to use your printer.

---

### Post by Morbius1 on 2011-01-20
(1) From the Ubuntu machine post the output of the following command:
```
smbtree
```(2) See if cups is running:
```
sudo service cups status
```If it's not running start it:
```
sudo service cups start
```BTW, Ubuntu should have installed cups automatically so if it's not installed you're a Debian user masquerading as an Ubuntu user ;)

---

