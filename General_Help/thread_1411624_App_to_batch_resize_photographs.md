---
title: "App to batch resize photographs"
date: 2010-02-20
forum: General Help
---

### Post by alan_uk on 2010-02-20
I am resizing my photographs to reduce file size for a photo display unit.  Although doing this picture by picture is no problem I have hundreds to do.  Is there an app that batch them for me?

Thanks

Alan

---

### Post by HermanAB on 2010-02-20
Imagemagic of course!

---

### Post by .nedberg on 2010-02-20
I created a script to do this once. Here it is:
```

#!/bin/bash

function resize {

	mogrify -quality 75 -resize 960 ${1}
	h=$(identify -format %h ${1})
	if [ $h -gt 640 ]; then
		cut=$((($h-640)/2))
		mogrify -quality 100 -shave 0x$cut ${1}
	fi
}

for i in `ls -1 *.JPG *.jpg`; do
	resize ${i}
done

```

Run it inside a folder with jpg files and it will resize all the files (it will overwrite the originals).

Play with the sizes to fit your needs (max width is 960 and max height is 640).

EDIT: You need to have imagemagick installed!

---

### Post by mcduck on 2010-02-20
I use Imagemagick for this kind of stuff, so +1 for that of course.

But in case you are not ready to use a command-line based image editor you might want to try Phatch, which is a graphical tool for batch processing images. Not nearly as powerfull as Imagemagick+shell scripting combiantion can be, but handles most common takss very well.

---

### Post by mkvnmtr on 2010-02-20
I have been usinf Nautilus to do 10 to 20 at a time. I guess it would do 100 just as easy. I right click on them and choose resize. A nice menue comes up and gives me the choice af size and if I wish to produce a copy ar replace. Not very geeky but it is right there without opening a terminal.

---

### Post by kaibob on 2010-02-20
> I have been usinf Nautilus to do 10 to 20 at a time. I guess it would do 100 just as easy. I right click on them and choose resize. A nice menue comes up and gives me the choice af size and if I wish to produce a copy ar replace. Not very geeky but it is right there without opening a terminal.

I believe this forum member is referring to the Nautilus Image Converter. I don't think it's installed by default but is available in the repositories. I also use and recommend this utility.

[http://www.bitron.ch/software/nautilus-image-converter.php](http://www.bitron.ch/software/nautilus-image-converter.php)

---

### Post by alexbardasu on 2010-02-20
I recommend David's Batch Processor if you are a fan of GIMP.
It's really easy to install and it has a nice GUI.

You can get it from [here]("http://members.ozemail.com.au/~hodsond/dbp.html").

---

### Post by jalirious on 2010-03-18
The nautilus-image-converter just utilitises imagemagick's covert tool.

---

