---
title: "I have an HP deskjet 932C printer and I am having trouble getting it to print."
date: 2011-03-27
forum: General Help
---

### Post by mitchelljj on 2011-03-27
I have an HP deskjet 932C printer and I am having trouble getting it to print.  I went through the normal process of system->administrator->printing and then choose New Printer then Forward and then Apply, but it will not print anything.
Any suggestions?

---

### Post by linuxuser12345 on 2011-03-27
Install the HPLIP Toolbox from the Ubuntu Software Center

---

### Post by Mark Phelps on 2011-03-28
Open a web browser, enter "localhost:631:".  That will start CUPS.

Follow the menus and select the option to add a printer.  When it gets to the model, enter the make and model, and see if their is a CUPS driver for it.  

I have an HP 960 and was able to do this the same way by selecting the CUPS driver for the printer.

---

