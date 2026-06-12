---
title: "USB Drive is not a directory?"
date: 2010-11-08
forum: General Help
---

### Post by fmuise on 2010-11-08
When attempting to move files to my flash drive I get the following error:

       : is not a directory

I can cd media/flashdrive1, and view files but I can't move any files to the drive.

Any ideas?

---

### Post by sikander3786 on 2010-11-08
How are you trying to move the files? Via command line? Can you please mention that command?

Are you trying to move the files to the flash drive or to the HDD from flash drive?

---

### Post by Thelinuxgeek on 2010-11-08
You might try launching a terminal and running the command: gksu nautilus
this'll open a window that lets you move anything anywhere.

---

### Post by sikander3786 on 2010-11-08
> **Thelinuxgeek said:**
> You might try launching a terminal and running the command: gksu nautilus
this'll open a window that lets you move anything anywhere.
Copying from gksu nautilus will change the ownership of the files. So I wouldn't recommend it that way unless you want root to own your files.

---

### Post by fmuise on 2010-11-08
> **sikander3786 said:**
> How are you trying to move the files? Via command line? Can you please mention that command?

Are you trying to move the files to the flash drive or to the HDD from flash drive?

It's just a simple mv command,

```
mv file1 file2 file3 media/flashdrive1
```

I've also tried all kinds of different variations of the destination but nothing seems to work.

---

### Post by sikander3786 on 2010-11-08
Try with a slash before media.

```
mv file1 file2 file3 /media/flashdrive1
```

---

### Post by fmuise on 2010-11-08
> **sikander3786 said:**
> Try with a slash before media.

```
mv file1 file2 file3 /media/flashdrive1
```

Ugh, 

thanks sikander

---

