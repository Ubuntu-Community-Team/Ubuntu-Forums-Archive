---
title: "DEB package installation Question"
date: 2009-09-15
forum: General Help
---

### Post by greenco on 2009-09-15
I installed a .deb package and it shows up in the Synaptic Manager, as being installed. My question this. **How do I locate it, so I can run it**? It does not show up on the "Applications" menu nor anywhere else that I can think of to look.

---

### Post by NoaHall on 2009-09-15
Try launching it from the terminal. It's probably a terminal - only app.

---

### Post by DeMus on 2009-09-15
> **greenco said:**
> I installed a .deb package and it shows up in the Synaptic Manager, as being installed. My question this. **How do I locate it, so I can run it**? It does not show up on the "Applications" menu nor anywhere else that I can think of to look.

In Synaptic, right- click the green box at the beginning of the line mentioning your installed program. Choose properties and then TAB installed files. Here you can see where the files are placed.

---

### Post by greenco on 2009-09-15
Thanks
I ran it with terminal and got a message that it could not find a database file. Is there a command that will show me the folder that it is installed in?

---

### Post by NoaHall on 2009-09-15
Try "sudo ldconfig", or restart, and try again.

Also, "locate FILENAME" will show you.

---

### Post by bacardiandwatermelon on 2009-09-15
I'd use the where is command in terminal... I'm pretty sure if something is in the /usr/bin directory they can be run from any directory.. e.g.

```
whereis gedit
gedit: /usr/bin/gedit /usr/share/man/man1/gedit.1.gz

```

---

### Post by greenco on 2009-09-15
Thanks DeMus
I must have looked at the Synaptic screen hundreds of times and I never noticed the "Properties" option. It showed me the locations and now I need to try and find the database files.
Thanks again to all

---

