---
title: "Link opens file in read-only mode how do I change this"
date: 2010-04-18
forum: General Help
---

### Post by DrScum on 2010-04-18
I create a link to a file in order to open the file from the desktop. When I move the link from the file location to the desktop, the file is opended in read-only mode. How can I change this so that the file opens in regular mode so that I am able to edit contents?
The file in question is an open office spreadsheet.

---

### Post by bobcollard on 2010-04-18
> **DrScum said:**
> I create a link to a file in order to open the file from the desktop. When I move the link from the file location to the desktop, the file is opended in read-only mode. How can I change this so that the file opens in regular mode so that I am able to edit contents?
The file in question is an open office spreadsheet.
Find the file in your File Manager, right click it and open a link in Desktop, see screenshot.

---

### Post by DrScum on 2010-04-19
When I right click the file the selection of options I get is different from what is shown in your screenshot (I am using 9.04, maybe that's the reason). When I select "send to" I don't have the "create link" option.
When I create a shortcut via "create link" from the menu popping up upon right click, it works fine as long as it is in the same folder than the original file. 
As soon as I drag it to the desktop, it opens the original file in "read only" mode. Very strange behaviour!

---

### Post by bobcollard on 2010-04-19
> **DrScum said:**
> When I right click the file the selection of options I get is different from what is shown in your screenshot (I am using 9.04, maybe that's the reason). When I select "send to" I don't have the "create link" option.
When I create a shortcut via "create link" from the menu popping up upon right click, it works fine as long as it is in the same folder than the original file. 
As soon as I drag it to the desktop, it opens the original file in "read only" mode. Very strange behaviour!
Leave the original link in the folder, copy it to clipboard 
```
Ctrl C
```Then paste it to your Desktop.
```
Ctrl V
```

---

### Post by akakingess on 2010-04-19
I don't seem to have that problem on 9.10, but have you right-clicked on the file on the desktop and checked the permissions tab to make sure that everything is in order (i.e. that you the owner of the file have r/w permission)? That's the only other thing that I would check.

---

### Post by DrScum on 2010-04-19
Meanwhile I found the problem:
there was a lock file for the file I was creating a shortcut for on the desktop.
This probably was saved when the machine went into an irregular shutdown which sometimes happens when I close the lid of the laptop. OpenOffice crashed and the lock file remained there since it's a hidden file you only see it when you make hidden files visible.

Thanks for all the help guys.

---

