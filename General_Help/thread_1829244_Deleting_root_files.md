---
title: "Deleting root files?"
date: 2011-08-20
forum: General Help
---

### Post by rapattack1 on 2011-08-20
I have read a few pages and tried using commands to get rid of root files. They are files(videos) made by motion [http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning)
now i need to delete the files that i have checked and don't need anymore.
This is how i set it up [http://www.youtube.com/user/dgwthezombie#p/a/u/2/rzrXJLdNHwM](http://www.youtube.com/user/dgwthezombie#p/a/u/2/rzrXJLdNHwM)
i have now changed the target directory because Dropbox got full and i have no idea what to do about that.
So would appreciate advice on this :0)

---

### Post by akand074 on 2011-08-20
Run the command:

```
gksudo nautilus
```

in either a terminal or Alt+F2. This will open a file browser with root privileges allowing you to delete files. Alternatively, you can just delete them using a terminal via sudo rm (file)

---

### Post by whatthefunk on 2011-08-20
Should be pretty straight forward.  If you create the files in root, become root to delete them.  

```
sudo rm file_to_remove
```

---

### Post by rapattack1 on 2011-08-20
Oh thanks so much....thats the easiest way to deal with these files :0):)

---

