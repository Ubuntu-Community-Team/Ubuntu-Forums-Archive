---
title: "Is there a way to recursively invert all images in a directory?"
date: 2011-01-08
forum: General Help
---

### Post by Mr_VeRiTy on 2011-01-08
Hi, I need to invert the colors of a lot of images that are in different folders in the same directory, is there a way to use image magic or something to do this in only a few commands?

---

### Post by Zhuoxi on 2011-01-08
> **Mr_VeRiTy said:**
> Hi, I need to invert the colors of a lot of images that are in different folders in the same directory, is there a way to use image magic or something to do this in only a few commands?
what command do you use to invert only a single imag?
then you can write a bash script first to enumerate the images then to invert each.

---

### Post by Mr_VeRiTy on 2011-01-08
> **Zhuoxi said:**
> what command do you use to invert only a single imag?
then you can write a bash script first to enumerate the images then to invert each.

I don't know, I tried to find a command that does a single image but I couldn't find that either.

---

### Post by Zhuoxi on 2011-01-08
> **Mr_VeRiTy said:**
> I don't know, I tried to find a command that does a single image but I couldn't find that either.
then do you know what format are your images in?

---

### Post by Zhuoxi on 2011-01-08
> **Mr_VeRiTy said:**
> I don't know, I tried to find a command that does a single image but I couldn't find that either.
if your images are in popular formats such as uncompressed bitmap or jpeg et al., there must be some useful tools to do that on a single image for you. if not, once you got the specification of your image you can write a program to do this.

---

### Post by Mr_VeRiTy on 2011-01-08
> **Zhuoxi said:**
> then do you know what format are your images in?
They are all in png format.

---

### Post by Mr_VeRiTy on 2011-01-08
> **Zhuoxi said:**
> if your images are in popular formats such as uncompressed bitmap or jpeg et al., there must be some useful tools to do that on a single image for you. if not, once you got the specification of your image you can write a program to do this.
I don't know how to write programs, I'm not new to computers but I'm no programmer either. I may be able to write a small, simple script as long as I find the right tutorials somewhere... but other than that I have no talent for programming.

---

### Post by Idefix82 on 2011-01-08
First, install Image Magic via synaptic.

Go into the root of the directory tree in which you want to negate the pictures, create a text file there, paste this into the file:
```
#!/bin/sh
for file in "$@"
do
  convert "$file" -negate "$file"
done

```
and save as myconvert.sh. Now, backup all the pictures somewhere, open the terminal, change into the directory where you saved your script and where the pictures reside and do this:
```

chmod 755 myconvert.sh
find . -type f -name "*.png" -exec ./myconvert.sh '{}' \;

```

Note, that this will overwrite the pictures in the directory from which you are executing the script **and all subdirectories** with the inverted ones, so you must make a backup copy.

---

### Post by Mr_VeRiTy on 2011-01-08
> **Idefix82 said:**
> First, install Image Magic via synaptic.

Go into the root of the directory tree in which you want to negate the pictures, create a text file there, paste this into the file:
```
#!/bin/sh
for file in "$@"
do
  convert "$file" -negate "$file"
done

```
and save as myconvert.sh. Now, backup all the pictures somewhere, open the terminal, change into the directory where you saved your script and where the pictures reside and do this:
```

chmod 755 myconvert.sh
find . -type f -name "*.png" -exec ./myconvert.sh '{}' \;

```

Note, that this will overwrite the pictures in the directory from which you are executing the script **and all subdirectories** with the inverted ones, so you must make a backup copy.
This is exactly what I needed thank you!

---

### Post by Idefix82 on 2011-01-08
You are welcome! Note that Image Magic is full of fantastic utilities to modify image files through the command line interface. And you often don't need to write a separate script file, since it has lots of batch job capability built in.

---

