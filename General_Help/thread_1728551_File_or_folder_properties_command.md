---
title: "File or folder properties command"
date: 2011-04-13
forum: General Help
---

### Post by Diametric on 2011-04-13
Hello,

I'm having trouble finding the correct modifiers to the stat command to print out the file/folder properties in human readable format.  I would like to run a command on a given file or folder and have the file size in kb, mb, or gb size as opposed to byte size in addition to other pertinent information. 

Thanks!

---

### Post by Dysruption on 2011-04-13
You can use the du -h to give you the size of the directory in human-readable format. K is Kilobytes, M is Megabytes, G is Gigabytes. 

Also, du -ah will also display the files in the directories with their sizes. 

I hope this helps!

---

### Post by Diametric on 2011-04-14
Awsome!  Thank you.

---

