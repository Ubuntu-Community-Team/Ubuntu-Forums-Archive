---
title: "Finding a simple OCR"
date: 2010-09-26
forum: General Help
---

### Post by TBruff15 on 2010-09-26
I am a high school student and i have spent hours online looking for a simple ocr program to use with ubuntu. So far everyone i have installed does not appear in applications so i do not know how to run the program. There are a few that are command line based, but those seem really difficult to use I have tried gocr could not figure out how to use it easyocr the same basically every one i could find i tried clara it look promising if i could just run it does clara have a GUI interface something simple, and if not can someone please direct me to an ocr that does while giving me detailed directions on how to get it to work Ex (how to install and how to run, and possibly how to put an icon on the desktop) I am sorry if this seems like alot, but i have been trying to figure this out for hours

---

### Post by davidvandoren on 2010-09-27
try to get an old version from ABByy fine-reader 4.1 or so.
It's a really nice windows based OCR software which works under wine. You'll need to install wine though.

Then instead of exporting the files just save them and then open with open office. It will keep all the pictures and layout for you this way. 

only some functions like spell check won't work but with a recognition of more than 99% not needed anyway.

---

### Post by TBruff15 on 2010-09-27
I will try wine, but every time I set a program up with wine it does not work can you give me step instructions on how to get it to work i just started using Ubuntu and it is different

---

### Post by coffeecat on 2010-09-27
@TBruff15, I know you are not happy with the command line, but I suggest you try tesseract. It is command line only but it is very easy to use. The apps based on gocr give inferior results. For more see my post here:

[http://ubuntuforums.org/showpost.php?p=8177267&postcount=2](http://ubuntuforums.org/showpost.php?p=8177267&postcount=2)

---

### Post by StuartN on 2010-09-27
> **coffeecat said:**
> @TBruff15, I know you are not happy with the command line, but I suggest you try tesseract. It is command line only but it is very easy to use.

I found that a black & white (binary) image file at 300 dpi works well, but that XSane saves with a .tiff extension, whereas tesseract requires a .tif extension. **tesseract image.tif text** generates text.txt (do not include the .txt extension, or you get text.txt.txt).

---

### Post by pentask on 2010-10-16
If you call Xsane via GIMP, you can save with .tif extension and it works fine (for me anyway using Ununtu10.4)

---

### Post by DavePlummer on 2010-10-16
There are at least two free online services that work well. Unfortunately, I don't have the URLs handy, but Google search should find them.

---

