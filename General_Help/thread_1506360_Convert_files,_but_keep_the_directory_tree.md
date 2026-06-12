---
title: "Convert files, but keep the directory tree"
date: 2010-06-10
forum: General Help
---

### Post by LuciusMare on 2010-06-10
Hello, I've got a directory structure full of files. I want to convert them all into some other format, but I don't know how to keep the directory structure, is there a way so I can "set" which command to use on files instead of `cp`?

---

### Post by prshah on 2010-06-10
> **LuciusMare said:**
> I want to convert them all into some other format, 

An example is worth a hundred explanations, so here goes```
find /home/user/Pictures -iname "*.bmp" -execdir convert "{}" "{}".jpg \;
```

Where:
find - is a command used to find files
/home/user/Pictures - is a directory in which to look for files
-iname - This indicates find name with case insensitive matching
"*.bmp" - The filenames to look for
-execdir - Execute the following command in the directory in which the original file is found
convert - name of another command. This command is to be used on the found file
"{}" - this portion is replaced by the name of the file found
"{}".jpg - this is the same filename, with ".jpg" added to it
\; - tells find that the "execdir" section has ended.

Please post back if this is confusing or you want a more detailed explanation.

---

### Post by LuciusMare on 2010-06-10
Thanks, it works, but I wanted a something a little bit different. I wanted to make another directory, with the dir tree same as directory1, but all files converted, instead of the original files. Do you know how to do it?

---

### Post by ambroseya on 2010-06-10
can you just make a copy, in the correct structure, and then run that on the copy of the files? (I always do something like that anyways because I'm too scared to do *anything* to original files -- I always copy, and then perform actions on a copy.)

---

### Post by LuciusMare on 2010-06-10
ambroseya: Why didn't I think of that? >_>
Well, thanks, I guess it will work  :)

---

