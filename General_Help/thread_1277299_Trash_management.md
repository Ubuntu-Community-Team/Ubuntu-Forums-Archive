---
title: "Trash management"
date: 2009-09-28
forum: General Help
---

### Post by alawson on 2009-09-28
Hi all,

I have Ubuntu Jaunty installed on my media box. Recording from live TV to MPEG-2 generates quite a few multi-gigabyte files. Once I've watched these programs, I delete the file.

Fairly infrequently I forget to empty trash and the disk fills up and I miss stuff.

Is there a way to turn off trash, so files are just deleted?
Or a way to automatically purge the trash?

I tried trash-cli, but that doesn't seem to work. Having installed the package, I'm unable to run it from the command line. I though I could then use cron to kick off "trash-empty" at timed intervals and clear everything out.

Thanks for your help!

---

### Post by ankspo71 on 2009-09-28
Hi,

I turn it off in the Gnome configuration editor.

It is hidden in your start menu by default, so you can either unhide it, or type the following in the terminal...
```
gconf-editor
```
After it opens, find your way to:
Apps > Nautilus > Preferences, then tick the box next to "enable_delete"

I hope that is what you are looking for. Btw, leave "confirm trash" enabled so you don't accidentally delete anything. Also "Move to trash" will still be there in your right click menu, but "delete" will be right under it.
James
Edit: fixed typo

---

### Post by pmlxuser on 2009-09-28
you could also just write a script to delete files in the trash at the end of the week

do bolean valuing, if its 7 days gone since last delete if yes delete items in trash....

---

### Post by sideaway on 2009-09-28
Use cron to empty trash every 6 (or however many you wish) hours or so?

---

### Post by wojox on 2009-09-28
Another option is use Shift + Delete to automatically delete a file.

---

