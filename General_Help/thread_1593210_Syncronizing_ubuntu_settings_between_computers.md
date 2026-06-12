---
title: "Syncronizing ubuntu settings between computers"
date: 2010-10-11
forum: General Help
---

### Post by LonelyStar on 2010-10-11
Hi,

Is it possible to syncronize certain settings in ubuntu between several computers, such that when I change them on one they change on all?
If not, is it possible to at least use the settings of one computer as the initial settings of another?
These are the settings I am interested in:
- Keyboard shortcuts
- Compiz settings
- Statusbar configuration
- Theme

Thanks!
nathan

---

### Post by tafsen on 2010-12-11
I'm wondering the same thing.  Does anyone know how the keyboard shortcuts are stored?

---

### Post by MrFaler on 2010-12-11
You can use rsync to syncronise the config files over your network. Set up a script that automates the process.

Here is a man page, you might want to do some reading; [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)

EDIT: Of course I meant config files, sorry for any confusion.

---

### Post by tafsen on 2010-12-12
Do you know where the keyboard shortcuts is stored?

---

