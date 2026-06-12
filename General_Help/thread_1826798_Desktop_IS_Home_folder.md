---
title: "Desktop IS Home folder??"
date: 2011-08-17
forum: General Help
---

### Post by gregdwulet on 2011-08-17
Hey, everyone.

I'm running 10.10 since I don't really want to deal with Unity and the new upgrades, and I'm for the most part comfortable where I am. Except one thing: when I upgraded from 10.04, I noticed that my desktop and home folders seem to have become the same.

What I mean by that is that all of my home folders are also displayed on the desktop. The "Desktop" folder inside my home directory is empty. When I delete a file/folder off of my Desktop, it also gets deleted from my home. WTH??

I've checked the Nautilus preferences, and the option to use the desktop as a home folder is disabled, so I'm very confused.

Thanks for the help.

---

### Post by nomko on 2011-08-17
Check this:
Go to Applications > System tools > Gconf-editor
Then go to /apps/nautilus/preferences
In the screen on the rigth look for something called Homefolder as desktop and uncheck that line.

---

