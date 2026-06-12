---
title: "Can't access encrypted home folder"
date: 2011-02-16
forum: General Help
---

### Post by jchase45 on 2011-02-16
I had issues on my last install , I couldn't boot into it cause I accidentally uninstalled python 2.6 and everything it was attached to. So I reinstalled on a separate hard drive, I can see my other file system from the media folder but the only thing in my home dir is these 2 files 1 read me that says 

[PHP]

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
[/PHP]

and then this file 

Access-Your-Private-Data.desktop

but when I click it and try to run it I get this error 

[PHP]

Untrusted application launcher
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.


[/PHP]

any ideas ??

---

### Post by jchase45 on 2011-02-17
Bump

---

### Post by jchase45 on 2011-02-18
Bump

---

### Post by jchase45 on 2011-02-18
Bump

---

### Post by jchase45 on 2011-02-19
bump

---

### Post by jchase45 on 2011-02-20
bump

---

### Post by hakermania on 2011-02-20
Try in the desktop file->properties->permissions->allow executing file as program ??

---

### Post by jchase45 on 2011-02-20
Now I can't even access it. I tried to format and unmount it so I can put windows on that drive, but I got this error when trying to format in gparted


[PHP]



The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually


[/PHP]

---

