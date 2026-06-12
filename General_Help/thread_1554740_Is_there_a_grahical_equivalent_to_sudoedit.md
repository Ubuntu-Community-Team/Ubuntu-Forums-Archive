---
title: "Is there a grahical equivalent to sudoedit?"
date: 2010-08-17
forum: General Help
---

### Post by descent89 on 2010-08-17
I use sudoedit in terminal frequently for safe editing of system configuration files. The problem is that when I execute
```
EDITOR=gvim gksudoedit /path/to/a/root/owned/conf/file 

```
nothing reasonable happens, sudoedit immediately ends with ```
sudoedit: /path/to/a/root/owned/conf/file unchanged

```
Gvim is running, but displaying only an empty sudoedit generated tmp file.

I thought of using gksudo, but man page doesn't mention any "gksudoedit" functionality.

Is there a way, or an application that supports sudoedit functionality in gtk-based plain text editors, analogously like gksudo is a gtk-based frontend for terminal-based sudo?

Thanks in advance.

---

### Post by Mulenmar on 2010-08-17
You could just back up the file, and then edit it with

gksu gedit

or the equivalent for your flavor. (Kubuntu uses something else, Xubuntu uses Mousepad last I I checked.)

---

### Post by kerry_s on 2010-08-17
gksudo gvim /path/to/file

---

### Post by jtprince on 2012-12-22
```
sudo -E gvim <somefile>
```

I think ubuntu may already alias *sudo* as *sudo -E*, though.

---

### Post by cariboo on 2012-12-22
Thread necromancy, closed

---

