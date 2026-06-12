---
title: "gnome-open and folders"
date: 2009-08-13
forum: General Help
---

### Post by drbcladd on 2009-08-13
(1) gnome-open, when given a folder (directory) name, attempts to open Brasero. Since the folder is not a Brasero project, error messages and the like follow.

(2) Symptoms showed up about four days ago. Looking at installation logs and trying to remember what, if anything, I did with packages at the beginning of the week, I don't see anything obvious. 

(3) Initially problem was noticed on the Places menu on the main menubar. Subsequent testing shows that it is gnome-open.

(4) So, the real question: where is gnome-open getting the folder/application association. I go into gconf-editor and search on Brasero (0 hits) and brasero (9 hits, all in key names for config keys for the application). 

Where the hell is the association stored? I can fix it if I can find the file. I am almost at the point to run a scan for the string in every file on the machine.

Thanks in advance,
-bcl

---

### Post by mc4man on 2009-08-13
Right click on any folder on your desktop (if you don't have any then create one) -> **properties** -> open with and set to nautilus or open folder

The line you may wish to look at is here (or fix there

```
gedit ~/.local/share/applications/mimeapps.list
```

inode/directory=

In most lines in mimeapps the first listed .desktop is the default, for "inode/directory=" it shouldn't be, but i remember that at various times in has been (intrepid, jaunty...?
Nautilus or open-folder should remain the default unless changed in properties as described


Edit: If for any reason you wish to edit in mimeapps.list keep to the formatting - all [COLOR="Blue"]whatever[/COLOR].desktop's entries end with a ; and no spaces between entries on any line

---

### Post by drbcladd on 2009-08-13
Thanks so much. I don't know if my setup is different than anyone else's but everytime I read in a thread about this that I should go to 

<right-click> Properties | Open With...

I kept opening the Properties dialog on the folder. Nothing in there about opening with. 

I went in to the file, clobbered the inode/directory line, and then Open With (on the context menu directly) did just what I wanted. Let me specify File Browser.

The previous value began with nautilus-folder-handler.desktop which, it appears, is not valid? That is, it fell through to the brasero entry after that (why it was associated at all is not clear but I assume it got touched when I upgraded brasero some time in the past).

Now has nautilus-browser.desktop and it seems to work like a charm. Thanks so much (I looked all through .gnome, .gtk2, .config; who'd have thought it was .local/share/applications...)

---

