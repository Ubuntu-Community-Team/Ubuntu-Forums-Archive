---
title: "Can't access two different hard disks from ubuntu"
date: 2011-01-30
forum: General Help
---

### Post by vat with tux on 2011-01-30
I'm having two hard disks in my pc. I can easily access both of them from my windows. But in case of ubuntu i can access only that hard disk on which ubuntu is installed. The other hard disk can not be accessed from ubuntu. Why it is so? Please suggest some solution for this. 

Thanking in advance. :)

---

### Post by clhsharky on 2011-01-30
vat with tux

How did you install Ubuntu?
(inside windows or on its own partition)


Sharky

---

### Post by Rubi1200 on 2011-01-30
The best thing to do would be to show us the results of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Also, check your settings in BIOS to see which drive is set to boot first.

---

