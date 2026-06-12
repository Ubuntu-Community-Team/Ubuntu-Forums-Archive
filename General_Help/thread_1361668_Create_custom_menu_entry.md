---
title: "Create custom menu entry"
date: 2009-12-22
forum: General Help
---

### Post by cdysthe on 2009-12-22
Hi,

This command opens a Windows program when I enter it in a terminal or as command for a desktop launcher:

 /opt/cxoffice/bin/wine "/home/user/.cxoffice/winxp/drive_c/Program Files/FamilyTree.exe"

How can I create a menu item that opens the program? I know how to use the menu editor and create tiems, but when I tried to simply use the same command in the command field it didn't work. I am giving the full path to wine since it's installed through Crossover Linux, but that isn't causing any problems since it works in the terminal. Do I need to add something else to the command in the menu editor to get it to work as a menu item?

---

### Post by starcraft.man on 2009-12-22
Hi, only thing I can think of is at top of launcher/entry editor change type to Application in Terminal. Then put the command back in the terminal.

Alternatively, right click on desktop and make a launcher of Type : Location and try.

---

### Post by audiomick on 2009-12-22
Hallo.
I did what I think you want to start synergy.

This doesn't add to a menu, it adds a starter to the panel, but I think it works for a menu too (see below)

You need to have you script ( your command ) saved somewhere where it wont move, and where you will be able to find it again in 18 months time when you have forgotten where you put it. I have a directory called

/home/myscripts

for instance.

The script needs to be saved as a .txt file. (use gedit, for instance, or vim or whichever text editor you prefer).

Give the file a name you will recognize in a year's time, e.g.
"start_that_tricky_program_in_wine"

In the properties (right click) of the file, third tab "permissions" check the box for "execute as a programm"


Then,

Right click in the panel, add a user defined starter, and point it at your script.

For the menus.
I haven't tried this, but it looks like it is the same in principle.

Right click on the menu, add entry, and point it at your script.

---

### Post by cdysthe on 2009-12-22
> **starcraft.man said:**
> Hi, only thing I can think of is at top of launcher/entry editor change type to Application in Terminal. Then put the command back in the terminal.

Alternatively, right click on desktop and make a launcher of Type : Location and try.

I can make a launcher without problems. It's getting an item in the menu that's the problem. Thanks!

---

### Post by cdysthe on 2009-12-22
> **audiomick said:**
> Hallo.
I did what I think you want to start synergy.

This doesn't add to a menu, it adds a starter to the panel, but I think it works for a menu too (see below)

You need to have you script ( your command ) saved somewhere where it wont move, and where you will be able to find it again in 18 months time when you have forgotten where you put it. I have a directory called

/home/myscripts

for instance.

The script needs to be saved as a .txt file. (use gedit, for instance, or vim or whichever text editor you prefer).

Give the file a name you will recognize in a year's time, e.g.
"start_that_tricky_program_in_wine"

In the properties (right click) of the file, third tab "permissions" check the box for "execute as a programm"


Then,

Right click in the panel, add a user defined starter, and point it at your script.

For the menus.
I haven't tried this, but it looks like it is the same in principle.

Right click on the menu, add entry, and point it at your script.


Thanks a lot, that worked even for the menu! Problem solved!:P

---

### Post by audiomick on 2009-12-22
Hallo.
Just tried it in the applications menu as I described in my last post. It worked. I now have a synergy starter in my applications menu.

edit: removing it again is just as easy...

---

