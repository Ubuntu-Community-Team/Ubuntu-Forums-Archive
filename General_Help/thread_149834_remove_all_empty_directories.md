---
title: "remove all empty directories"
date: 2006-03-24
forum: General Help
---

### Post by chronusdark on 2006-03-24
does anyone know of a script/program to remove all empty directories under a directory i specify?

---

### Post by trent dillman on 2006-03-24
```
find /path/you/specify -type d -empty -delete
```

---

### Post by aysiu on 2006-03-24
Well, assuming that there's one top directory and only subdirectories a level beneath it, it's quite easy, actually.

For example, if you have a setup like this:

Parent >

>> Child1 >> File File File
>> Child2 >>
>> Child3 >>
>> Child4 >> File File
>> Child5 >>

And then do ```
cd Parent
rmdir -v *
``` only Child2, Child3, and Child5 will be removed.

The *rmdir* command actually is described as > rmdir - remove empty directories in the man page for it.

---

### Post by trent dillman on 2006-03-24
Hehe, gotta love having multiple ways to do things.

---

### Post by aysiu on 2006-03-24
[QUOTE=trent dillman]Hehe, gotta love having multiple ways to do things.[/QUOTE] I wasn't too sure about the *rmdir* command at first, but I tested it out on some newly created directories, and it worked.

It won't work, unfortunately, if the OP wants to delete empty directories that are two levels down from the parent folder.

---

### Post by trent dillman on 2006-03-24
Yeah, that's why I gave him 'find' instead...

---

### Post by ComplexNumber on 2006-03-24
[quote=chronusdark]does anyone know of a script/program to remove all empty directories under a directory i specify?[/quote] if you use the main search program for gnome that you can find in the menu, there is an option to search for empty directories. just do a search and then delete the list.

---

### Post by chronusdark on 2006-03-24
worked great thanks very much

i used the find command one

---

