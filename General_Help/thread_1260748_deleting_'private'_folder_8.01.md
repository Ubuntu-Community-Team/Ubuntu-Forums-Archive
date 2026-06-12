---
title: "deleting 'private' folder 8.01"
date: 2009-09-07
forum: General Help
---

### Post by irishgoth8822 on 2009-09-07
i can't figure out how to delete the private/encrypted folder that is a new feature of jaunty.  i don't remember if i did anything weird when i installed it, but all it tells me when i try to delete it (either by right-click, 'move to trash' or by the command 'ecryptfs-umount-private') is that the device is busy or, in the case of the command line attempt, that it's not a command.

i installed the folder in the first place just to see that i could, but i don't use it at all and i'm OCD about having unnecessary icons and folders floating around. anybody know how i can delete it?

---

### Post by lildigiman on 2009-09-07
navigate to the directory in Terminal and ```
sudo rm /file or folder
```

---

### Post by irishgoth8822 on 2009-09-08
well, first, i figured out that it's a directory not a folder. (duh, i should have realized), but in any case, sudo rmdir does not remove it, so unfortunately, it isn't that simple.

---

### Post by credobyte on 2009-09-08
Boot from Ubuntu LiveCD and do all the stuff from there. I'm not really sure what you are talking about ( encrypted home partition ? ), but most probably it's mounted and before you can do something with, it needs to be unmounted ( live disc ).

---

