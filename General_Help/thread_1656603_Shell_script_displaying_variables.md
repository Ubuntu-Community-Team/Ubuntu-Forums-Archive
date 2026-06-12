---
title: "Shell script displaying variables"
date: 2010-12-31
forum: General Help
---

### Post by U2XS on 2010-12-31
I am writing a shell script & keep getting an error with one part of it.  I have to use the convert tool (from ImageMagick) and I need to assign how much extra to add to my canvas (0x55, 200x0, 30x40, etc).  However I need to do that by assigning a variable **widthVar**.  The problem is that when I type the following line:
```
convert $file -bordercolor white -border $widthVarx0 $file

```
The variable is assumed to be **widthVarx0**, so it cannot run because it can't find that variable & because it is missing the second parameter!

Is there another way to display a variable other than $widthVar?  I have also tried $(widthVar), but I had an issue as well.  I don't really know why.

---

### Post by Ram-Z on 2010-12-31
try with
```
 convert $file -bordercolor white -border ${widthVar}x0 $file
```

---

