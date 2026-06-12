---
title: "cant copy files permission denied"
date: 2009-10-02
forum: General Help
---

### Post by frilock on 2009-10-02
i am loged in threw a live cd and i need to copy files that i have on a partition that will not boot some files im able to copy but others i cant because i dont have the right permission can some one please tell me how to do this so i can back my files so i can reinstall ubuntu thank you

---

### Post by MaxIBoy on 2009-10-02
These files would be the system files most likely, which have restricted permissions. I doubt you would need to copy those, as restoring them when you reinstall would likely clobber your system. (In other words, if it's not in your home folder, you should not try to restore it!)

That being said, the best way to copy those files it to pull up a teminal (applications>accessories>terminal) and type "gksudo nautilus" and hit enter. Do not change any letters to uppercase. When it asks for a password hit enter again (liveCDs do not have a password set.) Now a new file browser window will open. This filebrowser is running with administrator privilages and you can do whatever you want with it.


Nautilus is the name of the filebrowser program.

Gksudo is what you use to run a program as administrator (AKA "root" or "super-user") privilages. For non-graphical programs (I.E. programs run in the terminal entirely,) you can use "sudo" instead.

So the command "gksudo nautilus" means "open nautilus with gksudo," which has the result of running nautilus as the super user.


A word of warning: **only use gksudo if you really now what you're doing! **Root privilages are not intended for day-to-day use and make it really easy to screw things up.

---

### Post by frilock on 2009-10-02
got it thanks:)





> **MaxIBoy said:**
> These files would be the system files most likely, which have restricted permissions. I doubt you would need to copy those, as restoring them when you reinstall would likely clobber your system. (In other words, if it's not in your home folder, you should not try to restore it!)

That being said, the best way to copy those files it to pull up a teminal (applications>accessories>terminal) and type "gksudo nautilus" and hit enter. Do not change any letters to uppercase. When it asks for a password hit enter again (liveCDs do not have a password set.) Now a new file browser window will open. This filebrowser is running with administrator privilages and you can do whatever you want with it.


Nautilus is the name of the filebrowser program.

Gksudo is what you use to run a program as administrator (AKA "root" or "super-user") privilages. For non-graphical programs (I.E. programs run in the terminal entirely,) you can use "sudo" instead.

So the command "gksudo nautilus" means "open nautilus with gksudo," which has the result of running nautilus as the super user.


A word of warning: **only use gksudo if you really now what you're doing! **Root privilages are not intended for day-to-day use and make it really easy to screw things up.

---

### Post by DasEi on 2009-10-02
try as superuser, make sure partitons are mounted

sudo cp -r /media/disk-1  /media/disk-2  as example

---

