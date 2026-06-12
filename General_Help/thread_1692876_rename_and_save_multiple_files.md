---
title: "rename and save multiple files"
date: 2011-02-22
forum: General Help
---

### Post by chirag.joshi on 2011-02-22
Hello mates, 

I am quite new to script programming and I am facing an uphill task to rename files in one folder. I have gone through similar posts but most of them deal with renaming files by changing the file extensions.
Problem : I have a folder which contains files like bild01.jpg,bild02.jpg....and so on..
There are more files in the folders which should remain untouched.
I want to rename these 'bild' files as follows: 

bild01.jpg -----> 1c.jpg
bild02.jpg -----> 2c.jpg
.
.
.
bild30.jpg------>30c.jpg

I would like to create a script as:
#!/bin/bash
npics=`ls -1 bild*| wc -l`
for i in $npics;
do
??????
done

I would be obliged to receive any helpful input !

Cheers,

CJ

---

### Post by GrandTheft on 2011-02-22
Hey,

if I'm not mistaken

```
for i in *; do j=`echo $i | cut -d . -f 1 | cut -c 5`; j=$j"c.jpg"; mv $i $j; done
```should do what you want. If you want to select more than one character from the source file you will need to nest the command, respectively. 

I'm sure there is a solution with parsing the file name for "bild" and taking everything that follows (maybe sed +s +g?) , and attaching a "c", but as long as you only want to rename a set of few files, the above should to the trick. 

Edit:

```
for i in *; do j=`echo $i | sed 's bild   g' - | sed 's .jpg c.jpg g' - `; mv "$i" "$j"; done
```

replaces "bild" with nothing and ".jpg" with "c.jpg" which might be a better solution.

Regards,
gt

---

