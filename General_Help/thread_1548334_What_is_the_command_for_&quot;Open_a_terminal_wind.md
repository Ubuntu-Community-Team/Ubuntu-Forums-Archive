---
title: "What is the command for &quot;Open a terminal window and run application in this terminal"
date: 2010-08-08
forum: General Help
---

### Post by medic2000 on 2010-08-08
What is it?

---

### Post by ankspo71 on 2010-08-08
Hi,
Do you mean this?
```
gnome-terminal -x command 
```

---

### Post by inameiname on 2010-08-08
Well I know how to make a script to do this, in which you simply run it and it'll open a terminal and run an application, whatever you want, and exit the terminal when the program or task is done. Here's an example, using rhythmbox:

```

#!/bin/sh

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
rhythmbox

```Using that, you can technically right click the application, such as finding the locale of the program rhythmbox, right clicking it, selecting properties, and change the 'open with' to a custom command, such as this:

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi &&

That works.

UPDATE:

Seems the above suggestion mentioned by [ankspo71]("http://ubuntuforums.org/member.php?u=734190") does the same thing.

---

### Post by medic2000 on 2010-08-08
> **ankspo71 said:**
> Hi,
Do you mean this?
```
gnome-terminal -x command 
```

Maybe. I use sakura. I have looked to the manual and there is a "-e" command for execute. I launch Alt+F2 and type "sakura -e top" and it works. But something like "sakura -e lampp start" doesn't work.

---

### Post by medic2000 on 2010-08-08
Oh ok lampp needs to be started by root. So this is another issue. Thanks guys, first solution does not work in some ways but second always do what i want.

---

