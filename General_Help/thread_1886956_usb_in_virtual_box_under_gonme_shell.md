---
title: "usb in virtual box under gonme shell"
date: 2011-11-25
forum: General Help
---

### Post by kmsalex on 2011-11-25
So i know this question has been answered a 100 times before, but the thing is all the answers i can find are how to do it under gnome 2.3x or unity. 

I'm at a lost as how to add the right user group in gnome-shell, is there a command line i can use?

Any suggestions are appreciated!

---

### Post by Sazhen86 on 2011-11-26
Try the addgroup command.  You'll need to use sudo to run it.  The syntax to add an existing user to an existing group is "addgroup USER GROUP".

Hope that helps.

---

### Post by kmsalex on 2011-11-27
trying 
```
 addgroup vboxuser
```

said that it added it up lunching virtual box and trying it out nothing changed

trying 
```
addgroup vboxusers
```

says that it already existes.

anymore ideas?

---

### Post by Sazhen86 on 2011-11-27
You need to add your user to the vboxusers group using a command like:

sudo addgroup <user> vboxusers

where <user> should be replaced by your username (without the angle brackets).

Hope that helps.

---

