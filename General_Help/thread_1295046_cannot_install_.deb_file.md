---
title: "cannot install .deb file"
date: 2009-10-19
forum: General Help
---

### Post by bostongeek24 on 2009-10-19
i am trying to install a program that is in .deb format but for some strange reason ubuntu doesn't know what that is because when i double click it it gives me the window to chose which application to open the file with. i am using ubuntu netbook remix 9.0.4 on a msi wind u120. which program do i need to install .deb files and why doesn't ubuntu recognize it?

---

### Post by renkinjutsu on 2009-10-19
linux doesn't use file extensions to determine filetype.. so just to be careful, check to see what the file REALLY is

```
file /path/to/file
```

---

### Post by -Zeus- on 2009-10-19
if you get something like this:
```
$ file /path/to/file
/path/to/file: Debian binary package (format 2.0)
```

try the command:
```
$ gdebi-gtk /path/to/file
```

---

### Post by geirha on 2009-10-19
Perhaps it is corrupt? If you right-click it and select properties, what does the Type-field say? For a proper debian package it should say (application/x-deb).

---

### Post by lidex on 2009-10-19
Look in your main menu "System Tools" for "Gdebi Package Installer". If it's not there run this command in a terminal:
```
sudo apt-get install gdebi-gtk 
``` Simplest way to install a deb package is with this program.

---

### Post by bostongeek24 on 2009-10-19
fixed now. when i downloaded the file from firefox it seems firefox didn't know what to do with it. once i went into the desktop and double clicked it it installed fine.

---

