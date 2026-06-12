---
title: "Remove .u1conflict from all files"
date: 2010-06-24
forum: General Help
---

### Post by gr3gg0r on 2010-06-24
I made the mistake of using ubuntu one to sync an svn repo i have checked out.  Recently this has caused some issues with the repo like me mistakenly committing .u1conflict files or svn restoring the original file because it had been renamed to *.u1conflict after I've made changes to the file.

This has been quite a head ache.  There are hundreds of these files in conflict and it's really really really annoying.  How can I rename all these files from *.u1conflict to * ??

Related: why does ubuntu one rename the file instead of creating "conflict" versions of the file while leaving the original alone like dropbox does?

---

### Post by doas777 on 2010-06-24
I use pyrenamer for bulk renames, and if that isn't advanced enough ReNamer for windows works great in wine.

---

### Post by gr3gg0r on 2010-06-24
It looks like pyrenamer should do the trick.  Under patterns I'm doing 
original: {C}.u1conflict
rename: {1}

It's still scanning, but I'm pretty sure this will do it.

I'll update to solved if this does in fact resolve it.

Thanks!

---

### Post by dcjfm on 2010-11-02
> **gr3gg0r said:**
> original: {C}.u1conflict
rename: {1}


Ok, you should use 

original: {**X**}.u1conflict
rename: {1}

instead for keeping spaces in original filenames.

Example 1:
original: {C}.u1conflict
rename: {1}
"My Music.mp3.u1conflict" -> "Music.mp3"

Example 2:
original: {X}.u1conflict
 rename: {1}
"My Music.mp3.u1conflict" -> "My Music.mp3"

---

### Post by Sigma1 on 2011-05-19
Here's a fairly nice command, I picked up somewhere (here: [http://www.basicallytech.com/blog/index.php?/archives/10-Shell-stuff-rename-multiple-files-on-the-command-line.html]("http://www.basicallytech.com/blog/index.php?/archives/10-Shell-stuff-rename-multiple-files-on-the-command-line.html")), for the same thing.
cd to the folder you're interested in, then:
```
$ for FILE in *.u1conflict ; do NEWFILE=`echo $FILE | sed 's/.u1conflict$//'` ; mv $FILE $NEWFILE ; done
```
There has to be a way of making this recursive, too. On my machine there weren't too many files concerned, so this was sufficient. Note that the same code will work to remove any suffix or part of a filename. You just replace the occurrences of .u1conflict (for a suffix) with whatever you like.

---

### Post by cjastram on 2012-02-12
You can easily perform this operation recursively with this command:

```
find . -name "*.u1conflict" | xargs rename 's/.u1conflict$//'

```
If you want to test out the renames and make sure nothing will go horribly wrong, add -n to rename (so, rename -i 's/.u1conflict$//').

cej102937

---

