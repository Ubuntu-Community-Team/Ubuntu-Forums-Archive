---
title: "multiple file renaming on command line"
date: 2012-09-09
forum: General Help
---

### Post by unckybob on 2012-09-09
This is something I have to do quite often so I would really appreciate it if someone could help me with it. 

This is a question mostly about command line syntax which might be easy for someone to explain. I have a number of files that I've taken off my digital camera 100_1116.jpg through 100_1147.jpg. There are 32 of them. I have them all in the same directory. 

I would like to use the "convert" command on the whole lot of them to convert them to a smaller size and rename them at the same time. I don't exactly know how to do the renaming part. I would like to rename them something like Home_Picture_01.jpg through Home_Picture_32.jpg, but I don't know how to do it.

The syntax for the "convert" command is something like:

# convert -size 120x120 old.jpg -resize 120x120 new.jpg

Maybe this will need to be run in a shell with a loop or something. It's been a long time and I've forgotten how to do anything like this. I used to have a job where I would use a lot of Unix and I'm pretty sure this can be done pretty easily. I would surely appreciate it if someone would give me a hand.

---

### Post by steeldriver on 2012-09-09
I think it depends how picky you are about the new filename - if you are OK with just reusing the old name plus a suffix (or prefix) then something as simple as

```
for file in *.jpg; do convert -size 120x120 "$file" -resize 120x120 "${file%.*}"_small.jpg; done
```

should do it - it just strips off the trailing .jpg extension then adds back _small.jpg

---

### Post by Primefalcon on 2012-09-09
> **unckybob said:**
> This is something I have to do quite often so I would really appreciate it if someone could help me with it. 

This is a question mostly about command line syntax which might be easy for someone to explain. I have a number of files that I've taken off my digital camera 100_1116.jpg through 100_1147.jpg. There are 32 of them. I have them all in the same directory. 

I would like to use the "convert" command on the whole lot of them to convert them to a smaller size and rename them at the same time. I don't exactly know how to do the renaming part. I would like to rename them something like Home_Picture_01.jpg through Home_Picture_32.jpg, but I don't know how to do it.

The syntax for the "convert" command is something like:

# convert -size 120x120 old.jpg -resize 120x120 new.jpg

Maybe this will need to be run in a shell with a loop or something. It's been a long time and I've forgotten how to do anything like this. I used to have a job where I would use a lot of Unix and I'm pretty sure this can be done pretty easily. I would surely appreciate it if someone would give me a hand.
you could try something like

```
for image in *.jpg; do
convert -size 120x120 $image -resize 120x120 new-$image.jpg
done
```

this would do all the jpg images in the current directory

---

### Post by unckybob on 2012-09-09
Thank you falcon. This is just what I was looking for.

---

