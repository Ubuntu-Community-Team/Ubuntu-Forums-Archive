---
title: "CUPS pdf printing is broken!"
date: 2010-12-19
forum: General Help
---

### Post by zenon222 on 2010-12-19
I can't print to pdf through the "cups-pdf" print module.  Here is my error logfile:

```
@ubuntu:/var/spool$ cat /var/log/cups/error_log
E [19/Dec/2010:20:52:44 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:11 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:19 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:27 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:34 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:43 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:53:52 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:54:01 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/Dec/2010:20:54:07 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
```Any ideas??

---

### Post by tgalati4 on 2010-12-20
Do you have file called sample.drv at that location?  Is it really bad or just missing?

Sometimes you can just delete the cups-pdf printer through the print management panel then add a new printer and select Print-to-File or CUPS-PDF, Generic-PDF, Print_to_PDF, etc.  Different versions of CUPS have different names for the same functionality.

---

### Post by wojox on 2010-12-20
What printer is it?

---

### Post by Yetisaurus Akjas on 2012-07-04
'Got rid of that message by simply copying the .ppd file assiged to the printer as the sample.drv file where the error message points, but that does not solve the problem, unfortunately - it is not printing anymore any PDF files. :))

---

### Post by nothingspecial on 2012-07-04
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

