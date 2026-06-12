---
title: "How do I make a script, and how do I make it run at startup?"
date: 2010-06-07
forum: General Help
---

### Post by Evilhugbear on 2010-06-07
Hi guys, I want to make a script run at startup to make my video card's fan speed go faster.

The command is  :```
nvclock -f -F 50
```

How do I make this into a script? And how do I make it run when I boot into Ubuntu?
I have Ubuntu 10.04 if that matters.

---

### Post by WorMzy on 2010-06-07
Open gedit (Alt+F2, gedit, run), enter the following: ```
#!/bin/sh
nvclock -f -F 50
``` Save as fancontrol.sh.

Open startup programs (System -> Preferences -> Startup Programs) and add the script. Next time you boot, it will run automatically.

---

### Post by WorMzy on 2010-06-07
Whoops, forgot to mention one crucial thing: you need to mark the file as executable before it'll work. Just right click on the file, choose properties, and check the box next to "Allow executing as a program" (or words to that effect).

---

### Post by Evilhugbear on 2010-06-07
Thanks, it worked :D

---

