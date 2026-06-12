---
title: "looking for a numerical batch renaming solution"
date: 2010-11-17
forum: General Help
---

### Post by treesurf on 2010-11-17
As a hobby I like to make short timelapse films ( [http://www.youtube.com/watch?v=9W-AHgeLrzg&hd=1](http://www.youtube.com/watch?v=9W-AHgeLrzg&hd=1) ).  I use mencoder to compile numerically ordered pictures into video.  Recently my camera rolled over from file name 9999.jpg back to 0001.jpg in the middle of a timelapse shoot leaving me with the problem that the photos in this series are not in chronological order.  If this was only a few photos it would be no problem to manually rename them, but this happened right in the middle of 785 photos.  Is there automated software/process that I can use to rename them in the numerical order that I would like?

---

### Post by asmoore82 on 2010-11-17
There is a `rename` command that batch renames files according to a given PERL expression.

But I don't know Perl!

I always use an on-the-fly BASH Shell for loop - I literally type the
for statement right on the command line instead of in a Shell script.

A trivial example, rename *.TXT files to .txt - without lowercasing the entire name:
```
for file in *.TXT; do mv "$file" "${file%.TXT}.txt"; done
```

Numbers and Math aren't a shell's forte, but you could do something like:
```
count="1"
for file in 9*.jpg 0*.jpg
do
echo mv "$file" $(printf '%08d.jpg' $count)
(( count++ ))
done
```
^if it looks like a winner, just take out `echo`

---

### Post by northern lights on 2010-11-17
[http://gnome-look.org/content/show.php/Renamer?content=87601]("http://gnome-look.org/content/show.php/Renamer?content=87601")

---

### Post by treesurf on 2010-11-17
> **northern lights said:**
> [http://gnome-look.org/content/show.php/Renamer?content=87601]("http://gnome-look.org/content/show.php/Renamer?content=87601")


Thanks!  That script is simple, effective, and integrates really nicely into the nautilus right click menu (using nautilus-scripts-manager).  I can see a whole lot more uses for this.


I love being able to mark a thread SOLVED :)

---

