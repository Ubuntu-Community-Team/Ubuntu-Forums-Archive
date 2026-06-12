---
title: "Strange problems with Trash"
date: 2010-01-25
forum: General Help
---

### Post by Muskegman on 2010-01-25
Hi everyone, even though i have emptied my Trash it still says i have 111 items in there. I have removed it from the panel and re added it and still when i hover my mouse over it, it still says 111 items, even after a reboot.

Its not causing me any trouble its more of an annoyance than anything, anyone else have this happening ?

currently using Karmic 9.10 :confused:

---

### Post by nothingspecial on 2010-01-25
What does ```
du -h ~/.local/share/Trash
``` output?

---

### Post by Muskegman on 2010-01-26
mark@mark-desktop:~$ du -h ~/.local/share/Trash
4.0K	/home/mark/.local/share/Trash/files
4.0K	/home/mark/.local/share/Trash/expunged
4.0K	/home/mark/.local/share/Trash/info
16K	/home/mark/.local/share/Trash


this is the output i get

---

### Post by llawwehttam on 2010-01-26
Try 
```
 sudo rm -rf /home/your_user_name/.local/share/Trash/*
```
Or you could try a reboot.

I always find a reboot helps....... at least sometimes.

---

### Post by nothingspecial on 2010-01-26
> **Muskegman said:**
> mark@mark-desktop:~$ du -h ~/.local/share/Trash
4.0K	/home/mark/.local/share/Trash/files
4.0K	/home/mark/.local/share/Trash/expunged
4.0K	/home/mark/.local/share/Trash/info
16K	/home/mark/.local/share/Trash


this is the output i get

There doesn`t appear to be anything in there. 4k for each of the three empty folders in there and 4k for the trash folder itself - 16k

---

### Post by Glinx on 2010-01-26
Had a similar problem after using a usb stick. I had to reinsert the stick and delete the hidden trash file from it for Karmic to empty the trash from the desktop.

---

### Post by Muskegman on 2010-01-30
Seems to have resolved itself, its now showing empty and yes i was using a USB stick at the time :)

---

