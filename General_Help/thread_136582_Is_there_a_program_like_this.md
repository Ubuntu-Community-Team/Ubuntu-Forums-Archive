---
title: "Is there a program like this?"
date: 2006-02-26
forum: General Help
---

### Post by IYY on 2006-02-26
In Gnome/KDE it's possible to click on a file and have it opened with a default application. Is there a way to do this from the terminal?

Something like "open file.pdf" will launch xpdf, and "open file.txt" will launch vim.

---

### Post by Xian on 2006-02-26
[QUOTE=IYY]Is there a way to do this from the terminal? Something like "open file.pdf" will launch xpdf, and "open file.txt" will launch vim.[/QUOTE]

From a terminal just preface the file name with the preferred application.
Example:

$ vim /usr/share/<filename>

You will need to at least provide the program name....

---

### Post by huckem on 2006-02-26
you can change file opening options by right clicking a file, going to properties, and change the 'opens with' option to whatever prog. you want to use for that type of file.

---

### Post by engla on 2006-02-26
Ok, what you want is called gnome-open in Gnome (I have no clue about KDE)

So
$ gnome-open file.txt
opens that file in your default text editor.

Yes, it could be nice to use an alias, I aliased gopen to that command.

---

