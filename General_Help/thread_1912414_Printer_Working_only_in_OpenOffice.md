---
title: "Printer Working only in OpenOffice"
date: 2012-01-20
forum: General Help
---

### Post by fl0at on 2012-01-20
Good afternoon all,

I set up a new printer (Brother HL-2270DW), which is on the network.  I'm using CUPS, and I show the printer within System>>Administration>>Printer.  I have it set as server default, all users may access, and everything works perfectly.  I am able to print a Test Page and I can even print in OpenOffice.

The problem is that all other print dialogs do not see the printer, and can only print to file.  This is true for DocumentViewer, gedit, Firefox... anything and everything except OpenOffice.

Have I got a setting off or what?  Why is the printer only showing up in OpenOffice?

Running Ubuntu 10.04 LTS and Gnome 2.30.2.

Thanks much.

---

### Post by fl0at on 2012-01-20
I found the answer.  I didn't have the printer published.  Under System>>Admin>>Printing, I had to click Server>>Settings and Publish.

---

