---
title: "Cant find the Network Manager"
date: 2010-11-06
forum: General Help
---

### Post by bazerka on 2010-11-06
Its just as the name says, i cant find the network manager applet o.o. What happened was it was automatically there when i first got Ubuntu, but after it downloaded the necessary updates on the update manager, i rebooted and it twas gone. Cant find it again :_, any1 know how to activate it or find it again. Thanks
-Baz

---

### Post by m4tic on 2010-11-06
Right click on the panel- add to panel. look for notification area.

---

### Post by bazerka on 2010-11-06
Ok great the notification area is up, still doesnt show the wifi icon or anything to do with the network manager...

---

### Post by iponeverything on 2010-11-06
open a terminal and type:

```

nm-applet&
disown %1
exit

```

---

### Post by bazerka on 2010-11-07
Ok so i typed in nm-applet&, and the terminal said "an instance of nm-applet is already running" but i dunno where it is and i cant see it... any ideas?

---

### Post by iponeverything on 2010-11-07
first do a:

```
killall -v -9 nm-applet
```

---

### Post by bazerka on 2010-11-08
Ok i did that and i killed the nm-applet and than i typed in the 3 lines of code, and it ran, great there isnt any change... the net manager still isnt there lol

---

### Post by bazerka on 2010-11-08
Ok here i got this 

isaac@ubuntu:~$ ** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:2780): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2780): DEBUG: old state indicates that this was not a disconnect 0
 but there is nothing showing in the notification area... any ideas?

---

