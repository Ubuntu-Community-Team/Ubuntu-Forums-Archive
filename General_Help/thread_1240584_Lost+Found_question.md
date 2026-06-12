---
title: "Lost+Found question"
date: 2009-08-14
forum: General Help
---

### Post by jeb800e on 2009-08-14
I am planning on completely re-formatting my HDD and bringing all the partitions back together into one when installing Ubuntu again. Will the "Lost+Found" folder(s) in the partitions be deleted/reset/removed of all files during the format, or what? I did notice one of my empty formatted partitions has a Lost+Found with .5 GB used. How could that be?

---

### Post by starcraft.man on 2009-08-14
This [thread]("http://ubuntuforums.org/showthread.php?t=229143") sufficiently answers the question.

To peer into a lost and found, ya need root privileges to Nautilus I believe. Just runt he following in the run menu (alt F2)

```
gksudo nautilus
```

Then navigate to directory in question.

---

### Post by jeb800e on 2009-08-14
[message deleted by original poster]

---

### Post by jeb800e on 2009-08-14
I didn't see anything in the Lost+Found directories, but I did get this in the Terminal:
[I]
jeb@Ubuntu-Linux:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:8200): WARNING **: Unable to add monitor: Not supported
seahorse nautilus module shutdown
jeb@Ubuntu-Linux:~$ 

[/I]_**I tried it again (just to double check), and I got this:**_[I]

jeb@Ubuntu-Linux:~$ gksude nautilus
bash: gksude: command not found
jeb@Ubuntu-Linux:~$ gksudo nautilus
Initializing nautilus-share extension

--- Hash table keys for warning below:
--> file:///media
jeb@Ubuntu-Linux:~$ 

[/I]

---

