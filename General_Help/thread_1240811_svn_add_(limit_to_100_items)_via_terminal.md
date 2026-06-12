---
title: "svn add (limit to 100 items) via terminal"
date: 2009-08-15
forum: General Help
---

### Post by retrodans on 2009-08-15
I have been asked to commit a LOT of images in a single directory into subversion.  But, whenever I open the directory through the GUI (nautilus or rapidSVN), my laptop cant load all the files so freezes.  And through terminal if I try to commit all the files at once, my internet connection times out.

So, I was hoping there would be a way of doing an svn add which only adds the first 100 or so files it finds, then I could commit those, and do the next 100 afterwards.

Any ideas on how to accomplish this?  Or another approach I could take?

Thankyou
Dan

---

### Post by DaithiF on 2009-08-15
Hi, something like:

```
svn status . | grep "^?" | cut -c9- | head -100 | xargs svn add && svn ci . -m"Your checkin message"

```

keep running this as many times as you need.
d

---

### Post by retrodans on 2009-08-15
Thankyou ever so much for that strip of code, I will try it later.  I don't suppose you could explain what some of those bits mean.  I thought grep looked at a files contents?  Also, I haven't used the command cut before.

Thankyou again
Dan

---

### Post by DaithiF on 2009-08-15
Hi,
ok taking things one piece at a time:

svn status . | grep "^?" | cut -c9- | head -100 | xargs svn add && svn ci . -m"Your checkin message"

svn status .  -- list the status of files in & below the current directory
new files show up with a status of ? in the first column of output
grep "^?" says find lines where the '?' character occurs at the start of the line, so only new files will be returned
cut is used to split lines of output into particular fields ... here I am asking for columns (-c) 9 onward (9-).  the output from svn status would look like this for new files:
?         newfile
ie. with the filename starting in column 9.  so the cut command gives me the filename on its own
head -100 takes the first 100 rows of output
xargs takes the 100 rows of output and constructs a single command with those 100 rows as parameters ... so if the output was
file1
file2
file3
etc.

'xargs svn add' morphs this into:
svn add file1 file2 file3 ...etc
&& means 'and' and is used to join 2 commands ... so we are saying:
svn add a bunch of files AND svn commit them

when commands are linked with the pipe '|' character, it means that the output of one command is passed as input to the next command, in a kind of chain.  This is a very common thing to do in unix, and although as you say grep can be used to search the contents of files, it can also be used in this way, to operate on content piped in to it.  Same goes for most other unix commands -- they are said to operate either on files or on STDIN (pronounced 'standard in') which means content passed into it in this way.

hope that helps
d

---

### Post by retrodans on 2009-08-15
Excellent, thankyou, it's always good to learn more about these commands.  Anyway, I tried it, but sadly got an error back

[HTML]svn: 'roducts' is not a working copy
svn: Can't open file 'roducts/.svn/entries': No such file or directory
svn: Write error: Broken pipe[/HTML]

The actual folder is 'products' so it's for some reason lost the first character of the foldername.  Just running svn status shows the full director of shopimages/products/xxxxxx

So I went into the lowest folder checked in (with no sub folders), and ran it again, this time I got the error:

[HTML]svn: invalid option character: b
Type 'svn help' for usage.
svn: Write error: Broken pipe[/HTML]

Any idea why this might be happening?

---

### Post by DaithiF on 2009-08-15
i miscounted the number of spaces before the filename -- filename starts at position 8, not 9.
so -c8- after the cut command.

---

### Post by retrodans on 2009-08-15
Thankyou, that appears to be working a charm.  I should have noticed that myself after your help, sorry about that.

Thanks again,
Dan

---

