---
title: "Search files containing a text within a hidden folder"
date: 2010-03-06
forum: General Help
---

### Post by koosfoto.hu on 2010-03-06
Greetings,
I have a hidden folder with a lot of text files in it. 
I would like to search in this folder for all files containing a given text.

The File Browser's" FIND searches only in the file names, not in their contents.
The FIND function of Ubuntu does not allow me to search ONLY in the given hidden folder. 

So, how can I find my files within the hidden folder with the given text within them?

Thanks,

Tamas

---

### Post by asmoore82 on 2010-03-06
```
grep "some text" /some/hidden/dir/*
```

if you need it be a recursive search, use `find` to help:
```
find /some/hidden/dir -type f -print0 | xargs -0 grep "some text"
```

if you need to root privilege to search/view the files, use `sudo` on _both_ sides of the pipe:
```
[COLOR="Blue"]sudo[/COLOR] find /some/hidden/dir -type f -print0 | [COLOR="Blue"]sudo[/COLOR] xargs -0 grep "some text"
```

---

### Post by patchwork on 2010-03-06
rather than using find for a recursive search, you can specify -r with grep like this:

grep -iHr <case insensitive search string> <directory>

or grep -ilr if you only want the file names

---

### Post by asmoore82 on 2010-03-06
If you are looking for a strictly graphical solution, use "Places -> Search for Files ..."

For "Nome contains:" use an asterisk(*) so that it will match every file.
Adjust "Look in folder:" to your needs.
Unfold "Select more options" with that little plus(+) button on the left,
you should have the option "Contains the text" in there to do a full text search.

---

### Post by asmoore82 on 2010-03-06
> **patchwork said:**
> rather than using find for a recursive search, you can specify -r with grep like this:

grep -iHr <case insensitive search string> <directory>

:popcorn:Awesome!

---

### Post by koosfoto.hu on 2010-03-06
Thanks a lot to all of U for the quick answers. 

Yes, indeed, I found, what I wanted to find. 
:-)

Great!

What recursive search is, by the way???

Have a nice night! (Here it is nearly 10 pm)


Tamas

---

### Post by Agent ME on 2010-03-06
A non-recursive search only searches files in a specific directory. A recursive search searches the files in that directory, and in all of its subdirectories.

---

### Post by koosfoto.hu on 2010-03-06
Logical. I should have found it out... 

THANKS, Agent ME!

Tamás

---

