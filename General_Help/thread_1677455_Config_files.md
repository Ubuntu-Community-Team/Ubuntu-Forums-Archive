---
title: "Config files"
date: 2011-01-28
forum: General Help
---

### Post by chillies89 on 2011-01-28
Very new to linux,

I am trying to set up my ubuntu install so i can share files to my xbox 360,  i have a program called ushare but for it to work i have to change a value in the config file.

using terminal and gui, both dont allow me to save the change. Is this something i have to allow?

thank for all and any help

---

### Post by sisco311 on 2011-01-28
Hi and welcome to the forums!

If it's a system wide config file, you have to edit it as root:
```
sudo nano path/to/file
```
or
```
gksu gedit path/to/file
```

See:
[uhelp]community/RootSudo[/uhelp]

---

### Post by chillies89 on 2011-01-29
Thanks for the reply, Ill keep trying it but it seems to only create a new file when i use that.  Ill continue to read over the commands.

---

### Post by sisco311 on 2011-01-29
You have to replace path/to/file with the actual path to the file. For example:
```
gksu gedit /etc/ushare.conf
```

---

### Post by chillies89 on 2011-01-29
I was typing sudo nano etc/ushare.conf
not sudo nano /etc/ushare.conf

problem solved! Thank you for your time.

---

### Post by sisco311 on 2011-01-29
You're welcome!

Don't forget to mark this thread as [SOLVED].

---

