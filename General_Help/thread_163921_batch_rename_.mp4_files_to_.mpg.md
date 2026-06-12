---
title: "batch rename .mp4 files to .mpg"
date: 2006-04-21
forum: General Help
---

### Post by jms830 on 2006-04-21
I have a folder full of .mp4 files, and I want to change all of their extensions to .mpg, is there a quick way to do this with bash?

---

### Post by wylfing on 2006-04-21
Yep!

Try this making a text file like this:
```
#!/bin/bash

oldext=mp4
newext=mpg

for file in *.$oldext
do
    echo ${file%$oldext}$newext
done
```

Make that file executable and run it in the directory where you want to rename the files.

---

### Post by jms830 on 2006-04-21
thanks! will try it very soon :)

---

### Post by wylfing on 2006-04-21
Oops, I should have pointed out that this code will not actually rename anything. It just "dry runs" the renaming so that you can verify everything is going to come out like you expect. This is important, because if you have things like spaces in filenames, etc., you're going to end up with problems.

If you want to turn this into a real version, replace the echo line with this one:
```
mv $file ${file%$oldext}$newext
```

Sorry for not spelling that out in the first place.

---

### Post by skralljt on 2007-08-22
Hey, this is amazing!  But how can I make it work recursively?  For example, I have 100 folders all in one folder.  All 100 subdirectories have an sfv file, but I want to rename the sfv files to sfvold.  Is there a way?
edit:  after running this script modified to rename sfv to sfvold i get this error:  mv: cannot stat `*.': No such file or directory

---

