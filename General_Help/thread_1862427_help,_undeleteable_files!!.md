---
title: "help, undeleteable files!!"
date: 2011-10-16
forum: General Help
---

### Post by couldbbetter on 2011-10-16
hi everyone, i use furious iso mount to mount my images, im not terminal expert, and i couldent something to install, so i tried to trouble shoot by dragging the contents from the virtual mounted drive to my desktop to install, it didnt work, so i went to delete the copyed files and it says i dont have permission to delete teh files, i can rename them, but i canot move or delete tehm. wtf?

when i right click on them move to trash is greyed out

they have locks on the folder icons, i have unmounted, remounted all to no avail, i cannot delete these copyed files from the virtual disk

is there a way???

TLDR, i have 4 folders i cannot delete move to trash is greyed out i can rename them but not delete. on my desktop

ive also rebooted, and i still cant delete them

---

### Post by TeoBigusGeekus on 2011-10-16
Try with this
```
sudo rm -R ~/Desktop/nameoffolder
```

---

### Post by Carborundum on 2011-10-16
Try running this command in a terminal:
```
sudo rm -R _FOLDER_
```Substitute _FOLDER_ with the actual name of the folder you want to remove.

---

### Post by couldbbetter on 2011-10-16
never mind, i should have read the ******* manuel :P

i just had to right click go into properties for the permissions of the folder and set to it create and delete files, for some reason it was set to access only

as i set it to create+delete, the locks disappeared from the folders and i could delete them

thanks for the replys above guys, luckily i solved this one on my own tho

thanks!

---

