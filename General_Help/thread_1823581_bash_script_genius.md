---
title: "bash script genius?"
date: 2011-08-12
forum: General Help
---

### Post by coldraven on 2011-08-12
Hi genius, I suppose that I'm being lazy but it would take me a day or more of searching and testing to do this.
I just need a simple script that creates a captions.txt file in a directory of images.
The format of captions.txt is like this:
```
image1.jpg|my caption 1
image2.jpg|my caption 2

```The script need to see if this file exists, create it or if it exists append to it.
Then take the filenames, add the "pipe" character and a placeholder caption.
This could be the filename or just "Untitled" or maybe both would be better.
So the result of adding image3.jpg to the directory would look like this
```
image1.jpg|my caption 1
image2.jpg|my caption 2
image3.jpg|image3.jpg Untitled

```I'm relying on your generosity. Thanks in advance.

---

### Post by gmargo on 2011-08-12
```

#!/bin/sh
for file in *.jpg *.JPG *.png *.PNG
do
        if test -f "$file" ; then
                echo "$file|$file Untitled"
        fi
done

```Just redirect the output into whatever file you like.

---

### Post by coldraven on 2011-08-15
Thanks gmargo, sorry that I did not reply sooner but I have been busy elsewhere.
I think that I can use your script although I was imagining something more complex.
I called it "cap" to keep it short.
If I have a folder with no captions.txt I can do ```
cap > captions.txt
```if I add some images to a folder that already has a captions.txt I can do
```
cap >> captions.txt
``` then edit the file to remove the duplicates. That is still easier than how I was doing it before.
Thanks for your time, I promise to study bash everyday :)

---

