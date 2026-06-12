---
title: "Making a script"
date: 2011-06-27
forum: General Help
---

### Post by c911darkwolf on 2011-06-27
I have watched a couple youtube videos and read a guide online and i'm still at a loss on how to make a script.

All i am trying to do is  make a script i can double click to do the following in terminal

vncviewer 192.168.2.2


I want to make a script my wife can click to connect to our Storage/Pritner PC.  

Any suggestions? 

or a good website to research ?

---

### Post by pqwoerituytrueiwoq on 2011-06-27
can't you use a desktop launcher for that?

---

### Post by wafflesausage on 2011-06-27
put the following code in a text file (vncviewer.sh, or whatever)
```

#!/bin/sh
vncviewer 192.168.2.2

```
Then mv vncviewer.sh ~/Desktop && chmod 700 ~/Desktop/vncviewer.sh
Double click on it and it should ask you if you want to run it in the terminal, choose "yes", etc.

---

### Post by c911darkwolf on 2011-06-28
I tried same thing before and it didn't work.  This time it did!  Thanks Waffle!!

---

