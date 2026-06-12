---
title: "how to compress files and include full path??"
date: 2009-09-11
forum: General Help
---

### Post by petermg on 2009-09-11
Hi all!!!

I need to archive some files but include their full path from the root.  However I don't need all the files in the folder they reside in.  Using file-roller it does not include the full path if I just add a file, and if I add a folder it includes ALL the files in that folder.  Winzip has this feature, but I'm not using winzip lol.

This doesn't seem to be that great of a task, I've just been searching for a while and still no luck.  I want to create a gzip, or tar.gz or something like that of some files.  Any help is GREATLY appreciated.  Thank you!!!!!


Peter

---

### Post by DaithiF on 2009-09-11
maybe i've misunderstood, but why not:
```
tar -C / -cPzf ~/myarchive.tar.gz ~/file1 ~/Documents/file2 ~/Music/file3

```etc...

---

### Post by petermg on 2009-09-11
I'd rather save 30+ mins and use a gui rather than having to type ever filename and path. 

In referring to file-roller, I'm speaking in context of a GUI.  Thanks though.

---

### Post by DaithiF on 2009-09-11
fair enough.  but just saying ... depending on how you are choosing what to archive I wouldn't rule out the command line.  It is almost always quicker than a GUI (once you know what you are doing :)  And it most definitely doesn't involve 30mins of typing out long lists of files :)  -- there are lots of ways to include/exclude files based on patterns, attributes, etc.  But whatever works best for you.

---

