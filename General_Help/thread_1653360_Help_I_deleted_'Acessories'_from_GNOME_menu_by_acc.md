---
title: "Help I deleted 'Acessories' from GNOME menu by accident :("
date: 2010-12-26
forum: General Help
---

### Post by aCsbD6N5xj on 2010-12-26
Hello.

Like the title suggests, I accidentally deleted the 'Accessories' sub-menu from the 'Edit Menu' menu.

Is there an easy way to recover the shortcuts from that sub-menu without re-creating everything from scratch? I don't even remember all the apps that were in there.

Thanks!

---

### Post by aeronutt on 2010-12-26
If you're willing to reset them all to default, this works. There's probably a better way someone else may have, that just adds your accessories menu.

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by wojox on 2010-12-26
revert didn't do anything?

---

### Post by aCsbD6N5xj on 2010-12-26
@aeronutt: Wow Amazing! Thanks!

It even kept additional stuff I added on my top panel and how I arranged them!


@wojox: No, 'Revert' didn't do anything :(

---

### Post by Brandel Valico on 2010-12-26
[http://ubuntuforums.org/showthread.php?t=554585&page=3](http://ubuntuforums.org/showthread.php?t=554585&page=3)

---

### Post by WorMzy on 2010-12-26
Your menu changes are stored in ~/.local/share/applications and ~/.local/share/desktop-directories

Remove both of these folders (and their contents) to revert _**all**_ changes.

---

### Post by Kalimol on 2010-12-31
Brandel Valico wins. Restored my Gnome Menu and Alt+F2 application list after I accidentally deleted my Office category and any and all Office apps I attempted to install were invisible to both. I tried and failed to just copy over the Office part of the file, but replacing the whole file with the default list from /etc/ of course included every installed application. Nice work!

---

