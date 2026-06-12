---
title: "Why is tehre a home folder that I cant remove in my home folder?"
date: 2010-12-13
forum: General Help
---

### Post by MollyWop on 2010-12-13
[[IMG]http://img59.imageshack.us/img59/266/screenshotkoi.png[/IMG]](http://img59.imageshack.us/my.php?image=screenshotkoi.png)
After doing a restore maybe?

---

### Post by plucky on 2010-12-13
Post output from a terminal of ```
ls -l ~
```

It has a padlock so you probably don't own the file.

---

### Post by WorMzy on 2010-12-13
At a guess, you've been running "sudo mkdir" or "sudo cp" without paying attention to what you're doing.

Assuming that the folder is empty (use ls to check), and you want to get rid of it, run
```
sudo rm -r ~/home
```

---

### Post by MollyWop on 2010-12-14
> **plucky said:**
> Post output from a terminal of ```
ls -l ~
```It has a padlock so you probably don't own the file.
mike@Maverick:~$ ls -l ~
total 68
drwxr-xr-x 5 mike mike  4096 2010-12-14 11:47 Desktop
drwxr-xr-x 9 mike mike  4096 2010-12-12 16:25 Documents
drwxr-xr-x 2 mike mike  4096 2010-12-13 23:47 Downloads
drwx------ 3 root root  4096 2010-12-12 21:51 home
-rw-r--r-- 1 mike mike  9096 2010-12-13 23:52 hs_err_pid27.log
-rw-r--r-- 1 mike mike   117 2010-12-12 13:51 jagex_runescape_preferences2.dat
-rw-r--r-- 1 mike mike    34 2010-12-12 13:49 jagex_runescape_preferences.dat
drwxr-xr-x 5 mike mike  4096 2010-12-12 02:18 Music
drwxr-xr-x 3 mike mike 12288 2010-12-12 02:19 Pictures
drwxr-xr-x 5 mike mike  4096 2010-12-12 17:31 Public
drwxr-xr-x 2 mike mike  4096 2010-12-12 16:34 Templates
drwxrwxr-x 4 mike mike  4096 2010-12-11 20:57 Ubuntu One
drwxr-xr-x 5 mike mike  4096 2010-12-12 16:25 Videos

---

### Post by plucky on 2010-12-14
> drwx------ 3 root root 4096 2010-12-12 21:51 home

The file is owned by root is the reason you cannot delete it.

Either open nautilus with ```
gksudo nautilus
``` and change ownership to yourself.

Or from a terminal ```
sudo chown -R mike:mike home
```

Find out what is in there if you are going to delete it.

Good Luck

---

### Post by MollyWop on 2010-12-16
> **plucky said:**
> The file is owned by root is the reason you cannot delete it.

Either open nautilus with ```
gksudo nautilus
``` and change ownership to yourself.

Or from a terminal ```
sudo chown -R mike:mike home
```Find out what is in there if you are going to delete it.

Good Luckthat worked. Thank you

---

