---
title: "Delete all files listed in a text file"
date: 2010-05-26
forum: General Help
---

### Post by seraieis on 2010-05-26
Through various Windows reinstalls and switches within Linux distros, I have a massive amount of duplication within my music archive (on the order of 7+ dupes of each file). Now, I found a lovely program called "fdupes" and was able to build a list of all the duplicate files, and I'm trying to use "xargs" to remove then. However, when I try and run the command "xargs -0 --arg-file="dupes.txt" rm" or "xargs -0 rm < "dupes.txt"" it give me the following error: "xargs: argument line too long".

Any idea what this is, or how perhaps a different way of accomplishing the same thing? I'm very new to Linux so I'm still in the learning phase :)

Thanks in advance!

Dan

---

### Post by dino99 on 2010-05-26
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

[http://webcache.googleusercontent.com/search?q=cache:QPVjzoYidHAJ:www.lamolabs.org/blog/2745/one-liner-copying-moving-files-efficiently-with-xargs/+xargs%2Bubuntu&cd=13&hl=fr&ct=clnk](http://webcache.googleusercontent.com/search?q=cache:QPVjzoYidHAJ:www.lamolabs.org/blog/2745/one-liner-copying-moving-files-efficiently-with-xargs/+xargs%2Bubuntu&cd=13&hl=fr&ct=clnk)

[http://www.xappsoftware.com/wordpress/2009/12/08/xargs-to-parallelize-jobs/](http://www.xappsoftware.com/wordpress/2009/12/08/xargs-to-parallelize-jobs/)

---

### Post by sisco311 on 2010-05-26
Try something like:
```

for file in $(< dupes.txt); do **gvfs-trash** "$file"; done

```

**gvfs-trash** moves the files in the Trash.

---

### Post by derrick81787 on 2010-05-26
If the text file contains the entire path of the files you want to delete or the files are in your current directory, then you can do it with a simple Bash script.  It would be something like this:

```
#!/usr/bin/env bash

echo "Beginning to remove files."
echo

for file in $(cat dupes.txt); do
   echo "Now removing the file $file..."
   rm "$file"
done

echo
echo "Finished removing files."
exit
```

That will delete the files and print out what it is doing at each step.

---

### Post by dino99 on 2010-05-26
> **sisco311 said:**
> Try something like:
```

for file in $(< dupes.txt); do **gvfs-trash** "$file"; done

```

**gvfs-trash** moves the files in the Trash.

as i've understood its only a dupes's list, not the files that are dupes. After finding and selecting, he need to move them then delete them.

---

### Post by seraieis on 2010-05-26
> **sisco311 said:**
> Try something like:
```

for file in $(< dupes.txt); do **gvfs-trash** "$file"; done

```

**gvfs-trash** moves the files in the Trash.

My next question is what do I do about spaces in the file names? I'm guessing into the loop, I'd need a way to not treat white space as the delimiter, but to use line breaks.

This is what I'm seeing:

Now removing the file Music/Jimmie's...
Now removing the file Chicken...
Now removing the file Shack/Pushing...
Now removing the file The...
Now removing the file Salmanilla...
Now removing the file Envelope/Folder.jpg...

I know with some programs, I can use -0 or -n, but that doesn't seem to work in this context.

---

### Post by sisco311 on 2010-05-26
Try:
```
while read file; do gvfs-trash "$file"; done < dupes.txt
```

---

### Post by seraieis on 2010-05-26
> **sisco311 said:**
> Try:
```
while read file; do gvfs-trash "$file"; done < dupes.txt
```

That worked! So the "read" operator reads the whole line, rather than pulling in each individual word?

---

### Post by derrick81787 on 2010-05-27
> **seraieis said:**
> That worked! So the "read" operator reads the whole line, rather than pulling in each individual word?

Yeah, that's correct.  That's probably the better way of doing this for this exact reason.

- Derrick

---

### Post by johnwhitkin on 2010-11-29
Oh i had the same problem but i will say ubuntu 10 is marvellous,i used a tool for searching and wiping such duplicate files which is a free version available at [www.duplicatefilesdeleter.com]("http://www.duplicatefilesdeleter.com")

---

