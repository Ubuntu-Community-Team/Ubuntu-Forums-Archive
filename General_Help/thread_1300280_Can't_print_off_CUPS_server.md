---
title: "Can't print off CUPS server"
date: 2009-10-24
forum: General Help
---

### Post by Amstell on 2009-10-24
I have a Canon PIXMA MP490 connected to an iMac, which is running CUPS.  The printer works fine on the iMac and I can connect to it through the Printer Configurations dialog box in Ubuntu 9.10.  I am able to look at the properties of the printer, the ink level, and can even print a test page,  but I am unable to print from any program within Ubuntu.

How do I get the printer to show up in the dialog box whenever I print from Open Office, or Firefox?

Thanks for any help you can provide.

Cheers

---

### Post by Amstell on 2009-10-25
Bump

Anyone have any suggestions?

---

### Post by Queue29 on 2009-11-19
This is kind of late but maybe this will help: [http://bozosort.com/content/?p=19](http://bozosort.com/content/?p=19)

The GUI dialog is a useless POS. You have to add the ip address of the server to the client PC's cupsys config file, otherwise you can't actually print to the printer. The dialog only lets you do everything *except* add it as a printer.

---

