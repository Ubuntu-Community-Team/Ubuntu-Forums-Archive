---
title: "Copy file with asterisk in filename?"
date: 2010-12-30
forum: General Help
---

### Post by Pithikos on 2010-12-30
I used the command ```
mv filename *.BACKUP
``` expecting to get a file with the name filename.BACKUP but instead I got a file with name "*.BACKUP". How can I fix that now?
I tried both "cp *.BACKUP file" and "cp '*.BACKUP'" but I just get this message:
```
cp: cannot stat `*.BACKUP': No such file or directory
```

---

### Post by lisati on 2010-12-30
I'm not quite sure what you're trying to do here. Do you want to copy a file or rename it? 

"mv" is short for "move". If you want to make a copy, you'll have to use the "cp" command. 

As well as this, the asterisk has a special meaning in filenames. For example, when doing a directory listing, it matches just about anything.

---

### Post by Nytram on 2010-12-30
Include quotes around the filename, such as:

> 
cp "*.BACKUP" filename


Or you could rename it with nautilus.

---

### Post by t4thfavor on 2010-12-30
Can you escape the * with something like this cp \*.backup?

---

### Post by johnmay on 2010-12-30
maybenot@zillatron:~$ cp ~/Desktop/'untitled folder'/*.BACKUUP ~/
cp: cannot stat `/home/maybenot/Desktop/untitled folder/*.BACKUUP': No such file or directory
maybenot@zillatron:~$ cp ~/Desktop/'untitled folder'/*.BACKUP ~/
maybenot@zillatron:~$ 


Your directory list has a misspelling, or you didn't spell the .BACKUP file properly, also, everything is CAP sensitive.

---

### Post by Pithikos on 2010-12-30
Well in the end I noticed that I accidentally deleted the file. though I still don't understand the result of command ```
cp file *.bak
```

I know that asterisk is a wildcard so why in the heck is it saving with the asterisk included? I just want to make a copy my "file" to "file.bak".

(in first post I was just trying to rename my file)

---

### Post by endotherm on 2010-12-30
I think you have the arguments backwards for what you want.
the cp and mv commands use a syntax like this:
```

cp <source_file> <destination_file>

```

the wildcard '*' refers to all files but (for most intents and purposes) can only be used as a source, not a destination. the destination should be a single object, be it a file or a directory. 

the command 
cp file *.bak
would copy the file 'file' to a new file named '*.bak'

there are potential consequences to having a file with that name. it will let you do it, but consider this:
```

user@maverick:~$ mkdir tst; cd tst
user@maverick:~/tst$ touch file1
user@maverick:~/tst$ ll
total 8
drwxr-xr-x  2 user user 4096 2010-12-30 22:37 ./
drwxr-xr-x 35 user user 4096 2010-12-30 22:37 ../
-rw-r--r--  1 user user    0 2010-12-30 22:37 file1
user@maverick:~/tst$ cp file1 *.bak
user@maverick:~/tst$ ll
total 8
drwxr-xr-x  2 user user 4096 2010-12-30 22:37 ./
drwxr-xr-x 35 user user 4096 2010-12-30 22:37 ../
-rw-r--r--  1 user user    0 2010-12-30 22:37 *.bak
-rw-r--r--  1 user user    0 2010-12-30 22:37 file1
user@maverick:~/tst$ mv file1 file1.bak
user@maverick:~/tst$ ll
total 8
drwxr-xr-x  2 user user 4096 2010-12-30 22:38 ./
drwxr-xr-x 35 user user 4096 2010-12-30 22:37 ../
-rw-r--r--  1 user user    0 2010-12-30 22:37 *.bak
-rw-r--r--  1 user user    0 2010-12-30 22:37 file1.bak
user@maverick:~/tst$ rm *.bak
user@maverick:~/tst$ ll
total 8
drwxr-xr-x  2 user user 4096 2010-12-30 22:38 ./
drwxr-xr-x 35 user user 4096 2010-12-30 22:37 ../
user@maverick:~/tst$

```

the rm at the end could not tell whether I wanted to delete all files that ended in .bak, or just the file called '*.bak'. as you can see, it took the more destructive option and deleted all the files, not just the one I wanted. fun that.

---

### Post by dcstar on 2010-12-31
> **Pithikos said:**
> Well in the end I noticed that I accidentally deleted the file. though I still don't understand the result of command ```
cp file *.bak
```

I know that asterisk is a wildcard so why in the heck is it saving with the asterisk included? I just want to make a copy my "file" to "file.bak".


You might get away with that in DOS but not Unix/Linux.

---

### Post by endotherm on 2010-12-31
what exactly do you want to do? just copy all the files to new files with .bak at the end?
this should do it:
```

#!/usr/bin/env python 

import os, sys, shutil

srcdir= sys.argv[1]
for f in os.listdir(srcdir):
    if not f.endswith(".bak"):
        fname=os.path.join(srcdir,f)
        if not os.path.exists(fname + ".bak"):
            shutil.copy(fname, fname + ".bak")

```

---

### Post by Pithikos on 2010-12-31
> **endotherm said:**
> what exactly do you want to do? just copy all the files to new files with .bak at the end?
this should do it:
```

#!/usr/bin/env python 

import os, sys, shutil

srcdir= sys.argv[1]
for f in os.listdir(srcdir):
    if not f.endswith(".bak"):
        fname=os.path.join(srcdir,f)
        if not os.path.exists(fname + ".bak"):
            shutil.copy(fname, fname + ".bak")

```

Yes but was expecting something simplier for such a task :/

And it doesn't have to be a case of many files. Imagine that you have a file with name "thisisafilewithaveryveryhugefilename.txt"
Now if you want to copy that to a backup file, it would make a pain in the *** to sit and write manually:
```
cp thisisafilewithaveryveryhugefilename.txt thisisafilewithaveryveryhugefilename.txt.bak
```So was expecting a simple way to make the backup without having to type the whole name twice. Something in the sence "make a copy of this file and add .bak at the end of it"

---

### Post by Pithikos on 2010-12-31
> **dcstar said:**
> You might get away with that in DOS but not Unix/Linux.

I guess it's a conventient that I still carry from the my "Windows" days :lol:

I think that's a +1 for DOS even though I hate M*.

---

### Post by WorMzy on 2010-12-31
You can press TAB to autocomplete file names in the terminal. You can also copy selected text with Ctrl+Shift+C, and paste with Ctrl+Shift+P.

---

### Post by melander on 2010-12-31
How about just using a loop in bash?

```
for i in *; do cp $i $i.bak; done
```

That should do it, right? and it even uses an asterisk ;)

Regards,

---

### Post by Pithikos on 2010-12-31
> **WorMzy said:**
> You can press TAB to autocomplete file names in the terminal. You can also copy selected text with Ctrl+Shift+C, and paste with Ctrl+Shift+P.

Thanks! wasn't aware of the TAB and it seems quite helpful.

Though Ctrl+Shift+C and Ctrl+Shift+P don't work. 
Ctrl+Shift+P acts as Ctrl+P which has the same effect as hitting the Up Arrow

```
manos@duntu:~/inspircd/run$ ls
bin  conf  data  inspircd  ircd.log  logs  modules
(Ctrl+Shift+P)
manos@duntu:~/inspircd/run$ ls
```

```
manos@duntu:~/inspircd/run$
(marking "inspircd" - Ctrl+Shift+C)
(Ctrl+Shift+P)
clear

```

clear appeared in the same line

---

### Post by WorMzy on 2010-12-31
Strange. Are you using something other than gnome-terminal? Like sakura or terminator?

---

### Post by Pithikos on 2010-12-31
> **WorMzy said:**
> Strange. Are you using something other than gnome-terminal? Like sakura or terminator?

Nope. I even hit F2 and ran "gnome-terminal" to be 100% sure.
Though I noticed now that Ctrl+Shift+C works. It's only Ctrl+Shift+P that doesn't work.

---

### Post by tredegar on 2010-12-31
Ctrl+Shift+[COLOR="Red"]V[/COLOR] pastes.

---

### Post by WorMzy on 2010-12-31
Ah, that's right. My mistake, I'm not sure why I said P. Sorry about that.

---

