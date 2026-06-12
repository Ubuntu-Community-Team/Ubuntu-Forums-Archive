---
title: "Very slow cbr thumbnail creation after upgrade to 10.04"
date: 2010-05-14
forum: General Help
---

### Post by StGermain on 2010-05-14
Cbr files are comics and I use comix to read them, when I move them around sorting them out or renaming a folder the thumbnails are recreated. While this went really fast in 7.04 to 9.10 it is now incredibly slow, it looks as if the files have to be read in by the system completely in order to be created, this is especially obvious when they are on a network drive.

Any help would be appreciated.

---

### Post by betlog on 2010-08-23
Yeah, I have the same problem. Here is another thread with the same issues.
http://ubuntuforums.org/showthread.php?p=9758030

I think we need to persue this. Currently its extremely unsatisfactory on large folders, and frequently crashes dolphin if i try to close the dolphin window too quickly when a thumb refresh is happening.

---

### Post by betlog on 2010-08-24
Ok, after some research I think I have found *my* issue.

My issue is with what appears to be some kind of malfunctional  behaviour, because on each login it seems to require a rebuild  of many  thumbs of *larger* folders.
It's possible its just slow to load them all into memory, but I suspect  it is actually rewriting many of the thumbs for stuff it already has a  thumb.
It seems I am simply overflowing the limit for stored thumbs, so the system is forced to regenerate them every time I relog.

so:
gconf-editor > desktop > gnome > thumbnail_cache > maximum_size=512
...and 512Mb seems to be grossly inadequate for even a couple of the folders I frequently open and  therefore need to be efficiently thumbnailed on my system. (note the currenly 4.1gb of thumbs I have just from one folder of my larger image collections)

caveat:
 I do accept that 11000 files, 63 folders, at ~2.5gb of stuff in one  folder is a fairly large amount to make thumbnails for, however I am sure it's not too atypical.

---

### Post by betlog on 2010-08-24
Hmm.
I set my thumb cache to 10240Mb and rebooted
I browsed a few larger folders with dolphin and allowed all images to thumbnail
However when i go back to a previously cached folder the images take some time to load again.. but they do seem to load faster, so i assume the time taken is simply from finding and pulling them from the cache.

QUESTION: does the cache retrieval process always process in order of image name? if so this could be modified to process in the order of the folder being displayed (I always sort image folders by Date, descending, show folders first)

also, I read:
"If a program needs a thumbnail for an image file which is 	smaller than 128x128 pixel it doesn't need to save it at all."
on http://jens.triq.net/thumbnail-spec/creation.html

QUESTION: I can see that it does indeed store all of my (64x64 preview size) thumbs, however instead of normal=128x128 and large=256x256... perhaps a more useful (and faster, more generally apropriate) scale would be small=64x64 ?
Does anyone have an opinion?

---

### Post by lavinog on 2010-08-24
> **betlog said:**
> Hmm.
I set my thumb cache to 10240Mb and rebooted
I browsed a few larger folders with dolphin and allowed all images to thumbnail
However when i go back to a previously cached folder the images take some time to load again.. but they do seem to load faster, so i assume the time taken is simply from finding and pulling them from the cache.


If the folder has a large number of images, you could have some extra overhead because for each file, the thumbnailer needs to calculate a MD5 for each URI.  Then the md5 is used to locate the thumbnail.


> 
QUESTION: does the cache retrieval process always process in order of image name? if so this could be modified to process in the order of the folder being displayed (I always sort image folders by Date, descending, show folders first)

Nothing is implemented.  There is nothing to prevent it from being designed that way.  Maybe you can file a bug report.

> 
also, I read:
"If a program needs a thumbnail for an image file which is 	smaller than 128x128 pixel it doesn't need to save it at all."
on [http://jens.triq.net/thumbnail-spec/creation.html](http://jens.triq.net/thumbnail-spec/creation.html)

QUESTION: I can see that it does indeed store all of my (64x64 preview size) thumbs, however instead of normal=128x128 and large=256x256... perhaps a more useful (and faster, more generally apropriate) scale would be small=64x64 ?
Does anyone have an opinion?

I haven't tested that out, but I do know that if the image format is not a 24bit png with alpha channel then it will need to make a thumbnail.
It might be that it is quicker to just make a thumbnail, than read a file once to determine if it meets the criteria, then read again to make the thumbnail.

I wrote a script once that can force the generation of thumbnails of a given folder from the command line.
I don't remember what computer that was on though, but I can see if I still have it.

---

### Post by betlog on 2010-08-24
Hmm, i hope i did that right
[http://brainstorm.ubuntu.com/idea/25678/](http://brainstorm.ubuntu.com/idea/25678/)

..what component is it that actually generates the thumbs... or would be responsible for the communication of how to deliver the sorting option? I guess it would need to involve modification of both file managers in general, and the thumbnail generation/delivery...

---

### Post by betlog on 2010-08-24
> **lavinog said:**
> you could have some extra overhead because for each file, the thumbnailer needs to calculate a MD5 for each URI.
 indeed. However in my case the problem relates more to how the images jump around and change their sequence, more than the speed.

---

### Post by betlog on 2010-08-24
> **lavinog said:**
> IIt might be that it is quicker to just make a thumbnail, than read a  file once to determine if it meets the criteria, then read again to make  the thumbnail..
What I mean is maybe 128x128 is a little too large, and maybe if it was smaller some loading speed gains could be made.
Personally I either have huge thumbs, or something good for displaying hundreds of pages of images as densely as possible while still being discernible. So for me it's either relatively small, or huge. 
Also, due to understanding a little aboout graphics I try to set my display size the same as my storage size for stuff... so no intermediate calculation needs be done to display the zillions of images i frequently peruse.  Being able to define the large and small thumbnail *storage* size to correlate with users preferred *display* sizes would be awesome for this.
...so I guess thats another feature requestright there :]
[http://brainstorm.ubuntu.com/idea/25679/](http://brainstorm.ubuntu.com/idea/25679/)

---

