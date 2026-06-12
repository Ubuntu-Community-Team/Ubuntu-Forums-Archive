---
title: "Remove a folder with root ownership"
date: 2012-03-10
forum: General Help
---

### Post by Unotforme on 2012-03-10
I'm trying to delete an old folder (in the / directory), but the owner is root, and I'm not sure how to enable permission to remove the folder.

---

### Post by surfer on 2012-03-10
are you sure you should remove that folder? it may be vital for the system... but
```
$ sudo rm -r the_directory
```
should do the trick.

---

### Post by Unotforme on 2012-03-10
I should have posted this first, but the folder has a funny name (it was created by mistake). Here's a screenshot, it's the opt$%$%exit folder I'm trying to delete.

---

### Post by AnojiRox on 2012-03-10
what are the numbers in the little squares? i can tell you how if i know;).

---

### Post by Unotforme on 2012-03-10
That's part of the problem...I don't know!

How do I list the folder names in terminal, that might give me the more accurate folder name.

---

### Post by AnojiRox on 2012-03-10
oh I know! just type "sudo nautilus" (without quotes) in terminal. this opens the file browser with root permisions. try not to break anything:D

---

### Post by MSPdwalt on 2012-03-10
use ```
ls -a
``` to list all directory contents.  Use tab complete to auto-fill the path to the bad directory.  It's pretty hard to express paths with special characters.

```
gksu nautilus
``` should open the file manager as root, that may be easier.

---

### Post by Unotforme on 2012-03-10
Awesome!  That did it. Thanks very much.

---

### Post by AnojiRox on 2012-03-10
:popcorn:

---

### Post by Cheesemill on 2012-03-10
> **AnojiRox said:**
> oh I know! just type "sudo nautilus" (without quotes) in terminal. this opens the file browser with root permisions. try not to break anything:D

DON'T DO THIS !!!

You should use:
```
gksudo nautilus
```
instead :)

---

