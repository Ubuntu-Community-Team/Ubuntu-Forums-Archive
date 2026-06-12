---
title: "Directory/Drive Comparison"
date: 2009-12-03
forum: General Help
---

### Post by Samilong on 2009-12-03
Is there any software out there that will allow me to compare the contents of two drives? 

My Music collection, some 45+Gb, is on one drive. Recently, I copied it onto a second, external drive. This external drive shows 135 fewer files than the internal one. Short of manually wading through five hundred plus directories and comparing them side by side, is there a program - preferably a graphical (rather than command line) one - to which I can say 'compare drive x with drive y and show me the differences'?

Incidentally, the external drive isn't a 'back-up' in the traditional sense; it exists so that I can move my music onto Windows, Mac and Sparc platforms at home and work.

Many thanks...

---

### Post by davec64 on 2009-12-03
Have a look at the DIRCMP command, this looks like it will do what you want.
Here are some more details:
[http://www.computerhope.com/unix/udircmp.htm]("http://www.computerhope.com/unix/udircmp.htm")

Sorry, this isn't a GUI!

---

### Post by Samilong on 2009-12-03
dircmp... Nope.

> bash: dircmp: command not found


Incidentally, if it makes a difference, I'm running 9.04

---

### Post by hal10000 on 2009-12-03
install **xxdiff**
you can compare the content of files as well as the content of directories. Start it from the commandline, e.g.
```
xxdiff dir1 dir2
``` it pops up a window where you can see the differences between the two directories.

---

### Post by jegerjensen on 2009-12-03
There is no need for additional software, use diff with option -q  (=quiet) and -r (=recursive)

```
[...]$diff -q -r /media/path/to/drive1 /media/path/to/drive2
```

This gives me the output
```

[...]$ diff -q -r 1 2
Only in 1/deep: 01 - Heartbreak Hotel.ogg
Only in 1/deep: 02 - Don't Be Cruel.ogg
Only in 1/deep: 03 - Hound Dog.ogg
Only in 1/deep: 04 - Love Me Tender.ogg
Only in 1/deep: 05 - Too Much.ogg
Only in 1/deep: 06 - All Shook Up.ogg
Only in 1/deep: 07 - (Let Me Be Your) Teddy Bear.ogg
Files 1/deep/23 - Return to Sender.ogg and 2/deep/23 - Return to Sender.ogg differ

```

---

### Post by StuartN on 2009-12-03
> **Samilong said:**
> This external drive shows 135 fewer files than the internal one.

The tool I found most friendly for exactly this task was Krusader. It appears under Tools->Synchronise Directories, which provides a list of differences that you can act on manually or assign actions for Krusader to take. It has plenty of options for compare by date, size, contents, left/right only. You can save the comparison as a profile to reuse whenever you update your music.

Meld is okay for finding differences, but not as versatile.

Another tool that is very useful for music collections is fdupes, an incredibly fast checksum-based duplicate file detector. It is command line only.

---

### Post by hal10000 on 2009-12-03
> The tool I found most friendly for exactly this task was Krusader
I just tried out this feature in krusader; it's great.

---

### Post by gadolinio on 2009-12-03
> **jegerjensen said:**
> There is no need for additional software, use diff with option -q  (=quiet) and -r (=recursive)

```
[...]$diff -q -r /media/path/to/drive1 /media/path/to/drive2
```This gives me the output
```

[...]$ diff -q -r 1 2
Only in 1/deep: 01 - Heartbreak Hotel.ogg
Only in 1/deep: 02 - Don't Be Cruel.ogg
Only in 1/deep: 03 - Hound Dog.ogg
Only in 1/deep: 04 - Love Me Tender.ogg
Only in 1/deep: 05 - Too Much.ogg
Only in 1/deep: 06 - All Shook Up.ogg
Only in 1/deep: 07 - (Let Me Be Your) Teddy Bear.ogg
Files 1/deep/23 - Return to Sender.ogg and 2/deep/23 - Return to Sender.ogg differ

```

Wow, nice one! Very useful command!

---

