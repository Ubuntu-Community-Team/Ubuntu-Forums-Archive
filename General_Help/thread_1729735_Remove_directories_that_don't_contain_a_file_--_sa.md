---
title: "Remove directories that *don't* contain a file -- safe testing method?"
date: 2011-04-15
forum: General Help
---

### Post by billWalker on 2011-04-15
Hi,

I'm trying to clean up an iTunes-sorted Music directory.  For whatever reason, it contains a large number of folders that have album art, but no music.  I'm actually more concerned about a safe way to test my removal batch, but I thought I'd paste everything I did in case it's useful to someone.

Based on [this thread]("http://ubuntuforums.org/showthread.php?t=1488832"), I came up with the following script:

```
#!/bin/bash

find ./*/* -type f -iregex ".*\(mp3\|m4a\)" | sort | while read line ; do
   echo "${line%/*}" >> file1
done

sort -u file1 > fileuniq

find ./* -mindepth 1 -type d > file2
sort file2 > file2sort

comm -3 fileuniq file2sort > artworkOnlyDirectories

rm file1 fileuniq file2 file2sort
```

I'm sure this isn't the most elegant solution, but I'm pretty confident that, after running it, I have a file named artworkOnlyDirectories that contains only the directories I will want to remove.

So, my next step, I guess, would be something like:
```
cat artworkOnlyDirectories | xargs rm
```

But I'm scared to just run this on my music folder.  Is there any way to run rm in "test mode", so that I would just see verbose output, but it wouldn't actually delete anything?  Failing that, does anyone see anything wrong with my plan?

---

### Post by tredegar on 2011-04-15
Run the script (which doesn't seem to delete anything that it has not created) and then just look at the file list it has created:

**cat artworkOnlyDirectories** or even **gedit artworkOnlyDirectories**
and check that it has what you want to see listed there, and nothing else.

---

### Post by Spyderkid on 2011-04-15
if your looking for a to securly remove files use *shred*

---

### Post by squaregoldfish on 2011-04-15
Simply replace 'rm' in your script with 'cat' - that way it will list the files that would be deleted.

Steve

---

### Post by billWalker on 2011-04-15
Thanks for the help, guys.  I mainly had cold feet to actually run the rm. I also realized probably the easiest thing to do to allay my fears (beyond reading the artworkOnlyDirectories file), would be to move the directories first.

So I ended up doing:

```
while read file; do mv "$file" ../Trash; done < artworkOnlyDirectories

```

Instead.  This actually didn't work too well, since it failed when the same album name (and thus directory) existed for multiple artists.  But running that a couple of times gave me the confidence to do:

```
while read file; do rm -r "$file" ; done < artworkOnlyDirectories
```

and clean up for good.  I didn't use xargs because the file was too big (!).

Anyway, thanks!

-bW

---

