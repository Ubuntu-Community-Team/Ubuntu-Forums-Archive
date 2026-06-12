---
title: "how do I fix this? running 11.10"
date: 2012-04-24
forum: General Help
---

### Post by Bushcraft Bill on 2012-04-24
my system just did an update and this message pooped up how do I fix what it wants? no idea what this cd-rom thing is no cd in the drive? 

W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by PaulW2U on 2012-04-24
Ubuntu is trying to download updates from a CD that it can't find.

Go into your repositories or sources list and uncheck the entry for the CD. The warning shouldn't appear the next time you update.

---

### Post by Bushcraft Bill on 2012-04-24
No idea were to go for that can someone give me guidance as to how to get from here to this repository thing?

> **PaulW2U said:**
> Ubuntu is trying to download updates from a CD that it can't find.

Go into your repositories or sources list and uncheck the entry for the CD. The warning shouldn't appear the next time you update.

---

### Post by jerrrys on 2012-04-24
You need to find software-sources in your menu and uncheck the CD's.

[ATTACH]216529[/ATTACH]

If you cannot find it you can [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter:

software-properties-gtk

Thats the command for my gnome desktop, I think it will work for Unity.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9)

Hope that makes sense

---

### Post by Bushcraft Bill on 2012-04-25
OK thanks that got me were I needed to go I unmarked the cdrom so will see now if that fixes things...

---

### Post by Bushcraft Bill on 2012-04-25
Ok just tested things and I dont get the error message any more thanks everyone for the help...

---

### Post by techsupport on 2012-04-25
> **Bushcraft Bill said:**
> Ok just tested things and I dont get the error message any more thanks everyone for the help...

Don't forget to mark this thread "Solved" to close it.

---

