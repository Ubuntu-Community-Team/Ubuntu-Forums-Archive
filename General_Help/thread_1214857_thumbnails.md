---
title: "thumbnails"
date: 2009-07-16
forum: General Help
---

### Post by John M2009 on 2009-07-16
Is there a way to stop kubuntu saving every single thumbnail to the /home/.thumbnails/normal directory?

---

### Post by josvanr on 2009-09-11
I'm also having trouble with this: I was using kdirstat to clean up my disk but it kept freezing at some point. I discovered that the .thumbnails directory was the problem. There are so many files in there, I dont know how many. I've started rm -r .thumbnails and it has been running for 5 minutes now, meaing that there are... 100.000 files or more? Crazy!

josvanr

---

### Post by josvanr on 2009-09-11
rm just finished removing the .thumbnails directory. Now kdirstat works again.

---

### Post by StuartN on 2009-09-11
In Nautilus go to Edit->Preferences->Preview. The Show thumbnails is set to "Local only" (so it doesn't thumbnail USB or network drives) and files "Smaller than 10 mb" (so it doesn't spend forever thumbnailing movies).

Set Show thumbnails to "Never".

---

### Post by whozai_min on 2009-09-12
i also have this problem..but this time, after follow StuartN method i still get dat thumbnail, but this when i view my photo.

---

### Post by StuartN on 2009-09-12
> **whozai_min said:**
> i still get dat thumbnail, but this when i view my photo.

The settings in my earlier post disable the creation of thumbnails by Nautilus while browsing directories. The image viewer application (Eye of Gnome) will still create thumbnails for each image viewed, and for entire folders if collections are displayed. EoG has no preference setting to disable thumbnail creation.

To disable thumbnail creation for ALL applications you can open Applications->System tools->Configuration editor (or "gconf-editor" in terminal) and browse to /desktop/gnome/thumbnail_cache. Then set either maximum_age or maximum_size to 0. All thumbnails will be gone when you next log in, and will not be recreated by any application.

---

