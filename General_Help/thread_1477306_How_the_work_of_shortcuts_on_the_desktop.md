---
title: "How the work of shortcuts on the desktop"
date: 2010-05-08
forum: General Help
---

### Post by 0918028 on 2010-05-08
I want to create a shortcut on the desktop, such as that in Windows for example, documents, games, and Recycle Bin possible to tell me the way
Thank you...:p
[RIGHT] [/RIGHT]

---

### Post by Ms_Angel_D on 2010-05-08
What you want is a symbolic link. Grab the item you wish to create a shortcut to, then press-and-hold Ctrl+Shift. Drag the item to the location where you want the symbolic link to reside, and release.

(hold control+shift click on your documents folder and drag it to your desktop.)

---

### Post by WorMzy on 2010-05-08
To get the recycle bin, my computer, home folder, network folder and mounted partitions visible on the desktop, press Alt+F2 and run gconf-editor, browse to apps/nautilus/desktop, and check any boxes in there that you want. :)

To make an application launcher, right click on the desktop and choose "Create launcher".

---

### Post by DeMus on 2010-05-08
> **0918028 said:**
> I want to create a shortcut on the desktop, such as that in Windows for example, documents, games, and Recycle Bin possible to tell me the way
Thank you...:p
[RIGHT] [/RIGHT]

In your Application menu, in the Tools section is a program called Gconf-editor.
When you don't see it, right-click on the Applications menu and choose Edit menu. In the next Window open Tools on the left and fill the tick-box on the right where it says Configuration-editor. Close the Window.

Now open Application --> Tools Menu --> Configuration-editor.
Open, on the left, Apps, Nautilus, Desktop.
On the right you see a couple of tick-boxes you can select to have the system show on your desktop what you want to see.

---

