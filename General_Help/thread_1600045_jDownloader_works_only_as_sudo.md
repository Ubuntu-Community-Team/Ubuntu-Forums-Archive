---
title: "jDownloader works only as sudo?"
date: 2010-10-18
forum: General Help
---

### Post by StOoZ on 2010-10-18
I've installed jDownloader from the repositories, now when I click on the icon, it loads the java, but the program doesnt start.
when I go to the shell and type:
gksudo jdownloader

it works fine.

any idea?

---

### Post by spikoley on 2010-10-18
I am not familiar with jDownloader, but it sounds like it needs admin rights.  Where do you click on the icon?  You should be able to edit the command the icon uses.  If it is in the menu then right click on Applications and go to Edit Menus.  Find the launcher and edit the command.  If it is on the desktop then right click and go to properties.

What happens when you don't use sudo?  There might be something else going on with having to use sudo, but I don't know jDownloader.

---

