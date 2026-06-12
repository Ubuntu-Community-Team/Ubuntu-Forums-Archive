---
title: "Is there a way to add an emblem to a file via the terminal?"
date: 2011-03-22
forum: General Help
---

### Post by drewsus on 2011-03-22
I would like to add an emblem to a file/folder via terminal. 
The idea is to be able to select certain folders/files via nautilus and then using a nautilus-script, add a predefined emblem to them. 
Is there any way to do this? Please share!

Thanks, 
Drew

---

### Post by drewsus on 2011-03-23
***bump*** (43 views but no leads? I am sure someone knows sooomething that could point me in the right direction)

---

### Post by dsv47 on 2012-10-15
The code for adding an emblem to a file via the terminal is:
gvfs-set-attribute -t stringv FILE metadata::emblems EMBLEMNAME
For FILE substitute the address of the file you want to add an emblem to, and for EMBLEMNAME substitute one of the following emblem names:
OK certified cool danger distinguished draft erase favorite important new ohno personal special urgent
Refresh the directory of the file you have added an emblem to in Nautilus in order to see your new emblem.

---

