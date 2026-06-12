---
title: "Printer configuration files - where"
date: 2011-08-29
forum: General Help
---

### Post by bucz on 2011-08-29
Hi all

where are stored all the files with installed printers' configurations? I haven't seen anything like ~/.cups

---

### Post by Wayne_V on 2011-08-29
probably what you are looking for is in /etc/cups

You can see the packages related to cups with:

dpkg --list *cups*

and then the files in those cups with (for examplet):

dpkg --listfiles cups

---

