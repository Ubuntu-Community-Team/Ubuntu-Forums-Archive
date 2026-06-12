---
title: "1 &amp; a 1/2 million files in a folder killing my system"
date: 2010-03-23
forum: General Help
---

### Post by Donalb on 2010-03-23
So I accidentally deleted a few jpgs from my /home...

I installed & ran Foremost.

System was crawling to a halt everytime I tried to access the /foremost/recovery folder.

So I let Nautilus spend the night loading the list of files. When I checked this morning all files were visible. Nautilus showed 1,593,904 files ranging from 1 byte to 11mb. (About 2 gb size)

Yep, 1 & a half million. nautilus hangs or literally takes trying to deal with these. even trying to delete 20 or 30 thousand at a time is impossible through nautilus.

So I'm wondering if someone could tell me how to rm every jpg smaller than say 100kb?

---

### Post by patchwork on 2010-03-23
[B]Test this with some test files first!

[/B]I tested with some small text files (instead of jpgs) and it seemed to work well.  The size constraints in the script describe 512 byte blocks (i.e. 2 for 1024 bytes, 1 for 512 bytes, etc).

You can find more information on this with```
man find
```

Also, change to the directory in advance, or you can add ```
cd /path/files/are/in && 
```to the pipeline before the first find command.
```
find -iname *.jpg -size 2 -delete && find -iname *.jpg -size 1 -delete && find -iname *.jpg -size 0 -delete
```

---

### Post by sisco311 on 2010-03-23
or:
```
find /path/to/dir -type f -iname "*.jpg" -size -100k
```
NOTE: find is recursive, if you don't want to search for files in the subdirectories, then:
```
find /path/to/dir -type f -iname "*.jpg" -size -100k -maxdepth 1
```

To move the files in the trash (**be careful**, **test** the command before you run it):

```
find /path/to/dir -type f -iname "*.jpg" -size -100k -maxdepth 1 -exec gvfs-trash '{}' +;
```

---

### Post by uRock on 2010-03-23
Burn them all to a DVD then delete the whole folder. When you go to put them back on the system separate the files into folders by size so that they are easier to manage as you sift through the folders. It is good to do that with the files as you collect them in the future.

---

### Post by Donalb on 2010-03-23
Thanks guys. Just to clarify though, if I move them to Trash, won't I still have some problems just emptying trash? 
 
I moved 50k files into Trash earlier and that crashed Nautilus also when I tried to empty it.  That's why I was think rm.

Burning to DVD would cause the same problem.I'd still have a folder with 1.5 million files what I'd be trying to browse to copy the relevant ones.

---

