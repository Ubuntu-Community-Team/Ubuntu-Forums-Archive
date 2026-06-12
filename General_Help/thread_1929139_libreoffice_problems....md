---
title: "libreoffice problems..."
date: 2012-02-21
forum: General Help
---

### Post by watgrad on 2012-02-21
Hello - I need help with Libreoffice 3.5
I run ubuntu 11.10

When trying to save some files (in Impress) LibreOffice crashes.  When run from the terminal I get this error on the crash:
(soffice:5693): Gtk-WARNING **: Unable to retrieve the file info for `file:///home/leej/Desktop/NTIP/NTIP%20Numeracy%20Focus%202012': Error stating file '/home/leej/Desktop/NTIP/NTIP Numeracy Focus 2012': No such file or directory


Any suggestions about how to prevent / fix this issue?

---

### Post by roelforg on 2012-02-21
That's normal.
Just ignore it.
Thats a GTK-bug where it'll try to find some file info before saving a file whilst the file doesn't exist (like when saving new files).

It's not important.

---

### Post by watgrad on 2012-02-21
I would ignore it if I could - but LibreOffice crashes when it happens and won't save any file changes...

---

