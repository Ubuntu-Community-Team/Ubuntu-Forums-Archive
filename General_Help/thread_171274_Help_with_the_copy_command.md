---
title: "Help with the copy command"
date: 2006-05-06
forum: General Help
---

### Post by joewhite on 2006-05-06
I have video files in seperate folders and the folder names contain the date and time like, for instance JAN061530. I don't need them ordered like this anymore so I decided to get rid of the folders and just have all the .avi files in one main directory. In constructing a command I have considered that that all of these folders have in common that they begin with JAN and that their contents (avi) must be moved into a root directory. I try cp /*Jan*/*.avi / but that doesn't work. The copy command only seems to allow the copying of one file at a time, getting confused at the fact there is more than one directory called Jan. But I want to do it in batch rather than drag each avi file out in to the main directory. Any ideas?

---

### Post by Ramses de Norre on 2006-05-06
Easiest way is a script I think, can't test it now but I think this might work:
```
#!/bin/bash
for file in *JAN*/*
do
cp $file ~/dir/
done

```
Copy it in a text file and run it from the directory the *JAN* directories are in.
To run it: sh textfile
Replace ~/dir/ by the location you want the files in.

---

### Post by joewhite on 2006-05-06
That worked great, thanks.

---

