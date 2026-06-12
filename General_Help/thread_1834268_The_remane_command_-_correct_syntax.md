---
title: "The remane command - correct syntax?"
date: 2011-08-27
forum: General Help
---

### Post by zozza on 2011-08-27
I am trying to rename a serious of .JPG extensions as .jpg.

I use:

rename --no-act 's/.JPG$/.jpg/' *.JPG

Gnome shows:

IMG_4927.JPG renamed as IMG_4927.jpg

But, in fact, they are not renamed.  Why not?  I don't know if it matters but a number of the files in the directory have words separated by spaces such as "Name of File.JPG".

What is wrong with my command?  Thanks!

---

### Post by dino99 on 2011-08-27
try with underscore instead of space

---

### Post by zozza on 2011-08-27
You mean rename all the files with spaces in them then try again?  Why not just manually rename .JPG into .jpg then?

---

### Post by tredegar on 2011-08-27
Try
```
for f in *.JPG; do rename  's/\.JPG$/\.jpg/' "$f";done
```
...because the spaces in the filenames are the problem.

---

### Post by sbraz on 2011-08-27
> **zozza said:**
> rename **--no-act** 's/.JPG$/.jpg/' *.JPG
:confused:

---

### Post by nothingspecial on 2011-08-27
> **tredegar said:**
> Try
```
for f in *.JPG; do rename  's/\.JPG$/\.jpg/' "$f";done
```
...because the spaces in the filenames are the problem.

The spaces are dealt with by *

Nothing's getting renamed becaus you are using the --no-act option. Remove it and it will actually do it. Out a g at the end of the command and it will do all of them.

---

### Post by SoFl W on 2011-08-27
I don't use rename but the "mv" (move) command.  If doing it in bulk I use [GPRename]("http://gprename.sourceforge.net"), available in software center or the package manager.

---

### Post by tredegar on 2011-08-27
> The spaces are dealt with by *
You are right ;)
It's been fun.

---

