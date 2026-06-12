---
title: "How to use Windows Printer from Ubuntu?"
date: 2010-03-04
forum: General Help
---

### Post by karthick87 on 2010-03-04
My printer is attached to a Windows machine which runs Windows XP and the other  system runs Ubuntu 9.04..I want to use that printer in my Ubuntu machine..So wat are all the steps to be followed to access my Windows printer from Ubuntu?

---

### Post by halj32 on 2010-03-04
How about some info???
what printer are you using, with out this info no one can help

---

### Post by karthick87 on 2010-03-04
HP Deskjet 3940

---

### Post by jhoney142 on 2010-03-04
Hi,
  please check this link
   [http://www.crn.com/software/223100831;jsessionid=BODMOABHXIWXHQE1GHPCKHWATMY32JVN](http://www.crn.com/software/223100831;jsessionid=BODMOABHXIWXHQE1GHPCKHWATMY32JVN)

---

### Post by Morbius1 on 2010-03-04
From the Ubuntu end:
Go to System > Administration > Printing > Click "New Printer" > Select "Windows Printer via SAMBA". 

Now enter your Windows machine name or IP address in the box  titled "smb://". Click the "Browse" button.

If it can't browse to it then enter the entire path to the Windows Printer. For example:

[COLOR=Black][WORKGROUP_NAME/MACHINE_NAME/WinPrinterName]("smb://workgroup_name/MACHINE_NAME/WinPrinter")
[MACHINE_NAME/WinPrinterName]("smb://machine_name/WinPrinter")
[192.168.0.100/WinPrinterName]("smb://192.168.0.100/WinPrinter")

All of this presumes you have enabled printer sharing on the WinXP box of course.
[/COLOR]

---

