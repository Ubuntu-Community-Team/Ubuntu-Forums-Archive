---
title: "cli comparing file names recursively"
date: 2011-04-24
forum: General Help
---

### Post by chris1497 on 2011-04-24
I would like to use the command line to compare two directories against each other.  I have two folders called music collection that have evolved over the last year on two separate computers.  90% of the two folders are the same, but there are small differences.  I would like a solution that will print out all the differences so I can analyze them and choose what I want to do with them, before merging the two folders.  

for example.

I would like some kind of output that shows the differences and where its located.

comparing MusicCollection1 and MusicCollection2

dif1.mp3 located in MC1/folder1                     (this one I might want to keep and merge over)

dif2.mp3 located in MC2/folder3                     (while this one I might realize does not exist in both                                                                                              folders because I deleted it for a reason)

I've looked at sort, uniq, and even tried scripting my own solution, but haven't come up with an elegant solution thus far.  Its important that it is recursive because there are about 15 folders in Music collection and more folders under those 15.

---

### Post by Doug S on 2011-04-24
I think "diff" will do what you want.
diff /MusicCollection1 /MusicCollection2
Also, there was a similar thread a day ago, [http://ubuntuforums.org/showthread.php?t=1737520](http://ubuntuforums.org/showthread.php?t=1737520)

---

### Post by 3Miro on 2011-04-24
Check out Meld, it is a graphical front end for diff. I find it very useful. Meld should be in the Software Center.

---

### Post by chris1497 on 2011-04-29
thanks. diff was exactly the thing I was looking for.

---

