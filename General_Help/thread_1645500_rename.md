---
title: "rename"
date: 2010-12-14
forum: General Help
---

### Post by dpwilson on 2010-12-14
Trying to rename files in terminal using rename.  I have searched the internet and these forums and I think I am just overlooking the obvious. I believe I have a certain way I think I need to do it and cant get past that.

I want to take the files P9220002.jpg, P9220004.jpg, etc and rename them to dover1.jpg, dover2.jpg, etc

I put in
```
rename -n 's/.jpg$/dover/' *.jpg
```
but get the P92....dover.jpg and so on.

How would I get rid of the P#'s and just have them renamed to dover 1.jpg, dover2. jpg and so on?

I know there are other ways to do this, but I want to figure out how to use rename to do so.  

Appreciate any help.

---

### Post by io5cml4z on 2010-12-14
Use the move command instead. e.g.
> mv file_a.png file_b.png

---

### Post by dpwilson on 2010-12-15
I am wanting to batch rename them.  I would like to do this to thousands of pictures in hundreds of folders.  I would also like to see where I am stumped with this rename as well.

I believe I have seen where you can use mv to batch rename and I know I can use a gui to do so, but I am trying to learn to do as much in terminal as I can.

---

### Post by BlueSpecial on 2010-12-15
Try this:

```
#! /bin/bash

x=0
for fname in *.png
do
  mv $fname `printf "%03x.png" $x`
  x=$&#40;&#40;$x+1&#41;&#41;
done
```

---

### Post by surfer on 2010-12-15
```
rename -n 's/P92200([0-9]*).jpg$/dover$1\.jpg/'  *.jpg
```

...will give dover02.jpg and dover04.jpg.

---

### Post by dpwilson on 2010-12-15
```
rename -n 's/P92200([0-9]*).jpg$/dover$1\.jpg/'  *.jpg
```

Thanks, exactly what I was looking for.  I know that there were other ways to do this, but I am trying to learn to do this using rename.  Thanks for all the replies as well.

---

### Post by surfer on 2010-12-15
> **dpwilson said:**
> ```
rename -n 's/P92200([0-9]*).jpg$/dover$1\.jpg/'  *.jpg
```

Thanks, exactly what I was looking for.  I know that there were other ways to do this, but I am trying to learn to do this using rename.  Thanks for all the replies as well.

now that i reread your post... it actually isn't quite what you want... it does not really count but just strip and rename the original filename.

---

### Post by dpwilson on 2010-12-16
That worked for what I wanted to do.  

While it did just strip the beginning off, is there a way to strip it all and rename by incrementing each by one?

Also, I am still a bit puzzled with the renaming process.  I thought that it was s'/old/new/'  so that it searched for the old and then replaced with the new name given, however it isnt stripping the old name, but adding it to the new.  Trying to learn this stuff, but I am missing out on something.

---

### Post by digitography on 2010-12-16
I'm no terminal genius so therefore use
pyrenamer

Applications
       Ubuntu Software centre.

very useful piece of software, even if you only use it once.

---

### Post by dpwilson on 2010-12-16
> I'm no terminal genius so therefore use
pyrenamer
Thanks for the suggestion.  I will eventually probably use something like this, and did just check it out and install it to use until I know more about "rename".  I do want to learn the terminal better and therefore would like to learn how to do it without a GUI.

Thanks again.

---

