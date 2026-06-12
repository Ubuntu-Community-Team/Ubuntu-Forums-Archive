---
title: "ubuntu files ..access deniend"
date: 2009-08-31
forum: General Help
---

### Post by soafy_san on 2009-08-31
hello every one !

i had hp comaq laptop (its in bad condition now) ,I took its hard disk which has 2 OS win xp and unbuntu 8.10 I need to take a file from the hard disk which was stored via unbutu OS . 
when I attached it(via USB) to pc has mandriva OS i saw the forlders but i couldnt access them , it gives message said access denied , the same for window when attached the HD to windows xp pc .
what should I do to get the files ?

thanks in advance

---

### Post by wojox on 2009-08-31
In a terminal try:

```
chmod -R 777 /path/to/folder
```

---

### Post by SuperSonic4 on 2009-08-31
Right click on a file in question and go to properties, it could be that root owns them.

---

### Post by soafy_san on 2009-08-31
I wanted to add that I want to connect it to  laptop has ubuntu OS is the commad your writ goes well for ubuntu, and yes the root owned them the previous ubuntu has just one user which the root and i know its password ,and remember the hard disk is now as USB .

---

### Post by The Cog on 2009-08-31
The Ubuntu user id that owns the file will not be the same as the user id in Mandriva who is now trying to read the file. It's a long time since I used Mandrake, but I think I would have used these commands:
[B]su -
konqueror[/B]
in order to get a file manager running with root priviledges. Perhaps these days I would use dolphin instead of konqueror- like I say, it's been a while.

Once you have copied the file off using the privileged file manager, you may then have to also set the owner to the id of your normal Mandriva user.

---

