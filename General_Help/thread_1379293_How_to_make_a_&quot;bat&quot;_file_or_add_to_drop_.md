---
title: "How to make a &quot;bat&quot; file or add to drop menu?"
date: 2010-01-12
forum: General Help
---

### Post by stillcen on 2010-01-12
I was wondering how to make, what i know (ok vaguely remember) as a .bat file, or how to add a executable file to the drop down menues.

i got freecol 0.9, and i can run it if i go into terminal, cd to the directory then type in 

                                 java -Xmx256M -jar FreeCol.jar


I bit obtuse, looking to know how to streamline.


stillcen


and thanks

---

### Post by tornadof3 on 2010-01-12
Not sure if this is what you're after, but have you tried right-clicking "Applications" in top right of screen, click "Edit Menus" and create a new menu item. Give it type "application in terminal" and set the command to 

java -Xmx256M -jar /path/to/FreeCol.jar

..? Might meet your needs.

---

### Post by jbird80 on 2010-01-12
Alternatively you can script it

#```
!/bin/bash

java -Xmx256M -jar /path/to/FreeCol.jar

```

copy and past the above code into a text editor and name it something like runFreeCol.sh

use chmod +x runFreeCol.sh to make it executable

run the script using ./runFreecol.sh

---

### Post by sisco311 on 2010-01-12
> **stillcen said:**
> I was wondering how to make, what i know (ok vaguely remember) as a .bat file, or how to add a executable file to the drop down menues.

i got freecol 0.9, and i can run it if i go into terminal, cd to the directory then type in 

                                 java -Xmx256M -jar FreeCol.jar


I bit obtuse, looking to know how to streamline.


stillcen


and thanks

Right click on the menu -> Edit Menus -> Highlight a sub-menu -> New Item & in the command filed type:
```
bash -c "cd /path/to/dir && java -Xmx256M -jar FreeCol.jar"
```

---

### Post by stillcen on 2010-01-14
Thanks guys thats just what i was looking for.

tak


stillcen

---

### Post by baddog144 on 2010-01-14
Just fyi, .bat is Windows-speak for a script ;)
Over here, they're called shell scripts :)

---

### Post by stillcen on 2010-02-02
Windows Speak??

i know know no Windows speak....now DOS, i vaguely remember hence the .bat.


enjoy

stillcen

---

