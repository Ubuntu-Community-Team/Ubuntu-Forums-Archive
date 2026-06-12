---
title: "Automated Renaming of Files"
date: 2009-11-22
forum: General Help
---

### Post by SillySod on 2009-11-22
I am looking for a command or utility which will allow me to rename a set of files in number order without me having to individually rename each file.

For instance, if I have made a directory with selected images from my camera (IMGxxx or DCIMxxxx etc) then how could I rename all these files in sequence to be called, say, November1.jpg to November50.jpg ?

---

### Post by kaibob on 2009-11-22
The following shell script will do what you want. Be sure to change to the target directory before executing the script. 

```
#!/bin/bash

count=1

for file in *.jpg ; do
   mv "$file" "November-${count}.jpg"
   count=$((count+1))
done
```

You can use the above as a long one-liner:

```
count=1 ; for file in *.jpg ; do mv "$file" "November-${count}.jpg" ; count=$((count+1)) ; done
```

I don't use it, but you may also want to look at pyrenamer, which has a GUI:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

---

### Post by callan79 on 2009-11-22
> **SillySod said:**
> For instance, if I have made a directory with selected images from my camera (IMGxxx or DCIMxxxx etc) then how could I rename all these files in sequence to be called, say, November1.jpg to November50.jpg ?


If you're looking to use this for digital camera images only, then try renrot - just install it from the repositories, go to terminal, and type man renrot for the full usage information.

For reference, I use this line :

```
renrot -e JPG -n %Y%m%d-%H%M%S-%n
```

And this will give me filenames with the date/time the photo was taken, plus also %n includes the original filename on the end (which you can omit if you like).

Another suggestion install gqview. Start the program, go to the folder with your images, then select all and click file >> rename, then tick "auto rename". Works well.

Cheers
CD

---

### Post by SillySod on 2009-11-24
Thanks for this.  I have installed gqview and it gives me a "Numbering" option in the multiple file rename box, which is just what I need.

I'm wondering now though whether this option was there all the time, but I don't remember it when using Bulk Rename previously.

---

