---
title: "How do I get IDLE to work with Python 2.7?"
date: 2011-07-10
forum: General Help
---

### Post by Thrashrokz33 on 2011-07-10
Hello, I've recently adapted to Ubuntu from Windows, and I'm used to doing python a certain way. All I had to do was right click a python file, and choose the option "edit with IDLE", and it would let me code away. If I would hit F5, the code would go into the shell and execute. Now however, it's not as simple.

I've downloaded the IDLE 2.7 package from the Ubuntu download center, and I'm guessing it's installed because the download center says that it is, and so does the terminal. I'm a bit lost at this step though...how exactly do I work with my python files in IDLE now? When I click them, it simply goes to the shell, and not the IDLE program. I tried to do "open with..." but had no luck whatsoever finding the idle program. I checked /bin/lib, /usr/bin, almost everywhere. Maybe I'm just bad at searching for files, but is there a trick to this? Sorry if this sounds like such a newbish question, as I haven't even gotten the basics of Ubuntu down yet

---

### Post by ohadcn on 2011-07-10
1) install nautilus-actions and add an action for .py files to have a right click "edit with idle" option

2)what package did you install?
idle or idle-python2.7?
if you installed idle-python2.7 then it's command is idle-python2.7

anyway it installed to /usr/bin

---

### Post by Toz on 2011-07-10
To get idle (Python2.7) to show up in your "Open With" list, you need to edit two files:

1. ```
gksudo gedit /usr/share/applications/idle-python2.7.desktop
``` and add to the bottom of the file:> MimeType=text/x-python;

2. ```
gksudo gedit /usr/share/applications/mimeinfo.cache
```search for the line "text/x-python=" and add to the end of that line:> idle-python2.7.desktop;

---

### Post by Thrashrokz33 on 2011-07-10
> **Toz said:**
> To get idle (Python2.7) to show up in your "Open With" list, you need to edit two files:

1. ```
gksudo gedit /usr/share/applications/idle-python2.7.desktop
``` and add to the bottom of the file:

2. ```
gksudo gedit /usr/share/applications/mimeinfo.cache
```search for the line "text/x-python=" and add to the end of that line:

Thank you very much! Worked like a charm! I don't understand it but if you'd like to explain exactly what happened then that would help too.

---

### Post by Toz on 2011-07-10
Not sure I can explain it in any coherent fashion - I've just been able to figure out how it works. Here are a couple of links that might help:

[https://help.ubuntu.com/community/AddingMimeTypes]("https://help.ubuntu.com/community/AddingMimeTypes")
[http://mzimmerm.blogspot.com/2011/04/freedesktop-linux-mimetypes-file.html]("http://mzimmerm.blogspot.com/2011/04/freedesktop-linux-mimetypes-file.html")

---

