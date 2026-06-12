---
title: "Ubuntu UNR 9.10, A few issues"
date: 2009-10-31
forum: General Help
---

### Post by josh_moore on 2009-10-31
I wanted to get some advice on a few issues I am finding in UNR 9.10
Prior to this I was running UNR 9.04, this is a fresh install of 9.10 on a Dell Mini10v

1. A common keyboard shortcut that I like to set is for the Windows key to launch terminal. In 9.04 this was easily done in Keyboard Shortcuts under Preferences. However in 9.10, the Windows key itself is not accepted. It seems however that Windows key is used as a modifier Winkey+<x>, anyone know of a way to change that?

2. UNR Main Menu editor is not showing Favorites or Files & Folders so that those items in the UNR menu can be orginized., all other items within are displayed in the editor.

---

### Post by eac101 on 2009-10-31
1. A common keyboard shortcut that I like to set is for the Windows key to launch terminal. In 9.04 this was easily done in Keyboard Shortcuts under Preferences. However in 9.10, the Windows key itself is not accepted. It seems however that Windows key is used as a modifier Winkey+<x>, anyone know of a way to change that?
[B]
Try Alt-F2[/B]

2. UNR Main Menu editor is not showing Favorites or Files & Folders so that those items in the UNR menu can be orginized., all other items within are displayed in the editor.[/quote]

[B]I belive you just drag new apps into Favorites and to delete you Right-click to remove
[/B] 
Ed

---

### Post by josh_moore on 2009-11-01
eac101
What does alt+f2 have to do with the question of using the windows key as a shortcut button instead of a modifier?
And regarding the Favorites menu, UNR at least by default is not allowing to drag/drop icons around, you can however right click to add to favorites or right click to remove but that also is not what I had asked. I am looking for what was previously available in 9.04 through the Main Menu editor to organize what is in Favorites, as well as the Files and Folders menu item

---

### Post by ncweber on 2010-03-11
Any answers to this question?  I, too, would like to organize the icons in my Favorites menu.  Preferably in alphabetical order, with Web page favorites at the end of the list.

---

### Post by bone2006 on 2010-03-21
I would like to know as well

---

### Post by bone2006 on 2010-03-21
Figured it out, if you type in gconf-editor in the terminal, then edit from the menu and select find.  Type in favorite

It will take you to /apps/netbook-launcher/favorites

right click on the favorites on the right side and edit key.  Here you can rearrange the order.   You have to reboot for it to work though after you finish editing.

To add or remove items you can just right click on them while using the environment

Hope this helps somebody

---

### Post by ncweber on 2010-03-25
> **bone2006 said:**
> Figured it out, if you type in gconf-editor in the terminal, then edit from the menu and select find.  Type in favorite

It will take you to /apps/netbook-launcher/favorites

right click on the favorites on the right side and edit key.  Here you can rearrange the order.   You have to reboot for it to work though after you finish editing.

To add or remove items you can just right click on them while using the environment

Hope this helps somebody

Nicely done.  Thanks for cracking the case. :D

---

### Post by joopbraak on 2010-07-29
> **bone2006 said:**
> You have to reboot for it to work though after you finish editing.
Don't reboot, just open System, Administration, System monitor, select netbook-launcher and click "End process".

It will automatically restart. No need to close all your open programs.

---

