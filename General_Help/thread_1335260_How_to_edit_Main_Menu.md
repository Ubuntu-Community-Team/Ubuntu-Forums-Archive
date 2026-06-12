---
title: "How to edit Main Menu"
date: 2009-11-23
forum: General Help
---

### Post by acroporas on 2009-11-23
How do I edit the items in the Main Menu without the GUI tool(System/Preferences/Main Menu)?  What file are the menu items stored in?

Here's my problem.  I tried adding an item to the Main menu with the GUI tool.  But it did not work.  I click OK, and it does not show up in the Main Menu Tool, or in the Main Menu.  I just assume that the add item to menu feature did not work and moved on.

But then today I installed GnoMenu and that item I had tried to add to the menu shows up in the GnoMenu....Well I don't want it there any more.  But since the item does not show up in the Main Menue editing program I can not delete it.  So I want to find the file where the menu items are stored and edit it directly.

---

### Post by Sam on 2009-11-23
Systemwide launchers are stored in /usr/share/applications
Per-user lauchers are stored in ~/.local/share/applications

The files you looking for are *.desktop.

---

### Post by acroporas on 2009-11-23
Thanks.

---

### Post by BFG on 2009-12-22
> **Sam said:**
> Systemwide launchers are stored in /usr/share/applications
Per-user lauchers are stored in ~/.local/share/applications

The files you looking for are *.desktop.

That's useful.  But where is the structure held?
My "Other" folder is messed up after a fresh install of 9.10.
(My user folder is on a network share)

---

