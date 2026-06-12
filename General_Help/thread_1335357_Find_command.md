---
title: "Find command"
date: 2009-11-23
forum: General Help
---

### Post by RedSingularity on 2009-11-23
Is there a way to get the find command to search all directories?  Even the hidden ones?

---

### Post by audiomick on 2009-11-23
After a VERY QUICK look in my reference book, I think

```
find /
```
should set find of from / and go through all the lower directories.

The syntax for find is 

find path options

also

```
man find
```

will get help.

---

### Post by RedSingularity on 2009-11-23
I have found that "find / name-of-something" has found a few directories but not hidden ones in my home folder.  I cant figure out how to get it to go through hidden folders as well.

---

### Post by Kaput1982 on 2009-11-23
```
find . -name filename
```

Will search from the current directory down and will include hidden directories.

---

### Post by gdonwallace on 2009-11-23
You will need to run the command as superuser:

**sudo find / -name <what you are looking for>**

That will allow you to enter any directory on your system.  It should allow the search of hidden directories / files as well.

---

### Post by t0p on 2009-11-23
Okay, let's imagine that you want to search the entire file system for a file called "file.txt".  You should type the following command:

```
sudo find / -name file.txt
```

**sudo** lets it search all files, including ones that you don't own;

**/** tells it to search all directories under / - ie all of them;

**-name file.txt** tells it to find files with the name "file.txt".

If you wanted to search all files in your home directory, you'd type:

```
find /home/username -name file.txt
```

That will search everything under your home directory, including "hidden" directories.

---

### Post by falconindy on 2009-11-23
Find is generally used for performing actions on the resulting files found. If all you're interested in is finding the location of files, use `locate` instead. You may have to use `sudo updatedb` first to get accurate results.

---

### Post by nothingspecial on 2009-11-23
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1128937") excellent tutorial from the extremely helpful andrew46.

---

### Post by XCan on 2009-11-23
> **falconindy said:**
> Find is generally used for performing actions on the resulting files found. If all you're interested in is finding the location of files, use `locate` instead. You may have to use `sudo updatedb` first to get accurate results.

Be aware that 'locate' uses a cache, thus you may find recent deleted files or not find recent created files. However, due to the cache, of course 'locate' is much faster.

---

### Post by RedSingularity on 2009-11-23
> **XCan said:**
> Be aware that 'locate' uses a cache, thus you may find recent deleted files or not find recent created files. However, due to the cache, of course 'locate' is much faster.

Is there a command i can use to update the cache??

---

### Post by fluffman86 on 2009-11-23
sudo updatedb

But it updates automatically on either each boot or each day, so I almost never have to run it.

---

### Post by RedSingularity on 2009-11-23
Great!  Thanks everyone!!

---

