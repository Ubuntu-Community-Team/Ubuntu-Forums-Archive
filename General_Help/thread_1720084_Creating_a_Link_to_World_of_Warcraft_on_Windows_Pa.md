---
title: "Creating a Link to World of Warcraft on Windows Partition?"
date: 2011-04-02
forum: General Help
---

### Post by swatto on 2011-04-02
Hey all,

I have a bit of a problem that I don't understand and would like some help please - I will try and explain the best way I can.

I installed Ubuntu using the WUBI installer and so I can access my Windows partition in /host.

Using Wine I can run World of Warcraft by going to /host/Program Files/World of Warcraft/WoW.exe

But I would like to create a link on my desktop to that file so I do not have to keep going to that path everytime. 

The Problem - when I click make link and drag it to my desktop I double click the file (expecting it to just act like a windows shorcut) but it doesn't - it creates some of the files that are in the world of warcraft folder on the desktop and then fails to open with message: Failed to open archive data\art etc...its like it is creating a copy of files on my desktop of what is already in the WoW folder. 

I hope I explained that clearly enough - please could you help me understand why this happens?

Thanks for any help you can give :)

---

### Post by swatto on 2011-04-03
Bump :)

Anyone know why this would happen and why a symlink won't just act like a normal launcher shortcut in Gnome?

---

### Post by skyline-racer on 2011-05-05
My advice is DONT!

You might run into unexpected errors when trying to run games off your windows partition. Copy your WoW Folder over into your home directory on your linux install.

Much safer.

---

