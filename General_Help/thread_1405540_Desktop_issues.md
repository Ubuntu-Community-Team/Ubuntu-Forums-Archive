---
title: "Desktop issues"
date: 2010-02-12
forum: General Help
---

### Post by HyperX on 2010-02-12
I just installed Ubuntu 9.10 on a t41 laptop. Everything is snappy and great but I can't copy anything to the desktop, I also can't change the wall paper. Is there a setting I need to reset? Thanks to all!

---

### Post by gordintoronto on 2010-02-12
If you right-click on an empty part of your screen, you should be able to select "change desktop background."

And you should be able to drag a file from Nautilus to the desktop.

---

### Post by HyperX on 2010-02-12
> **gordintoronto said:**
> If you right-click on an empty part of your screen, you should be able to select "change desktop background."

And you should be able to drag a file from Nautilus to the desktop.

nope. just doesnt let me drag and cant change desktop. Any ideas? I can drag into my home folder but not desktop

---

### Post by x33a on 2010-02-12
post the output of
```
$ ls -l $HOME
```

---

### Post by HyperX on 2010-02-13
Here it is:

(btw right clicking on the desktop doesnt even work(nothing happens), but it works in folders), when I drag a file from any folder to desktop, the icon just drags itself back.

hyperx@t43:~$  ls -l $HOME
total 15608
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Desktop
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Documents
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Downloads
-rw-r--r-- 1 hyperx hyperx      167 2010-02-12 10:22 examples.desktop
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Music
drwxr-xr-x 3 hyperx hyperx     4096 2010-02-12 17:27 Pictures
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Public
-rw-r--r-- 1 hyperx hyperx 15943680 2010-02-11 14:57 sample.avi
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Templates
drwxr-xr-x 2 hyperx hyperx     4096 2010-02-12 10:27 Videos

---

### Post by HyperX on 2010-02-13
OK, weird. There was some update today for Ubuntu, I did it, and rebooted and now I can right click, I can drag and drop folders to desktop and change wall paper. So I am not sure what happened, but all is well.

---

### Post by x33a on 2010-02-13
Well, you should mark the thread solved.

just add [solved] to the title.

---

