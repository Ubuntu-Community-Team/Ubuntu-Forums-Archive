---
title: "read only files"
date: 2011-10-24
forum: General Help
---

### Post by salmonila on 2011-10-24
I lent my flash memory to a friend and when it came back I wanted to delete some files to make some room but I couldn't do it because  it was read only files and I can't change file permission 
[http://img855.imageshack.us/img855/6402/screenshotat20111024215.png](http://img855.imageshack.us/img855/6402/screenshotat20111024215.png)

---

### Post by Gadgetech on 2011-10-25
You should be able to delete the files from the command line using sudo. Open a terminal and navigate to you USB stick. Then use this command
```
sudo rm -R Greys.Anatomy.S07.HDTV.XviD-TvT
```

---

### Post by varunendra on 2011-10-26
> **Gadgetech said:**
> You should be able to delete the files from the command line using sudo. Open a terminal and navigate to you USB stick. Then use this command
```
sudo rm -R Greys.Anatomy.S07.HDTV.XviD-TvT
```
+1 if you want to remove the whole directory. However, if it is only some files, or if you want to do it with GUI, this would be more convenient:
press Alt+F2, then type and enter-
```
gksu nautilus
```
This will open the nautilus file browser as 'root' who has full access to everything. [COLOR=Red][As such, be cautious not to move/delete any system files/folders. Also, any file/folder copied or created in this mode can be opened by root only.][/COLOR] Once you are done, simply close the browser. Next time (without gksu) it will open as normal user.

The mounted drives in root mode can be found at /media directory.

---

