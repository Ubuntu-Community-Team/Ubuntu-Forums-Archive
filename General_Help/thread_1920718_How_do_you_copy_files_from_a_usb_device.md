---
title: "How do you copy files from a usb device?"
date: 2012-02-05
forum: General Help
---

### Post by mace200200 on 2012-02-05
The other day I wanted to copy a file from my friends external hard drive onto my computer, but I couldn't get it to do it. I could look at the files on the drive but when i tried to drag and drop them to my desktop, nothing would happen. What is the correct way to do it on ubuntu, do you just log in to sudo, mount the drive and then you can drag and drop them? Guess I need to see the codes to put into terminal so that i can copy and paste them. I'm also actually running xubuntu, but i assume it be the same on any variant.

---

### Post by deserthowler on 2012-02-05
What is the format of the drive?
Earl

---

### Post by mace200200 on 2012-02-05
> **deserthowler said:**
> What is the format of the drive?
Earl

not sure, my friends runs windows, so it must be fat32 then huh?

---

### Post by sudodus on 2012-02-05
It might be a problem with write permissions. If you start the file browser as root (both windows), you should be able to drag and drop.
```
gksudo thunar
``` (I think xubuntu uses Thunar)
Otherwise you can copy with terminal window commands for example
```
cp source target
``` or
```
sudo cp source target
```
as long as you have read access where you read and write access where you want to write.

---

### Post by corncob on 2012-02-05
Right-click on the file you want to copy and select 'Copy to'.  It give you a choice of your home folder or desktop.  You can move it around from there.

---

### Post by mace200200 on 2012-02-05
used the command lines and worked great thanks dude!

---

