---
title: "Printing pages in reverse order on Canon printer"
date: 2009-11-09
forum: General Help
---

### Post by sunbird on 2009-11-09
Hi all,

I've got a MP160 printer which works great, except that I can't get it to print in reverse order. I tried the suggestion in [this thread]("http://ubuntuforums.org/showthread.php?t=263820"), which was to add the following to the .ppd file:

```
*DefaultOutputOrder: Reverse 
```

But I think that may be Brother specific.

Any ideas?

---

### Post by grandtoubab on 2009-11-09
maybe have a look in cups manual
[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

and manage the printers with browser interface
[http://localhost:631/](http://localhost:631/)

---

### Post by sunbird on 2009-11-09
Yeah, I checked the localhost config and there is no option for reverse page order. Also read the manual (well, okay, I didn't read it cover-to-cover, but I searched through it)... no dice.

---

### Post by sunbird on 2009-11-10
I browsed around and found the way to fix this. As root::

```
# lpoptions -o outputorder=reverse
```

This will also have the effect of creating or editing the file /etc/cups/lpoptions to set this option as the default for all users on that machine. 

If you prefer GUI, you can accomplish the same result in Gnome by going to System->Admin->Printing, then selecting the printer, then Job Options, then scroll to the bottom and type outputorder in the Other Options field and click add, then type reverse in the new dialog box that appears and click apply.

---

