---
title: "Is it possible to shrink multiple images files at once?"
date: 2010-11-12
forum: General Help
---

### Post by sofasurfer on 2010-11-12
I have a folder full of image files. They are large files and they only need to be large icon size...manybe 2 inches wide. Is there a way to convert them without editing each file individually?

---

### Post by bioterror on 2010-11-12
> **sofasurfer said:**
> I have a folder full of image files. They are large files and they only need to be large icon size...manybe 2 inches wide. Is there a way to convert them without editing each file individually?

Yes,

```

sudo apt-get install imagemagick
mogrify -resize 1440x960 *.jpg

```

---

### Post by sofasurfer on 2010-11-12
Thanks for the info. I'll need to study before I attempt to use that program. Looks like it does just about everything.
Sorry I did not make myself clear. I would prefer to do a mass resize...all images at once. Is that possible?

---

### Post by mcduck on 2010-11-12
The command provided does exactly that. (although I prefer using *convert* instead of *mogrify*, both work pretty much the same way but convert leaves the original images intact while mogrify overwrites them)

You may also want  to try nautilus-image-converter , which adds option to resize images into the right-click menu of your file manager (you can select multiple iamges at time to resize them all) or Phatch, which is a simple graphical tool for batch processing of images.

---

### Post by sofasurfer on 2010-11-12
One more question...
I used nautilus-image-converter and I like it very much. 
Here the question. I opened my folder that contained the pics. I converted all of them. I noticed that the first 3 pics showed as icons or thumbnails. The rest of the pics showed as that generic little icon that looks like a drawing of a tree. The point is that it was not a thumbnail of the image but a generic thumbnail. 
Anyway, I have noticed this since the beginning of time, that sometimes icons show as the file image and sometime they show as a generic icon. Anyway, I compared the "properties" info on the differant images. I notices that under "permissions", "allow executing as program" needs to be checked in order for the pic icons to show. If this is not checked you will see a generic icon AND the resizing that had been done does not show. The properties, when right clicking on these generic icons showed sizes of around 50mg. After checking the "allow executing as program" box, the "real" icons showed as 300kb.
So, what is that "allow executing as program" box and why does it affect the image size? I though that only affected things like scripts.

Sorry this was so long but I didn't know how else to say it.
And thanks for the help.

EDIT:: Actually, I just noticed that on some of the images the "allow executing as program" box is already checked and if you uncheck it the real icon appears and the resize kicks in. Just the opposite of what I said above. Hmmmm.....

---

### Post by 73ckn797 on 2010-11-12
The Nautilus image converter works well for the, sometimes, 100 photos I need to resize everyday.

---

### Post by sofasurfer on 2010-11-13
I moved this post to a new thread...
[http://ubuntuforums.org/showthread.php?p=10112099#post10112099](http://ubuntuforums.org/showthread.php?p=10112099#post10112099)

---

