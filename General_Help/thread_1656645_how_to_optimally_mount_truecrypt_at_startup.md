---
title: "how to optimally mount truecrypt at startup?"
date: 2010-12-31
forum: General Help
---

### Post by linuxd00 on 2010-12-31
hi,



i want to use this line:



> truecrypt --auto-mount=favorites --background-task 



to mount my volume at start up... .

it prompts for my truecrypt password(TCP) to open my files.





so far i can put it in in the "Startup applications" but it needs root rights.. so it prompts for my root password and then again for my TCP.



id like it to only ask for my TCP.



so far i tried calling it from "/etc/rc.local" but somehow it gets ignored..
 i tried just putting the
 command and then also putting the command in a bash script and calling it from there.

rc.local does get parsed because i have other scripts there that do work.


i also tried putting it in the ~/.profile file. It works but as soon as i put my TC password the system kind of freezes. the mouse works but the screen freezes.  i can only change to a terminal by Ctrl+Alt+F1 and reboot from there.


any ideas?

---

### Post by linuxd00 on 2011-01-09
found the answer here:

[http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=65:truecrypt-and-sudoers&catid=37:tech-notes&Itemid=59](http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=65:truecrypt-and-sudoers&catid=37:tech-notes&Itemid=59)

basically you have to add an exception that allows to run truecrypt without password. So add this line to /etc/sudoers using the command "sudo visudo":

```
username ALL=(root) NOPASSWD:/usr/bin/truecrypt
```

replacing "username" with... well your username.

then you can place the truecrypt mount command in your autostart options

---

