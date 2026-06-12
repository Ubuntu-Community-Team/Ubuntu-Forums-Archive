---
title: "CLI- how to make backup copies of files in a directory?"
date: 2009-12-03
forum: General Help
---

### Post by blur xc on 2009-12-03
IIRC, back in the dos days (at least 15yrs ago for me) I could execute a command like "copy *.txt *.bak" to make backups of all .txt files in a directory.  ie. file.txt would become file.bak.

I'd like to do something similar in linux, except instead of replacing the extention, it'd be better for it just to add the .bak extension to the end of the file name, ie. file.txt woule become file.txt.bak (now that we can have long filenames).  

I would also use this command to make a backup of just one file, if it had a long filename and I didn't want to type it all out, and just use wildcards.  

Thanks,
BM

---

### Post by endBc on 2009-12-03
```
find . -name "*.txt" -exec cp {} {}.bak \;

```

---

### Post by blur xc on 2009-12-03
That's awesome.  I might have actually figured that out on my own had I thought about it long enough.

Quick q- what's the \; for at the end of every find command that has a -exec in it?  

Thanks,
BM

edit- just playing around with it, and was wondering, how can you make it not descend into subdirectories?  I've been wondering about that one as well when using the find command.

---

### Post by bodhi.zazen on 2009-12-03
[http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)

---

### Post by endBc on 2009-12-03
```
 
find . -name "*.txt" -maxdepth 0

```
 
.. will not go outside of the given directory.

---

### Post by StuartN on 2009-12-03
You might also have noticed that some applications, like gedit, create a copy of the previous version of a saved file under filename.txt~ and is not shown by Nautilus unless you view hidden files. These files are shown in the open file dialog.

---

### Post by blur xc on 2009-12-03
> **StuartN said:**
> You might also have noticed that some applications, like gedit, create a copy of the previous version of a saved file under filename.txt~ and is not shown by Nautilus unless you view hidden files. These files are shown in the open file dialog.

Yeah, I have noticed that but vi doesn't and I've been trying to get myself proficient w/ the command line.

I would like to get to a point where I could comfortable move around and get jobs done even if my gui crashes, which I almost did to myself recently.

BM

---

### Post by StuartN on 2009-12-03
> **blur xc said:**
> Yeah, I have noticed that but vi doesn't and I've been trying to get myself proficient w/ the command line.

You can make vi do likewise if you edit (or create) ~/.vimrc
and add the line **:set backup**

---

### Post by zman121 on 2009-12-03
You might also investigate these commands

rsync

rcs

They will take more time to master.

The rsync command will figure out what files need to be copied to a save directory to keep up with changes.

And the rcs tools will version files like they were software.  Very useful for archiving and reviewing changes over a longer time.  You can see previous versions of config files, for example.  Once you get used to using it, its painless to review changes, and even to back up to older versions that worked before you messed it up ;)


I lead several IT administration teams, and beat them mercilessly when they don't use RCS to version our configuration files.

---

