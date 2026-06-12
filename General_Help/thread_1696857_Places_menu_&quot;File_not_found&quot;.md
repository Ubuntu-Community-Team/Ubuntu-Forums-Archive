---
title: "Places menu &quot;File not found&quot;"
date: 2011-02-28
forum: General Help
---

### Post by missa-moe on 2011-02-28
I went to open up my home folder from my places menu and it said file not found, it was working just fine yesterday...running 64bit maverick...please help?

i can still use all of my partitions and such but it seems to have broken the top half of my my places menu whatever 'it' is...

---

### Post by coffee412 on 2011-02-28
Ive not had the problem myself but I did google this with "Ubuntu menu file not found". 

This might interest you?

[http://askubuntu.com/questions/17042/file-not-found-in-places-menu](http://askubuntu.com/questions/17042/file-not-found-in-places-menu)

coffee

---

### Post by Krytarik on 2011-02-28
Though Ubuntu Tweak is a cool and powerfull tool, you don't really need it for this task.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by missa-moe on 2011-02-28
Thanks guys! I managed to get it working again appreciate the quick responses.

---

