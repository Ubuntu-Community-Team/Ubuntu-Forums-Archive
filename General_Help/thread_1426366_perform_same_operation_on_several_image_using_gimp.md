---
title: "perform same operation on several image using gimp....."
date: 2010-03-10
forum: General Help
---

### Post by muctadir on 2010-03-10
well. i have to resize about 300 image. with gimp it will take too much time if i do it manually. i googled for help and found [this]("http://members.ozemail.com.au/~hodsond/dbp.html") solution....

i downloaded [this]("http://www.ozemail.com.au/~hodsond/dbpSrc-1-1-9.tgz"). but i dont know how to use it.

please help me here........

---

### Post by zerubbabel on 2010-03-10
xnview ([www.xnview.com](www.xnview.com)) is a free image viewer with excellent batch processing capabilities. It does have a Linux version, but the Windows version is more robust and runs very well under Wine.

---

### Post by ajgreeny on 2010-03-10
If you want a gui there are many ways, but you can do it much easier and quicker with the ```
convert
``` command.  See ```
man convert
```for all the details.

---

### Post by muctadir on 2010-03-10
> **ajgreeny said:**
> If you want a gui there are many ways, but you can do it much easier and quicker with the ```
convert
``` command.  See ```
man convert
```for all the details.

sorry, but i can't find this command

---

### Post by ajgreeny on 2010-03-10
Oh heck, sorry!  It is part of imagemagick which I think used to be installed by default, but no longer is.

If you want to look into this further use ```
sudo apt-get install imagemagick
```and try again.

---

### Post by muctadir on 2010-03-11
thank you for your advise....
i am going to try that.....

---

### Post by zerubbabel on 2010-03-11
Just noticed that the folks who make XnView also have NConvert freeware batch utility for the Linux platform ([http://www.xnview.com/en/nconvert.html):](http://www.xnview.com/en/nconvert.html):)

Import about 400 graphic file formats
Export about 40 graphic file formats
Multipage TIFF, Animated GIF, Animated ICO support
Resize
Adjust brightness, contrast...
Modify number of colors
Apply filters (blur, average, emboss, ...)
Apply effects (lens, wave, ...)
Etc...

---

