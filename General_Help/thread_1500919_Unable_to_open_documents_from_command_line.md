---
title: "Unable to open documents from command line"
date: 2010-06-03
forum: General Help
---

### Post by bismark on 2010-06-03
Previously I was able to open any document I wanted in the CLI by typing:```
open some_document.txt
```

Now when I try to do this I get the following:```
$ open image.jpg 
Couldn't get a file descriptor referring to the console
```

Anyone have any ideas on what changed?

---

### Post by wired99 on 2010-06-03
I will first admit that I am not familiar with the **open** command.

The conventional way is to call up the program that will handle the file, then call the file.
e.g.: **$ gedit /path/to/file/file.txt**

I tried looking for the man page for **open** but it brings up info on **openvt** command. I'm not sure if that's what you were looking for.

---

### Post by Iowan on 2010-06-03
I'm not familiar with **open** either. Was it an add-on -  which version had it?

---

