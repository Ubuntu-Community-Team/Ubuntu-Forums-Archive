---
title: "Basic bash scripting help?"
date: 2010-01-01
forum: General Help
---

### Post by Nixie Pixel on 2010-01-01
Hi, I'm trying to use imagemagick to convert a bunch of .jpg files with custom color profiles to .png files without the pesky custom profiles. I believe the command I want is convert x.jpg x.png
(where x is the name of the file,a numerical value from 001.jpg to 4500.jpg).

Since there are so many files I want to write a bash script to do this, but I suck at writing in any sort of pseudo-programming language, so I was hoping for some basic pointers on how to repeat this command for each file.

Thanks!

---

### Post by iMisspell on 2010-01-01
If all the pic are in the same folder you could try something like this (untested (and im new to bash scripting so this might not work ;) ) )

```

# change to the folder where your pics are
cd '/folder/pics/are/in';

# loop through the folder
for img in *.jpg; 
do

# replace the file extension attached to $img with "nothing" (so to create the .png file name correctly)
newName=${img/.jpg/}; 

convert "$img $newName.png";

done

```

'done' is part of the code, not a personal comment :)

_

---

### Post by Herman on 2010-01-01
Here's another one just in case you want an alternative, you need to cd to the directory contianing your .jpg images first,
```
for f in *.jpg; do mv "$f" "${f%.jpg}.png"; done
```
EDIT: It's actually pretty much the same command, just condensed a bit. Probably I shouldn't have intruded, sorry for my rudeness.

---

