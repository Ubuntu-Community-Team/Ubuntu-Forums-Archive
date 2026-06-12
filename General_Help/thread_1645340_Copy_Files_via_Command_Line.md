---
title: "Copy Files via Command Line"
date: 2010-12-14
forum: General Help
---

### Post by Deathmoon on 2010-12-14
I'm looking for a way to copy files with a certain file extension over to another folder.  

For example
Source Folder: /home/user/downloads
File Type:  *.epub
Destination Folder:  /home/user/epubs/

The downloads folder has several folders that may go as deep as 2 or 3 levels.

I tried this but it didn't seem to work (and I'm not really sure what to do to modify it to get it to work).
> find . -maxdepth 1 -type f -exec grep -q "pattern" '{}' ';' -exec cp '{}' /path/to/destination ';'

---

### Post by nothingspecial on 2010-12-14
Do you simply want to copy anything with the extension .epub in your Downloads directory to ~/epub.

Or,

Do you want to find any file in your Downloads directory and copy it to a directory of it`s extensions name, creating it if it doesn`t exist?

---

### Post by Deathmoon on 2010-12-14
I want to copy anything with the .epub extension from my Downloads directory into ~/epub.

---

### Post by nothingspecial on 2010-12-14
```
find ~/Downloads -type f -name '*.epub' -exec cp '{}' ~/epub \;
```

change cp to mv if you don`t want a copy in your downloads still.

---

### Post by Deathmoon on 2010-12-14
Perfect!

---

