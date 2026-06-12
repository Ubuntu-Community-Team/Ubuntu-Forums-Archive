---
title: "ImageMagick Conversion Question"
date: 2011-02-15
forum: General Help
---

### Post by ngrieb on 2011-02-15
I have been using imagemagick to convert a number of scanned jpg images into multi-page pdf documents. I love it and it works great, but I was wondering if there is a way to create the pdf in the some sort of ordered fashion. Right now I am simply doing:

convert *.jpg Document.pdf 

but am wondering if I can use another argument to get the files arranged in alphabetical order or in timestamped order etc, because currently they are just randomly arranged. I'm sure there is something easy that I am missing.
Thanks in advance.

---

### Post by tredegar on 2011-02-16
**convert** can read a file that is a list of file names to be converted in the order they are listed.
So all you need to do is create that list in the order you want.

So, to make the pdf of jpgs sorted by name try
```
ls *.[jJ][pP][gG] > filelist
convert @filelist Doc.pdf

```
Reverse sorted by name
```
ls *.[jJ][pP][gG] | sort -r > filelist
convert @filelist Doc.pdf

```
Sorted by modification time
```
ls -t  *.[jJ][pP][gG]  > filelist
convert @filelist Doc.pdf

```
I am sure there is a way to get rid of the intermediate step of storing the filenames in **filelist** by having convert read from STDIN but I can't make it work. If you can, tell me how.

**find [options] *.[jJ][pP][gG] | sort [options] > filelist** may be something else to play with (Eg find all jpgs created in the last week, sort them by name and convert them).

Have fun.

---

### Post by ngrieb on 2011-02-16
Thanks, that is very helpful. I found my problem when I took a look at ls through the command line. As you probably already know the order of the files was different than the order shown in the file manager (I wonder why they do that)... i.e. pic-1.jpg is further down the list than pic-11.jpg, however, pic-1.jpg will show up ahead of pic-11.jpg in the file browser. All I had to do was prepend a 0, pic-01.jpg, before the 1 to make things right.

---

### Post by tgalati4 on 2011-02-16
That is standard alpha-numeric ordering.  So yes, you need 001 to come before 010 to come before 100.

---

