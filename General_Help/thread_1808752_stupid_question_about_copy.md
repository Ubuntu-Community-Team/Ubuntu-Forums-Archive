---
title: "stupid question about copy"
date: 2011-07-20
forum: General Help
---

### Post by avix on 2011-07-20
I have 97 folders with various types of files in them. I want to move just all the graphics into one folder. I have googled and looked and read manuals to try to figure out a way to  just do a command to go through each folder and copy all the graphics files to one folder so I can avoid having to go into each folder and do it by hand.

help?

---

### Post by nothingspecial on 2011-07-20
The command depends on the file structure and the name of the files.

Are the 97 folders all in one folder? or spread out.

Do they all have the same file extensions or different ones (jpg, Jpeg, PNG. etc)
More info please.

---

### Post by avix on 2011-07-20
they are all under one folder IE: /mnt/storage/427/* and need to go to /mnt/storage/temp. the 97 folders are all under 427.

---

### Post by MG&amp;TL on 2011-07-20
How confident are you with a terminal? (not really a question of how **good** you are with it, more how much you're prepared to jump in.)

[http://snippets.dzone.com/posts/show/2059](http://snippets.dzone.com/posts/show/2059) -not exactly what you are looking for, but it might get you started. This works, however if your images are in different formats, you will have to do this multiple times. (jpg, bitmap, RAW, TIFF, png, svg, or whatever.

It still doesn't copy them. I shall endeavour to find out. I don't see there being a user-friendly solution unfortunately.

---

### Post by nothingspecial on 2011-07-20
> **avix said:**
> they are all under one folder IE: /mnt/storage/427/* and need to go to /mnt/storage/temp. the 97 folders are all under 427.

But you haven't told us the naming if any. If they were all ended with .jpg them
```

cp /mnt/storage/427/*/*.jpg /mnt/storage/temp/
```

If not then you need another solution.

---

### Post by nothingspecial on 2011-07-20
> **MG&TL said:**
> How confident are you with a terminal? (not really a question of how **good** you are with it, more how much you're prepared to jump in.)

[http://snippets.dzone.com/posts/show/2059](http://snippets.dzone.com/posts/show/2059) -not exactly what you are looking for, but it might get you started. This works, however if your images are in different formats, you will have to do this multiple times. (jpg, bitmap, RAW, TIFF, png, svg, or whatever.

It still doesn't copy them. I shall endeavour to find out. I don't see there being a user-friendly solution unfortunately.

Find will not be necessary in this case, since we know where the files are....... and don't need to find them.

---

### Post by MG&amp;TL on 2011-07-20
It would appear that this does the biz, but I haven't got it to work yet. There's nothing to suggest  it won't, though.

[http://stackoverflow.com/questions/2815532/how-does-one-find-and-copy-files-of-the-same-extension-in-different-directories](http://stackoverflow.com/questions/2815532/how-does-one-find-and-copy-files-of-the-same-extension-in-different-directories)

Problem solved? Or am I barking up the wrong tree here?

---

### Post by avix on 2011-07-20
:/mnt/storage/p/427$ cp /mnt/storage/427/*/*.jpg /mnt/storage/temp/
cp: cannot stat `/mnt/storage/427/*/*.jpg': No such file or directory

---

### Post by avix on 2011-07-20
DOH! DOH! DOH! DOH!

I forgot one level of directories

---

### Post by nothingspecial on 2011-07-20
> **avix said:**
> :/mnt/storage/p/427$ cp /mnt/storage/427/*/*.jpg /mnt/storage/temp/
cp: cannot stat `/mnt/storage/427/*/*.jpg': No such file or directory

hmmm

---

### Post by MG&amp;TL on 2011-07-20
Humph. IDK.

The only reason I though to use find was that there are 97 separate directories, and assumable they have sub-directories?

EDIT: Jeez, forums move fast sometimes.

---

### Post by nothingspecial on 2011-07-20
So did it work?

---

### Post by nothingspecial on 2011-07-20
An extra * for an extra level.

cp /mnt/storage/427/*/*/*.jpg /mnt/storage/temp/

---

### Post by avix on 2011-07-20
I am pleased to report that with the help of you Gentleman it appears to be copying things faster than microsoft can trash linux. 

damn I love the linux world. thanks all you guys

---

### Post by nothingspecial on 2011-07-20
:d

---

### Post by TannerD on 2011-07-20
I just skimmed the previous replies. 
Goto the top folder (whatever folder has all the other folders in it that you need to search through) and open up "Find...". It should be under one the menu's in Nautilus. When it opens type "*.png" without quotes and hit enter. Do this with each image file extension (.jpg, .png, .tiff, etc.) with an asterisk at the beginning. This will be kind of slow because you'll have to copy the images from each results to where-ever you want to copy them.
Another way to do it (I don't remember for sure about this in Nautilus because I'm on Kubuntu now and this is a feature in Dolphin. Granted I can't get it to work...) is to use the Filter feature. If I'm right, the filter feature will give you the ability to show just images and nothing else.
The screenshot just shows an example of the filter toolbar and the find feature in Dolphin as an example.

---

### Post by MG&amp;TL on 2011-07-20
No problem, avix. Even if I was barking up the wrong tree.

Typical, TannerD As soon as we find a (difficult) terminal solution, somebody pops up saying 'look, you just click here, there, done.' It just won't do. :P

---

### Post by avix on 2011-07-21
I thank you all. when I got it all done it was some 87,000 photos. now I can get them all into a photo management system. (my wife is SO going to owe me for this!)

---

