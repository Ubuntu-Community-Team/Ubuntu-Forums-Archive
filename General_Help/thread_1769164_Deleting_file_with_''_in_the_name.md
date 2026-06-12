---
title: "Deleting file with '\' in the name"
date: 2011-05-27
forum: General Help
---

### Post by memilanuk on 2011-05-27
Hello all,

Not a Ubuntu question directly... I tried running a back-up/restore script in a WordPress install to migrate from one server to another... long story made short, I ended up doing it manually and all is well on that front ;)

The one remnant from that botched script is that it tried creating a directory 'wp-backup' and then a file inside that directory - but it tried using '\' instead of '/'.  So what it created was a file named 'wp-backup\index.php' with a file size of 0 bytes.

The problem is thus:  I can't change the permissions nor delete the file, because of the invalid file name.  I don't have direct shell access (that cost *extra*, of course) and every time I try with the web-based file manager (Quixplorer) it sees it as 'wp-backupindex.php', as though the '\' is acting as an escape sequence in the file name.  Same thing in FileZilla, I can't do anything to the file without it complaining about the invalid file name.

Any suggestions on how to ixnay this one file given the limitations above (no shell access) short of calling and bugging tech support to delete the file for me?

TIA,

Monte

---

### Post by AlphaLexman on 2011-05-27
Just escape the escape character...
```
shell_command wp-backup[COLOR="Red"]\[/COLOR]\index.php
```

---

### Post by memilanuk on 2011-05-28
See my original post... no shell access.

---

