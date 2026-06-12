---
title: "Folder Administration"
date: 2011-04-04
forum: General Help
---

### Post by chand.sethi77 on 2011-04-04
I have installed php, mysql and apache using terminal and it created a folder /var/www where I can keep my files. But, I can't create a directory there..neither I can Save files up there

---

### Post by mendhak on 2011-04-04
Have you tried creating the file with sudo?  If you're doing it via Nautilus, press Alt+F2.  Then

gksu nautilus

In the Nautilus window that opens up, browse to /var/www and you should be able to create your files.

---

### Post by seawolf167 on 2011-04-05
Aye, sounds like you just need to use *sudo*

```
sudo mkdir /path/to/directory
sudo touch /path/to/newfile
gksudo nautilus
```

---

