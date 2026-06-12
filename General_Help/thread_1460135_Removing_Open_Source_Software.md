---
title: "Removing Open Source Software"
date: 2010-04-22
forum: General Help
---

### Post by odiear3rd on 2010-04-22
I want to know how to remove unwanted Open Source Software not listed in Ubuntu Software Center. I tried to used Add/Remove Program. That did not work for me. Anyone have any suggestions. Thanks for your help.

---

### Post by SnickerSnack on 2010-04-22
How did you install it?

If you compiled from source using 'make install', then you can go to the directory where the make file is and you should be able to use 'make uninstall'.

If you got it from Sourceforge, then you should look through the page there to see if there are special instructions.  You might have to send an email to the person(s) who made the software and ask how best to remove it.

Unlike windows, there is no "registry", so if all else fails, you can just delete the program's files.

---

### Post by scottiw2000 on 2010-04-22
The simplest way is to open Synaptic Package Manager and do a quick search for the software name. Then just select the package for the software in question and select "uninstall" or "remove" from the menu that appears and click the "apply changes" button. 

Usually any closely related packages (components of the software, resource packages, etc.) will also be removed automatically. Synaptic will warn you if it will remove other packages and give you a chance to confirm.

In a few cases (like openoffice) it can be confusing to know which package to remove. If in doubt, just ask here.

---

### Post by odiear3rd on 2010-04-22
Thanks for your posts. Synaptic Package Manager Worked in getting rid of the unwanted software.

---

