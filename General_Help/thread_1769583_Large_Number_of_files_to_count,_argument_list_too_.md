---
title: "Large Number of files to count, argument list too long"
date: 2011-05-28
forum: General Help
---

### Post by dazz100 on 2011-05-28
Hi 
I have the standard problem of trying to count a large number of files in a directory (>100k)

I have tried:

ls ~/user/images/* -l | wc -l

and 

find ~/user/images/* -maxdepth 1 -type f | wc -l

In both cases, I get the argument list too long error message.
I have tried using xargs but I can't seem to get it to work right.

The command

find ~/user/*  -type f | wc -l 

returns a valid answer but it includes all the subdirectories in the file count.

Any help would be much appreciated.

EDIT
I am having similar problems with trying to find oldest file

The command:
ls ~/images/* -1 -t | head -1
report too many arguments

but if I go to the image directory and run:

ls -1 -t | head -1
it works.

but
ls * -1 -t | head -1 
and 

ls ./* -1 -t | head -1
don't work

They report too many arguments.

---

### Post by sanderd17 on 2011-05-28
could you try wrinting it to a file and then counting it?

```

ls -l ~/blablabla > files.txt
wc -l files.txt

```

Or maybe with grep:

```

ls -l ~/blablabla > files.txt
grep -c $ files.txt

```

---

### Post by prodigy_ on 2011-05-28
Standard problems call for [standard solutions](http://www.linuxjournal.com/article/6060?page=0,0).

If you deal with large amounts of files regularly, Method #4 from the article might be preferable. Further reading: [http://www.in-ulm.de/~mascheck/various/argmax/](http://www.in-ulm.de/~mascheck/various/argmax/)

---

### Post by dazz100 on 2011-05-28
> **sanderd17 said:**
> could you try wrinting it to a file and then counting it?

```

ls -l ~/blablabla > files.txt
wc -l files.txt

```

Or maybe with grep:

```

ls -l ~/blablabla > files.txt
grep -c $ files.txt

```

Hi

Thanks but no, that doesn't work.  It appears that the ls command gets too many arguments.  Anything added just makes it worse.

---

### Post by dazz100 on 2011-05-28
> **prodigy_ said:**
> Standard problems call for [standard solutions](http://www.linuxjournal.com/article/6060?page=0,0).

If you deal with large amounts of files regularly, Method #4 from the article might be preferable. Further reading: [http://www.in-ulm.de/~mascheck/various/argmax/](http://www.in-ulm.de/~mascheck/various/argmax/)

I have one application that is pouring images into a single directory.  The article is very interesting and identifies my problem exactly.

Knowing all that, I think I will try Method 1.  I will try storing the images in a number sub-directories. Searching each sub-directory in a bash script will give me an workable answer.

As a first step I have used the command at the terminal
```

ls -1 -t > list_of_filenames

```

This has got me a file with the list of file names.

Next I will write a small bash script that will loop through the filenames and sort them into sub-directories.
This is a one-off process to get me out of the hole I am in.
Once this is done, I will write a script to automatically drop future new files into sub-directories to avoid getting too many files to exceed argument limits.

Edit

It worked.

---

