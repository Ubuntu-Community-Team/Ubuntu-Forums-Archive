---
title: "Help....Archive type not supported...???"
date: 2011-01-09
forum: General Help
---

### Post by robertcoulson on 2011-01-09
I can not get into "Places" menu to see desktop, pictures , downloads, etc...Don't know what is going on...
Please see attached picture....Any help is appreciated.
Robert 
P.S. - I am running Ubuntu 10.10

---

### Post by Verbeck on 2011-01-09
right click on the desktop > create folder
right click the folder > open with other application > select 'file browser' and check remember this application for folder files'

OR

edit the file ~/.local/share/applications/mimeapps.list 
and change the line [FONT=monospace]
[/FONT]inode/directory=someapp.desktop
to[FONT=monospace]
[/FONT]inode/directory=nautilus-folder-handler.desktop;

hope that helps

---

### Post by slooksterpsv on 2011-01-09
Do this:

Open Terminal from Applications->Accessories->Terminal

Type in (and press enter after each of the following):
```

cd ~
pwd

```
what does pwd show?

Type in:
```

ls -al

```

What does that show?

I've ran into this problem when my home directory wasn't there, like I had no directory for my user account. Or I was missing all of the default folders (desktop, documents, downloads, pictures, music, videos)

---

### Post by robertcoulson on 2011-01-09
Verbeck...Thank you very, very, much...Worked great....Thanks again.
Robert

---

### Post by robertcoulson on 2011-01-09
slooksterpsv thanks, but Verbeck fixed it for me...Thank you though for trying to help.
Robert

---

