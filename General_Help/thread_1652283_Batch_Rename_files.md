---
title: "Batch Rename files"
date: 2010-12-24
forum: General Help
---

### Post by cariboo on 2010-12-24
My youngest brother became a grandfather recently, he copied the photos to one of my systems. He named all the pictures with a period and a space at the start, then a number eg:

```
. 001.jpg
```

These show up as hidden files in Ubuntu. I've looked for a script to batch rename the files, but because of the dot space, I've run into problems. Can any one give me an example of a script or command that would help me rename all the files, there are 250 pictures, at once?

---

### Post by sisco311 on 2010-12-24
There are many ways. In Ubuntu, you can use the perl based rename command. Invoked with the -n flag it shows what files would have been renamed:
```

cd path/to/dir
rename **-n** 's/\. //' ./.\ *.jpg

```

---

### Post by TeoBigusGeekus on 2010-12-24
Or, if you want to use a gui, thunar's bulk rename is awesome.

---

### Post by sisco311 on 2010-12-24
> **TeoBigusGeekus said:**
> Or, if you want to use a gui, thunar's bulk rename is awesome.

+1 for thunar. 


[list]
[*]**gprename** 
[*]gnome-commander (file manager)
[*]purrr 
[*]pyrenamer 
[*]gwenrename
and
[*]**krename** 
[/list]

are also very good GUI tools.

---

### Post by RedRat on 2010-12-24
> **TeoBigusGeekus said:**
> Or, if you want to use a gui, thunar's bulk rename is awesome.
+2 for Thunar. It works great. If the files are "hidden" just turn on the view hidden files.

---

### Post by gamblor01 on 2010-12-24
You could also do this with a for loop in bash.  Essentially, just setup a for loop to loop through all of the .jpg files in the directory and assign them the next number.  For example, if you wanted the filename to begin with "picture" followed by a number, then you could do something like this:

```

$ j=1
$ for i in *.jpg
do
  mv $i picture$j.jpg
  let j=j+1
done

```My only complaint with this method is that Ubuntu will display the files lexicographically so it will display picture1.jpg, then picture10.jpg - picture19.jpg before it finally displays picture2.jpg.  Thus, the filenames appear to be listed out of order (surely 10 is greater than 2, yes?).   One way to get around this is to pad the numbers with zeros. Since you have 250 photos it means that every number must be a minimum of 3 digits.   For example:

```

$ for i in $(seq 1 9)
do
  mv picture$i.jpg picture00$i.jpg
done

```That will rename all of the pictures from 1-9 to 001-009.   Now to rename all of the ones from 10-99 you can use similar syntax but pad with only a single zero:

```

$ for i in $(seq 10 99)
do
  mv picture$i.jpg picture0$i.jpg
done

```This probably isn't the most friendly route but it's a good intro to shell scripts which can greatly simplify your life if you learn how to write them.  :)

---

### Post by sisco311 on 2010-12-24
Here is a bash for loop:
```

cd path/to/dir
for file in .\ *.jpg; do
  **echo** mv -b "${file}" "${file/. /}"
done
```

mmv equivalent:
```
cd path/to/dir
mmv -r **-n** ". *.jpg" "#1.jpg"
```

---

### Post by cariboo on 2010-12-24
Thanks for the help everyone.

---

