---
title: "Help moving multiple files"
date: 2010-11-08
forum: General Help
---

### Post by fmuise on 2010-11-08
If I want to move 3 different files with the same command what would the syntax of the command be?

---

### Post by nothingspecial on 2010-11-08
Depends if they are in the same directory and weather or not you want to move them to the same place

If that is the case then simply
```

mv file1 file2 file3 destination
```

---

### Post by fmuise on 2010-11-08
> **nothingspecial said:**
> Depends if they are in the same directory and weather or not you want to move them to the same place

If that is the case then simply
```

mv file1 file2 file3 destination
```

Thanks, 

yes they are in the same directory, and being moved to the same place, anyway you could be me an example if they weren't in the same directory, or say moving file1 from dir1 to dir 2 and moving file2 to dir2 to dir1.

or am I retarded.:P

---

### Post by SeijiSensei on 2010-11-08
You'd need separate mv commands for each source/destination pair and specify full pathnames from the sources.  You could do this in a script, but for only a few files, that's overkill.

```

mv /path/to/dir1/file1 dir2
mv /path/to/dir2/file2 dir1

```

---

### Post by nothingspecial on 2010-11-08
Yet, if you wanted to move all files of the same type in your home directory, eg jpegs, to a jpeg directory, then bash would save you time, using find

Or, if you wanted to move, all .mp3 to ~/Music and all .docs to ~/Documents, in one line.

But yes, for 3 files, do it one by one.

---

