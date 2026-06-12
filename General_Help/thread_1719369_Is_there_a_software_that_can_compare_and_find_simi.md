---
title: "Is there a software that can compare and find similar &amp; duplicate images for ubuntu?"
date: 2011-04-01
forum: General Help
---

### Post by YQ002lc2 on 2011-04-01
Here's the problem I hope to solve:

I had to recover a hard drive with pictures and other data on it after the file system was erased. Now, in some cases there are 5 or more instances of the same image with different sizes and different file names. Sometimes the images are also in different formats such as jpeg or pnm...

Some of these images may be duplicates of images in a backup hard drive.

I am just asking to see if there is a software that can visually compare images, find visual similarities, and ask me which to keep.

Thanks a lot!

jpinson

---

### Post by bodhi.zazen on 2011-04-01
[http://www.cyberciti.biz/faq/linux-unix-finds-duplicate-files-in-given-directories/](http://www.cyberciti.biz/faq/linux-unix-finds-duplicate-files-in-given-directories/)

---

### Post by YQ002lc2 on 2011-04-01
Thanks bodhi.zazen,

I used "fdupes" per your suggestion. It found the files that were identical in their information despite differences in:
filename, file format, and size,

I also did some searching in "synaptic" and found a package called "findimagedupes".   

I had to use this link to fix a small error with perl.   [http://ubuntuforums.org/archive/index.php/t-1610258.html](http://ubuntuforums.org/archive/index.php/t-1610258.html)

It actually does a lot of the same stuff, but with images. It found visually identical images that were different sizes and in different file formats.

I will play around with these more and edit this post with more information as I find it.

Thanks again for pointing me in the right direction.

jpinson

---

### Post by bodhi.zazen on 2011-04-01
> **jpinson said:**
> Thanks bodhi.zazen,

I used "fdupes" per your suggestion. It found the files that were identical in their information despite differences in:
filename, file format, and size,

I also did some searching in "synaptic" and found a package called "findimagedupes".   

I had to use this link to fix a small error with perl.   [http://ubuntuforums.org/archive/index.php/t-1610258.html](http://ubuntuforums.org/archive/index.php/t-1610258.html)

It actually does a lot of the same stuff, but with images. It found visually identical images that were different sizes and in different file formats.

I will play around with these more and edit this post with more information as I find it.

Thanks again for pointing me in the right direction.

jpinson

you are most welcome. Just take care with the -d option is all.

---

### Post by LewRockwellFAN on 2011-04-07
There is fslint as well. It is very powerful and isn't restricted to images. If you CAN restrict it to searching for only one file type I haven't figured that out yet. I don't think so, but there is an "advanced search parameters" section I don't understand yet. I'm still learning how to use it efficiently but it is sometimes said that working with smaller chunks of data (say two partitions or 2 directories suspected of having duplicates) rather than just sicing it on all your data at once and doing your duplicate weeding in stages works better. Maybe. I'm trying 2 partitions as I write this. I can say that when you sic it on a LOT of data it takes hours to run before you can start picking what to delete. And it doesn't seem to save the results, so you either have to go through ALL of them before closing it or just accept some wasted processing time doing it again. So I guess I can see some logic in the do-it-a-little-at-a-time approach. One thing about fslint, it finds, DUPLICATES, not merely similar files. I have some file duplicate weeding questions myself and I was searching the forum when I ran across this but I think maybe I should make a separate thread. If you google duplicate file finder linux you'll find about a dozen programs.

---

### Post by Telengard C64 on 2011-04-07
> **jpinson said:**
> I also did some searching in "synaptic" and found a package called "findimagedupes".

```
~$ apt-cache show findimagedupes
Package: findimagedupes
. . .
Description: Finds visually similar or duplicate images
 findimagedupes is a commandline utility which performs a rough
 "visual diff" to two images. This allows you to compare two
 images or a whole tree of images and determine if any are
 similar or identical. On common image types, findimagedupes
 seems to be around 98% accurate.
```

This is good to know! I previously used [SimilarImages](http://similarimages.en.softonic.com/) (which looks abandoned now.) Next time I have the need to cleanup my collection of anime pictures I'll have to try **findimagedupes**.
:guitar:

---

