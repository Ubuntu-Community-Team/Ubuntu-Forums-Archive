---
title: "Stopping GRUB2 from updating the list on update"
date: 2011-03-17
forum: General Help
---

### Post by nkae100 on 2011-03-17
Is there a way to stop GRUB2 from updating grub.cfg with new entries after an update? It shits me because it goes and writes over all my custom modifications of current entries.. e.g:

"Windows 7 Home Premium" (which I made), gets changed back to:

"Windows 7 (loader) (/dev/sda2)"

ANNOYANCE!!

---

### Post by blueridgedog on 2011-03-17
You could create a custom entry:

[https://help.ubuntu.com/community/Grub2#Custom Menu Entries](https://help.ubuntu.com/community/Grub2#Custom Menu Entries)

Then place it higher on the menu:

(from the same help page)

> The placement of the menu items in the grub.cfg menu is determined by the order in which the files in this directory are run. Files with a leading numeral are executed first, beginning with the lowest number. 10_linux is run before 20_memtest, which would run before 40_custom. If files with alphabetic names exist, they are run after the numerically-named files.

Custom entries can be added to the 40_custom file or in a newly created file. Based on its name, 40_custom entries by default appear at the bottom of the menu. A custom file beginning with 06_ would appear at the top of the menu since its alphanumeric sorting would place it ahead of 10_ through 40_ files.

So, if you made a a custom file called 09_Windows, it would show up early in the menu and get re-made with each update.

---

### Post by nkae100 on 2011-03-17
Thank you my friend. You have been a help.

---

