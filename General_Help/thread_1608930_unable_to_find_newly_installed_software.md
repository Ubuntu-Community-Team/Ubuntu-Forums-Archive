---
title: "unable to find newly installed software"
date: 2010-10-29
forum: General Help
---

### Post by bregale on 2010-10-29
hi all been using ubuntu for nearly 3 years now , i bought a game on line that is linux friendly i have converted it to .deb the the package manager did the rest, i now cant find the game to launch it even though it is listed as installed in synaptic i am using ubuntu  10.04 , any ideas will be helpful .


      thanks

---

### Post by jbruced on 2010-10-29
I'd run

sudo gnome-search-tool 

and search for the file name(or similar) to the game name. then you can create a launcher that points to the application file once you know where it is.

Hope it helps.

---

### Post by davec64 on 2010-10-29
HI,

When you converted it to a .deb there may not be code in the file to create a menu entry. Try entering the programme name in a terminal, this will also provide any errors that occur.

i.e if I wanted to start the file manager Nautilus, i would type at the terminal:
```
nautilus
```

---

### Post by efflandt on 2010-10-29
**man locate** (in a terminal). **q** quits if you have not used man pages before.

updatedb is run by cron.daily to update the locate database (at 6:25 AM on my system).  If that has not run since you installed the program, you could to **sudo updatedb** first.

---

### Post by bregale on 2010-10-30
thanks for your help i have located where it is , thought it would be in file system but its not should be able to sort it now 
  
 thanks for help

---

