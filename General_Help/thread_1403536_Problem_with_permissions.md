---
title: "Problem with permissions"
date: 2010-02-10
forum: General Help
---

### Post by litlfrog on 2010-02-10
I run into this every once in a while and it drives me crazy. I'm trying to extract Joomla to my /var/www directory to run on my machine. I've gotten the tar.gz archive saved and every time I try to extract the files using the archive manager I get "you don't have the right permissions to extract archives" to that folder. Why can't the archive manager just ask for a password if I need permissions to extract files to that folder? Do I need to do something with a chmod command?--I seem to remember using that in the past. I just get really frustrated that in 2010 I'm having to remember terminal commands to perform the bog-simple task of extracting zipped files.

---

### Post by audiomick on 2010-02-10
try using the file manager with root privileges
```
gksu nautilus
```

---

### Post by Enigmapond on 2010-02-10
Well first of all Ubuntu is all about the terminal. I couldn't do without it but it's right...you don't have permission and you shouldn't...run it in 

```
gksu nautilus
``` if you don't want the terminal to do it for you. You shouldn't change the permission to the folder.

---

