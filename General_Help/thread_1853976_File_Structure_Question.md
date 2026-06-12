---
title: "File Structure Question"
date: 2011-10-03
forum: General Help
---

### Post by jpr25 on 2011-10-03
Hi,  I have folder and inside that I have lots of other folders and inside them I have different scripts.  I want to be able to run my script where ever I am without typing the full path to the scrips.   rather than add each location to my PATH variable can I make a folder and create like a pointer for example:  script1 = /full path/ script2 = /full path to this/  then just add that folder to my path?  hope that makes sense if so how do I make like the file pointer?  thanks

---

### Post by mcduck on 2011-10-03
I'm not sure what you mean with a "file pointer", but what I'd do is create the ~/bin directory, and then link your scripts into that directory.

~/bin is automatically included in your path if it exists (although you'll have to  log out and back again after you create it before it works).

...and to create symbolic links you can either drag&drop a file or a directory using middle mouse button, which will give you option to copy, move or link the file, or use the *ln* command in a terminal:

```
ln -s /path/to/sourcefile /path/to/link
```

edit: If you don't want to see the ~bin directory in your home, you can easily hide things by creating a file called .hidden and adding files and directories you wish to hide into it, one per each line. (it only works for files & directories that are in same place where the .hidden file is located, and only has effect in Nautilus)

---

### Post by jpr25 on 2011-10-04
cool I will try that thanks :)

---

