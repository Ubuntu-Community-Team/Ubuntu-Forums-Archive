---
title: "read only file"
date: 2011-11-17
forum: General Help
---

### Post by queenita on 2011-11-17
I am using ubuntu 10.10 and I have tried to edit a protected excel sheet which i copied from windows but I got a message 'read only file'. I tried the command chmod 755 to the directory containing the folder but i failed to make it able to edited,any help?

---

### Post by ksprasad on 2011-11-17
See the permission of that file: ls -l file.xls
If it still read only, try changing the permission of that file alone.
 
chmod 777 file.xls

---

### Post by Lars Noodén on 2011-11-17
> **ksprasad said:**
> See the permission of that file: ls -l file.xls
If it still read only, try changing the permission of that file alone.
 
chmod [s]777[/s] file.xls

[s]chmod 775 or chmod 755[/s] on the file is safer.  777 allows write access to anyone and that is a risk.

Edit: oops.  That should be 664 or 644, not 775 or 755.  Either way it's not going to help because the protection is at the application level.

---

### Post by haqking on 2011-11-17
Excel sheet protection is different to file read/write permissions.

or am i confused by the OP statement of protected ?

If it is a protected worksheet it is supposed to be read only and the file attributes do not effect the sheets protection mechanism

---

### Post by ksprasad on 2011-11-17
> **Lars Noodén said:**
> chmod 775 or chmod 755 on the file is safer. 777 allows write access to anyone and that is a risk.
 
Yeah right. Thanks for correcting :)
 
 
Regards,
ksprasad

---

### Post by dave0109 on 2011-11-17
Also, the execute bit isn't necessary for a spreadsheet file.

Mode 644 would be more appropriate, or just 600 if nobody else is allowed to read the file. ;)

---

