---
title: "spaces in files names"
date: 2010-01-26
forum: General Help
---

### Post by xgreyhound on 2010-01-26
Hi, I am delving into the linux command line and have noticed the following problem:  if I have files I have brought in from Windows that have spaces in their names (i.e. "my new file") I can't seem to do things with them on the command line.  Is there something I am doing wrong?

I have been renaming them with the file manager and putting underscores instead and that seem to work but I would like to know how to do from the command line, if someone can tell me how?

Thanks, Barton

---

### Post by tors on 2010-01-26
Hi!

You can use the backslash-character in front of the spaces:

> cat My\ Text\ File.txt


Or you could use "" around the filename:

> cat "My Text File.txt"

---

### Post by wojox on 2010-01-26
Try:

```
cat File\ With\ Spaces.txt
```

---

### Post by sharpdust on 2010-01-26
If you use single quotes, it will understand the spaces.
Example

```

touch 'a test file'
mv 'a test file' atestfile

```

---

### Post by sisco311 on 2010-01-26
You have to escape the spaces:
```
ls file\ name
```
or quote the name:
```
ls "file name"
```

```
man bash | less +/^QUOTING
```

---

### Post by steviefordi on 2010-01-26
All the above information is correct. However I will add something - the shell uses spaces to identify different arguments. That is, stuff you pass to programs that (usually) you want that program to work on like so:

programname argument1 argument2 argument3

Therefore spaces in file names pose a problem. You get around the problem by quoting. There are three types of quoting:

\ - quotes (escapes) the following character. Hence arg1\ arg2 is one argument. 

"" - quotes everything between the quotes but still allows for expansion. ie some characters may need to be quoted within these quotes depending on what you want to do.

'' - quotes everything and no expansion takes place
 
Read the QUOTING section of the bash manpage for more detailed info.

---

### Post by lewisforlife on 2010-01-26
One other thing worth mentioning.  If you type part of the file name and then hit the "Tab" key on your keyboard, the shell will automatically fill in the rest of the file name for you with the escape characters.

---

### Post by ghostborg on 2010-01-26
If you have many files I like the program GPRename found in the Synaptic package manager.

---

### Post by xgreyhound on 2010-01-26
Thanks for the answers and support.  I was beginning to suspect it had something to do with quotes and the argument thing as I created a file this way "touch my new file to test" and got six files, "my" "new", etc.  

Love this command line but, yes, difficult.  Good to have the help, here, though!  :)

Barton

---

