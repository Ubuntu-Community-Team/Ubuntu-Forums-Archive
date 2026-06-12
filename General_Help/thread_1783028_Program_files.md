---
title: "Program files"
date: 2011-06-15
forum: General Help
---

### Post by tonewheelkev on 2011-06-15
....PLEASE....how do I find the folder with my program files in it
.....in 11.04......driving me potty!!:confused:

---

### Post by hakermania on 2011-06-15
There's no such folder in Ubuntu at all.
**Configuration files** can be found at
~/.config/
**Executable files** can be found at
/usr/bin/
**Other files** used by a program can be found at
/usr/share/

and the list goes on but these are the basic ones

---

### Post by tonewheelkev on 2011-06-15
...thanks for that....but still stuck I'm afraid!

Have installed EAC through WINE...and now need to access the EAC folder......haven't a clue where to find it though....:(

---

### Post by inameiname on 2011-06-15
If you are talking about Windows programs through Wine, they are in a directory alltogether like Windows. 

And as for finding the folder, first open Nautilus, the file  browser. You can open it by double clicking your home folder on the  desktop. Then you can either enter  "/home/INSERT_YOUR_USERNAME_HERE/.wine/drive_c" into the field like you  would in Windows, and click enter.....OR....on the left side of the  screen where there are all of those shortcuts to folders, just click  'File System', and then inside the normal folder section on the right  double click: "home" => "INSERT_YOUR_USERNAME" => ".wine" =>  "drive_c"


Finally, if that doesn't work out for you, another way is to open that  folder directly through the terminal. Open a terminal window just as you  did uprading Wine, and then enter:

nautilus /home/me/.wine/drive_c


In that folder you'll find all the files you'd normally see in a Windows system.

---

### Post by dargaud on 2011-06-15
OK, then it's in ```
~/.wine/drive_c/Program Files/
```

---

### Post by tonewheelkev on 2011-06-15
Many thanks....found it....SORTED!!!!

(....until the next time.....just one disaster after another, I feel like I'm actually learning very little...):(

Is there  a good guide to get me moving with 11.04??

Thanks again Kev/UK

---

