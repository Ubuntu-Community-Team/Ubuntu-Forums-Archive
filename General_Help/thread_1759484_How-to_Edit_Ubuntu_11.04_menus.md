---
title: "How-to: Edit Ubuntu 11.04 menus"
date: 2011-05-15
forum: General Help
---

### Post by malleus74 on 2011-05-15
Like many others, I've been irritated that I can't customize my menu in 11.04 or change which program is used for what extension. After not finding a satisfactory solution on the forum:

I opened a Terminal, and typed in 'alacarte'. This brought up the menu-editor. I attempted to edit the menu, and it gave me an error to work with: ./local/share/applications already exists.

I made a copy of the file, and deleted the original. Apparently it recreated the file correctly after right-clicking on the menu, and choosing to edit it. This allowed me to change my menu, edit what applications I use to open extensions, and the like.

---

### Post by wildmanne39 on 2011-05-16
> **malleus74 said:**
> Like many others, I've been irritated that I can't customize my menu in 11.04 or change which program is used for what extension. After not finding a satisfactory solution on the forum:

I opened a Terminal, and typed in 'alacarte'. This brought up the menu-editor. I attempted to edit the menu, and it gave me an error to work with: ./local/share/applications already exists.

I made a copy of the file, and deleted the original. Apparently it recreated the file correctly after right-clicking on the menu, and choosing to edit it. This allowed me to change my menu, edit what applications I use to open extensions, and the like.
Hi, thank you for that information it is very useful.:)

---

### Post by Pa^2 on 2011-09-23
I am not sure if this is the correct approach but I found that ~/.config/menus was owned by root.  I chown'ed it and the contents to my username.  Now I am able to edit the menus.

chown -R <username>:<username> /home/<username>/.config/menus 

The "-R" recursively chown's all of the directories and files inside ...menus.

(Please don't flame me if this isn't the correct approach.  I am just an Ubuntunoobie.)

---

