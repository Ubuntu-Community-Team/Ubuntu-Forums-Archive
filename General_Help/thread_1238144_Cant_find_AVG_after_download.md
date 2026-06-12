---
title: "Cant find AVG after download"
date: 2009-08-12
forum: General Help
---

### Post by gavoby on 2009-08-12
I downloaded AVG free but cant find where it is after downloading it. Any ideas?

---

### Post by JohnWesleyMethodist on 2009-08-12
Did you install it? If you installed it you won't find an icon for it because it runs in Terminal only. I don't use it I use Avast! because it has a GUI.

 As far as not being able to find the file, just go to "Places" in the panel menu and then choose "Search For Files" and search for it. You may need to switch your location for searching to Filesystem instead of your username (home) folder.

---

### Post by gavoby on 2009-08-12
Ok how do I run agv or avast?

---

### Post by michy99 on 2009-08-12
As noted above, AVG 8.5 is command-line only. To update the database, enter```
sudo avgupdate
```To scan for viruses, use avgscan. For example, to scan your home folder, enter```
sudo avgscan ~
```To learn more about these commands, read the man pages.```
man avgupddate
man avgscan
```

---

