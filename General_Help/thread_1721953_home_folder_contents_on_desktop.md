---
title: "home folder contents on desktop"
date: 2011-04-05
forum: General Help
---

### Post by u-noob-tu on 2011-04-05
hello, id like to show some (not all) of the contents of my home folder on my desktop, namely the music, documents, videos, and pictures folders. however, if i copy the folders to the desktop they are then seperate from the original and are listed under the /home/user/Desktop/ directory, not /home/user/. what i want is to have these folders displayed on my desktop but still be synced with the originals in my home folder. i could do it manually, but that would be a pain. any advice?

---

### Post by wojox on 2011-04-05
You would need to edit:

```
/.config/user-dirs.dirs
```

---

### Post by Jouke74 on 2011-04-05
Another option is to install Ubuntu-tweak. It can also be simply undone with this program.

---

### Post by deathadder on 2011-04-05
What about right clicking on the folder in your home directory and choosing "Make Link" then drag and drop that into the Desktop folder? That just creates a symlink for you...

---

### Post by u-noob-tu on 2011-04-05
> **wojox said:**
> You would need to edit:

```
/.config/user-dirs.dirs
```

ill look into that.

> **Jouke74 said:**
> Another option is to install Ubuntu-tweak. It can also be simply undone with this program.

i have ubuntu tweak, but i dont want everything in my home folder to be on the desktop, just my most important folders.

> **deathadder said:**
> What about right clicking on the folder in your home directory and choosing "Make Link" then drag and drop that into the Desktop folder? That just creates a symlink for you...

so that would mean that whatever gets put in each respective folder will appear in both /home/user/Desktop/"foldername"/ and /home/user/? that will work.

---

### Post by nothingspecial on 2011-04-05
> **u-noob-tu said:**
> 



so that would mean that whatever gets put in each respective folder will appear in both /home/user/Desktop/"foldername"/ and /home/user/? that will work.

Yep, and if you delete the link you just delete the link not the contents of the folder it is linked to.

---

