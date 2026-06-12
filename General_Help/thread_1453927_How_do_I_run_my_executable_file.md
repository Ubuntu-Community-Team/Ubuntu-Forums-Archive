---
title: "How do I run my executable file?"
date: 2010-04-13
forum: General Help
---

### Post by Rick-O-Shay on 2010-04-13
Hello,
 
I am fairly new to Linux systems but I have a code that I just compiled and it produced an executable file that I need to run but I have no idea how to run that file. Is there a certain command to type to do it?
 
Thanks,

---

### Post by cdude42 on 2010-04-13
are you needing a windows .exe? if you need that then open a terminal and type.

```
 sudo apt-get install wine 
```

it doesnt work with most .exe files ive used but you might get lucky.

---

### Post by mckinnon81 on 2010-04-13
If you have download source code and compiled it then you would do the following with the file you are trying to run:

```
./<program name>
```

Notice the ./ in front of the file you are trying to run

Also make sure the file is executable, it should be if compiled from source, but if not

```
chmod +x <file>
```

---

### Post by hryanjones on 2010-04-14
Just as a quick add on to McKinnon you can check if files are executable from the command line:

from the directory where your compiled program file lives
>>> ls -l

(example output below & explanation)
[I][FONT="Courier New"]
-rw-r--r-- 1 slant slant  336 2010-04-13 20:57 A_Program_I_want2RUN
drwxrwxrwx 3 slant slant 4096 2010-04-09 20:37 Desktop
drwxr-xr-x 2 slant slant 4096 2010-02-04 18:27 Downloads
drwxr-xr-x 6 slant slant 4096 2010-04-09 20:57 jones_stuff
d--------- 3 slant slant 4096 2009-12-17 23:13 jrd
drwxr-xr-x 2 slant slant 4096 2009-12-04 01:39 Public
-rw-r--r-- 1 slant slant  336 2010-03-15 18:32 temp.txt[\I]
[B] ||||||||||_>(x for executable for everyone)
 |||||||||_>(w for writable for everyone)
 ||||||||_> (r for readable by everyone)
 |||||||_> (x " " by the file's group)
 ||||||_> (w " " " " ")
 |||||_> (r """"""")
 |||_|_> (x executable for the owner{usually the user} of the  file) _
 |||_> (w """"" by user)
 ||_> (r """")
 |_> (usually d {for directory}, could be l for links, etc)[/B][/FONT]

---

