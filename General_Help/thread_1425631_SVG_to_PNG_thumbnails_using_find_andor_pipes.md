---
title: "SVG to PNG thumbnails using find and/or pipes?"
date: 2010-03-09
forum: General Help
---

### Post by dubref on 2010-03-09
I would like to generate png thumbnails out of all the .svg files I have in my home directory.

This gets me a nice list of svg.
```
find . -name \*.svg > mysvgs.txt

```

This makes a nice png out of myfile.svg
```
inkscape -D --export-png\=myfile.png myfile.svg
```


Now how do I glue them together?

Looking at **man find**, seems like -execdir argument might do the trick.
so the command would be something along the lines of:
```
find . -name \*.svg -execdir inkscape -D --export-png\={} {}
```
However, that does not look quite right as **find** finds the full directory name not just the file name.

---

### Post by kidders on 2010-03-10
Hi there,

A **for** loop would give you a little more flexibility to mess about with filenames while you're constructing the **inkscape -D ...** command, eg using **basename**, **dirname**, **sed**, etc.

The simplest case is where all your SVGs are by themselves in one directory. You could try something like...```
for f in *.svg; do inkscape -D -e "`basename $f .svg`.png" "$f"; done
```

Of course, you may well be using **find** because your files *aren't* sitting neatly in one place ... something a **for** loop can only handle if you manage to express all the search paths as a single regular expression. If so, try combining **find** and **for** ...```
for f in `find . -name "*.svg"`; do ........; done
```This is a bit hairier though, so I won't go into it unless you need to see how.

Incidentally, since you mentioned thumbnails, another tool you might find handy is imagemagick ... especially if there's anything you'd like to tweak about the images while you're converting them to PNGs.

I hope that helps a bit.

---

### Post by sedawk on 2010-03-10
The solution given above looks fine, so only a few extra remarks:

* Test the solution above first by adding an "echo" command in   front of the tool doing the conversion. Then you can see if the commands generated look fine. I often pipe the output of the echo test-run to a file like script.sh and run this script if everything looks fine.

* Some tools support batch mode, you might be able to load list of files from the GUI and then run some export operation. I do not know if inkscape can do it.

* In theory a simple xargs pipe might do, if the conversion tool has some magic to create the output filename decently:
```

find . -name \*svg -print|xargs -n 1 magictool --export=png

```
The tool xargs appends elements from the list read from stdin to the command (with -n 1 it appends one every time), so you get
```

magictool --export=png file1.svg
magictool --export=png file2.svg
...

```

---

### Post by dubref on 2010-03-19
Thanks guys for the advice!

My problem was that I had a certain svg file in a subdirectory I could not remember, nor could I remember the file name, only way I could tell the file was the one I wanted, if I could take a look at a thumbnail(well of course I could open all .svg files one by one...).

In the end the easiest thing to do was cp all .svg files to a single directory (plenty of hard disk space).

```
find . -name \*.svg -execdir cp {} /home/dubref/svg/ \;

```
This does allow for files with the same file name to be overwritten..

Now that I got copies in a single directory, I can run Imagemagick convert or Inkscape.

As of last note, I am getting better results using Inkscape to convert from svg to png than with Imagemagick. Imagemagick convert seems to miss some elements.

---

