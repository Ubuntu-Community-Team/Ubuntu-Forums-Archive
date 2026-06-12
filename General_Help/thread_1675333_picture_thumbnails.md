---
title: "picture thumbnails"
date: 2011-01-25
forum: General Help
---

### Post by qwertyjjj on 2011-01-25
Is there a way to get picture thumbnails on the images in Places-->My Pictures?
They all just appear as blank jpgs at the moment.

---

### Post by hwttdz on 2011-01-25
So you're going to want to check that nautilus (I assume you're using nautilus?) is set to make thumbnails. In nautilus, edit->preferences->preview->(make sure for other previewable files you don't have it set to never, and that the size is sufficiently large).  

I'd try
/bin/rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
which will remove all the thumbnails that didn't work well.  

And finally, you can run touch ~/Pictures/* which will change the timestamp on all your photos and make the thumbnailer make a new one.

---

### Post by qwertyjjj on 2011-01-25
> **hwttdz said:**
> So you're going to want to check that nautilus (I assume you're using nautilus?) is set to make thumbnails. In nautilus, edit->preferences->preview->(make sure for other previewable files you don't have it set to never, and that the size is sufficiently large).  

I'd try
/bin/rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
which will remove all the thumbnails that didn't work well.  

And finally, you can run touch ~/Pictures/* which will change the timestamp on all your photos and make the thumbnailer make a new one.

err...where is nautilus so i can select it?
do i then use the terminal after?

---

### Post by Tamlynmac on 2011-01-25
When you click on my pics in the places menu, it probably opens the nautilus file browser. Once the file browser is open:

Check "edit/preferences/preview tab/other previewable files/show thumbnails"

If it's set to "never" change it to either "local files" and just below that box is another box that limits the size of said files - "only for files smaller than". You may try and set this at 10mb (starting setting). and then adjust as needed.

Depending on available memory and system speed, the loading of these thumbnails may take a few moments. View the first files in the directory and they should be loading thumbnails immediately after opening the directory.

You can change the size of the thumbnails by changing the zoom level - plus & minus magnifying glass in the toolbar. Keep in mind the larger the thumbnail the more memory and possibly longer load times. Depending on the number of pics in the directory.

Good Luck & hope this helps

---

