---
title: "Restoring F-Spot?"
date: 2010-07-31
forum: General Help
---

### Post by carbon512 on 2010-07-31
Hi all --

newbie still here, been using Ubuntu a few months. Had about 400 photos in F-Spot, tagged, etc. Imported a few more photos from someone else's SD card last night and F-spot looked just fine.

Today, F-spot shows no photos at all... no tags, nothing at all.

I still have the photos on my hard drive, but I really would hate to re-import from scratch and re-create all those tags. 

 Does F-spot back up the database anywhere? Can I look somewhere to see if the database, or an older version, is hanging out somewhere?SHould I re-start my computer, or will that limit my chances of restoring the good F-spot status I had last night? (Have not re-started since then)

The only other odd thing was a message today that said my computer had only 2 GB free hard drive space -- not true, but I am not sure how this is all partitioned. A friend initially set up the Ubuntu partition for me and I dont recall much about how to do that, check it, or what it all means. I installed everything and then took off for Alaska where I have limited internet access and limited time to lean Ubuntu the way I had wanted to... Here is some relevant info though about free drive space:

250 GB hard disk: Acer - total capacity 170 GB, free space 145 GB
250 GB hard disk: SYSTEM RESERVED - total capacity 100 MB, 75.6 MB free
File System: folder (inode/directory), still counting files, does not show disk graphic or report total capacity; says 2.0 GB free. This also shows "some contents unreadable"

I am confused, obviously... and want to get my f-spot thumbnails and tags and full browser back!

I do have windows installed in a partition on here but never use it.

Any ideas or help? I apologize for needing some step-by-step walk thru on it all.

Thanks!~

(using Ubuntu 10.04 LTS, run upgrades regularly)

---

### Post by carbon512 on 2010-07-31
Quick update -- it appears that my original photos are NOT any longer in my home/pictures/photos directory! I had been having f-spot copy them from my camera to that folder and had quite a few folders autonamed by date in there. Most of them are gone now...

very sad. Apparently something happened when I imported a few selected photos from the other SD card... I have no idea what though. Any ideas for restoring? Finding the files? There is nothing in the trash... I dont think I emptied it recently but I cant be sure.

---

### Post by bobcollard on 2010-07-31
First try Find>By Import Roll>Clear Roll Filter  To see all of your pictures.  If not, then Import new images>usr name/pictures/photos  Will restore all you have saved in your home folder.

---

### Post by carbon512 on 2010-07-31
That option is greyed out. F-Spot looks as if it is a brand-new install; doesn't have any filters or anything.
I'm hoping to not have to re-tag all my photos but if I have to I will just re-import them as you suggest.

(The missing photo sub-folders now DO appear again in my home folder... Very odd. I think a restart is in order...)

---

### Post by bobcollard on 2010-07-31
> **carbon512 said:**
> That option is greyed out. F-Spot looks as if it is a brand-new install; doesn't have any filters or anything.
I'm hoping to not have to re-tag all my photos but if I have to I will just re-import them as you suggest.

(The missing photo sub-folders now DO appear again in my home folder... Very odd. I think a restart is in order...)
If you re-import them they may still have the tags, depending on how you tagged them.

---

### Post by carbon512 on 2010-07-31
yay a different search returned this thread: 
[http://ubuntuforums.org/showthread.php?t=1455551](http://ubuntuforums.org/showthread.php?t=1455551)

I copied the database back to /.config/f-spot/photos.db and all is good!

weird dont know why that happened...

---

### Post by deserthowler on 2010-07-31
> **carbon512 said:**
> yay a different search returned this thread: 
[http://ubuntuforums.org/showthread.php?t=1455551](http://ubuntuforums.org/showthread.php?t=1455551)

I copied the database back to /.config/f-spot/photos.db and all is good!

weird dont know why that happened...

Please mark solved

Earl

---

