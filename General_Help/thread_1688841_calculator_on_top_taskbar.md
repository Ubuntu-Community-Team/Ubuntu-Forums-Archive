---
title: "calculator on top taskbar"
date: 2011-02-15
forum: General Help
---

### Post by tobydog on 2011-02-15
hi i cannot work out how to get the calculator icon on my top taskbar so i can access it fast from there, i know that with ubuntu you right click on it and add to taskbar, this doesnt seem to do it with xubuntu, i cannot work out how to do it , would be greatful of any help.

---

### Post by thefasterblueone on 2011-02-15
Have you tried dragging it from your menu to the taskbar?
Also right clicking calculator in the menu might bring up some options.

---

### Post by tobydog on 2011-02-16
tried all this no luck still cannot get it in taskbar

---

### Post by anglican on 2011-02-16
> **tobydog said:**
> tried all this no luck still cannot get it in taskbarRight click on the panel and choose:
> Add New Items...
Select the first option "Launcher" and choose "Add" then in the window enter:
> Name: Calculator
Description: Desktop calculator
Command: /usr/bin/gcalctool
Click on the Icon to choose a suitable icon for the calculator. That should do it.

H

---

### Post by tobydog on 2011-02-16
worked a treat thanks , can i ask how i would find the command details for the calculator if i don't know it , i would never have found this if you hadn't told me

---

### Post by anglican on 2011-02-16
> **tobydog said:**
> worked a treat thanks , can i ask how i would find the command details for the calculator if i don't know it , i would never have found this if you hadn't told meI just ran the calculator from the menu and looked at Help->About to see which was the default Xubuntu calculator. However you could also try ```
man -k calculator
```which may show other installed calculators e.g. xcalc or gnome-calculator. To get the full path you can then use ```
which xcalc
```- though mostly applications are in /usr/bin.

H

---

