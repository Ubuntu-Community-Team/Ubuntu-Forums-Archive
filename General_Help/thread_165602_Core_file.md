---
title: "Core file?"
date: 2006-04-24
forum: General Help
---

### Post by sinkxdie on 2006-04-24
Hey guys...
Can I delete the file "core" in my /lib/udev/devices directory?
It takes up 500mb of space and I only have a 4gb partition, so that leaves me with about 1gb of free space.
It looks like it is for X and KDE desktop environments, while I use gnome.
When I open it, it opens a Bug Buddy report update tool.:confused:

---

### Post by egorgry on 2006-04-24
you can dump it unless you want to do some debugging. ;)

---

### Post by sinkxdie on 2006-04-24
And how would I dump it? :D I need root...how do you throw something out in root?
Sudo toss core :D:D:D

---

### Post by sinkxdie on 2006-04-24
Hello, anybody know how to delete a file with root permissions?

---

### Post by nanotube on 2006-04-25
issue command
```
sudo rm -i /lib/udev/devices/core
```
to remove your core file.

in general, you might really want to read
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
this explains stuff about root and permissions in ubuntu, and using sudo. :)

---

### Post by sinkxdie on 2006-04-25
I know how to use sudo, exept not hot to delete a file.

---

### Post by sinkxdie on 2006-04-25
I deleted the core file, but my free space is still only 500mb
:(

---

### Post by nanotube on 2006-04-25
[QUOTE=sinkxdie]I deleted the core file, but my free space is still only 500mb
:([/QUOTE]
well, first, check to see if the file is still there. (or maybe in the trash, if you deleted using nautilus gui?)
second, are you sure it was really 500mb, and not say, 500kb, instead? :)

---

### Post by sinkxdie on 2006-04-25
Noo...it had to  be 500mb, I think?
Well yeah its not in the trash either.

---

