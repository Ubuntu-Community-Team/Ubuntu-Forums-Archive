---
title: "silly chmod recursion question"
date: 2011-01-12
forum: General Help
---

### Post by Muster Mark on 2011-01-12
Hey All,

So, it seems to me I can't get chmod to function recursively.  I have a folder with a couple subdirectories in it and a few in each of those etc. Now, I want to give everyone read-write on all .c files.  So, I typed in terminal:
```
chmod -R 666 *.c
```

However, none of the .c files in any of the subdirectories were touched, i.e. I could have accomplished exactly the same thing by typing
```
chmod 666 *.c
```

I did RTFM, and it seems that what I did initially should have been the ticket.  What am I doing wrong?

Many thanks.

---

### Post by nothingspecial on 2011-01-12
```
chmod -R 666 /directory/containing/the_subdirectories/and_.c_files
```To change the permissions recursively on a directory and all its subdirectories you use the -R option on the parent.
[B]
EDIT[/B] [SIZE=1][COLOR=Navy]I don`t think I explained that very well, the -R option will recursively change the permissions on the directory you specify at the end of the command, and all the subdirectories contained within it it. You specified *.c So chmod changes the permission of all .c files in you working directory and any subdirectories of those .c files (of which there aren`t any, because they are files). ..........

........ I probably just confused the issue more[/COLOR][/SIZE]  **EDIT**

I`ve never tried to change the permissions recursively of only one sort of file but something like this should work
```

for f in $(find ./ -type f -name *.c); do chmod 666 $f; done
```Make sure you issue that from the top directory you want to chmod your .c files from, if you do it from / as root [SIZE=3][COLOR=Red]boom![/COLOR][/SIZE]

---

### Post by Muster Mark on 2011-01-12
> **nothingspecial said:**
> ```
chmod -R 666 /directory/containing/the_subdirectories/and_.c_files
```To change the permissions recursively on a directory and all its subdirectories you use the -R option on the parent.
[B]
EDIT[/B] I don`t think I explained that very well, the -R option will recursively change the permissions on the directory you specify at the end of the command, and all the subdirectories contained within it it. You specified *.c So chmod changes the permission of all .c files in you working directory and any subdirectories of those .c files (of which there aren`t any, because they are files). ..........

Ok, that actually makes a lot of sense.

> **nothingspecial said:**
> 
I`ve never tried to change the permissions recursively of only one sort of file but something like this should work
```

for f in $(find ./ -type f -name *.c); do chmod 666 $f; done
```

Thanks!  I'll give it a try (not at my linux machine atm).  I was wondering if you could recommend a site or article for learning more in-depth command line stuff?  At this point, most tutorials I find just talk about really basic stuff I already know (like how to use simple commands like *ls* and *chmod* in the most simple of circumstances), but I hit a wall any time I try to do things slightly more complicated.

> **nothingspecial said:**
> 
Make sure you issue that from the top directory you want to chmod your .c files from, if you do it from / as root [SIZE=3][COLOR=Red]boom![/COLOR][/SIZE]

I'll  be careful :)

Again, many thanks.

---

