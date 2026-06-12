---
title: "Cannot open .cr2 Canon RAW files"
date: 2012-06-30
forum: General Help
---

### Post by WongFuChu on 2012-06-30
Using eog, the images only appear as the white/grey checker board background. I've been searching for multiple apps to open it, but have not found one that works in the repository. Does anyone know of a good app that works? I know Gimp and Shotwell work, but I was hoping to find a program where I can navigate to the next image (just like eog). 

Also, while I'm asking, is there a way to manually set the default application to open a file with (e.g. Properties->Open With)? For .cr2 files, nautilus freezes as soon as I click on Properties.

Currently using Ubuntu 12.04

---

### Post by robert shearer on 2012-06-30
Shotwell does this.

Simply find an image, right click on it an chose 'open with..shotwell.'
When it opens you will see 2 arrows at bottom right that allow you to step back or forward to the next image in the current folder. ie where you opened the current image from.

---

### Post by WongFuChu on 2012-06-30
I can open a single cr2 image with shotwell, but I cannot navigate to any other cr2 images with the prev/next arrows at the bottom right; the arrows are there, but are unclickable and I can't seem to navigate through the menubar either. It does work for jpeg's though.

---

### Post by robert shearer on 2012-07-01
:( 
Glad I have a Pentax then :)
Does your canon give a choice of raw file types ? or are you limited to their .cr2 only..?
If there is a choice to change in-camera then you may be able to use a raw file type more universally compatable rather than being tied to the canon only format...?

However, you could import the .cr2 files into gimp then 'save as' another format...

Links...
[http://www.fileinfo.com/extension/cr2](http://www.fileinfo.com/extension/cr2)
[http://www.madox.net/blog/2008/11/25/how-to-open-canon-cr2-raws-in-ubuntu/](http://www.madox.net/blog/2008/11/25/how-to-open-canon-cr2-raws-in-ubuntu/)
[http://platonic.techfiz.info/2010/11/cr2-canon-raw-file-management-in-ubuntu/](http://platonic.techfiz.info/2010/11/cr2-canon-raw-file-management-in-ubuntu/)
[http://ubuntu.kinjileslie.com/2011/10/working-with-canon-cr2-files.html](http://ubuntu.kinjileslie.com/2011/10/working-with-canon-cr2-files.html)
[http://ufraw.sourceforge.net/Cameras.html](http://ufraw.sourceforge.net/Cameras.html)

---

### Post by IanW on 2012-07-01
Darktable will deal with .cr2 files, it is to Adobe Lightroom as GIMP is to Adobe Photoshop.

---

### Post by robert shearer on 2012-07-01
> **IanW said:**
> Darktable will deal with .cr2 files, it is to Adobe Lightroom as GIMP is to Adobe Photoshop.

Excellent..!  so open a terminal and run...
```
sudo apt-get install darktable
```

Then open the dash and type **darktable**

thank you to IanW

---

### Post by eric-yorba on 2012-07-02
> **WongFuChu said:**
> I can open a single cr2 image with shotwell, but I cannot navigate to any other cr2 images with the prev/next arrows at the bottom right; the arrows are there, but are unclickable and I can't seem to navigate through the menubar either. It does work for jpeg's though.

You just need to be more patient!  Shotwell has a bug where large files (such as RAW photos) are slow to browse when the app first starts up in "direct" mode.  Give it a few seconds and the arrows will activate.

---

