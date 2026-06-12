---
title: "Configure Scanner"
date: 2010-10-23
forum: General Help
---

### Post by gjohnno on 2010-10-23
Hello I have just install the drivers for my Brother DCP-J315W . Printer , Copier, Scanner combo. That part of the process I have had not problems . The printer and copier are working . However the the scanner is not working . i have gone back to the Brother.com.au website and I found that I have to add two (2) additional lines in /lib/udev/rules_d/libsane.rules. I open this file type in the two (2) lines required . When I go to replace the original file by "Save As" , the system says I have not got permission, even though I am the administrator. Is there something I am doing wrong or perhaps there is something wrong in my administration setting that is causing the problem. Your assistance is very much appreciated

---

### Post by todak on 2010-10-23
According to the title bar in your screenshot, the file is opened as "Read Only", which means you are trying to save it as a regular user. This command will let you open, modify and save the file with administrative priveleges: ```
gksu gedit <location/and/name/of/file/here>
```

---

