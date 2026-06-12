---
title: "Using &quot;convert&quot; to make PDFs"
date: 2010-06-16
forum: General Help
---

### Post by Uruz on 2010-06-16
I have been using the terminal command "convert" to make PDFs and I noticed that some of the pictures are out of order. The script I wrote is thus:

> #!/bin/bash

cd /home/zach/Documents/PDFing
convert *.jpg -resize 50% *.png
rm *.jpg
convert *.png Chapter.pdf
rm *.png

During the stage where all the images are .png, they are still ordered properly in the folder. However upon converting to a PDF, some of them are in the wrong places. They are all uniformly named with numbers in the proper order, so that is not an issue.

Is there a way that I can force "convert" to order strictly by name? The man pages were interesting, but did not help me in this situation.

Thank you very much,
Uruz

*Post Scriptum:* I'm running 10.04 LTS Desktop Edition.

---

### Post by kaibob on 2010-06-16
Without additional information, I can't say exactly why the photos are out of order, but I do have a few suggestions that might fix things. 

The first convert command in your script works--after a fashion--but is incorrect in that it produces files with the names *-0.png, *-1.png, and so on. If you have more than 10 PNG files, and depending on your locale setting, this could account for the photos being out of order. You can retain the original file names with the following command line:

```
mogrify -resize 50% -format png *.jpg
```

So, first plug the above command in your shell script and run a test to see if it helps.

Also, unless you have some special need to create and then delete intermediate files in PNG format, you can combine the two convert commands as follows:

```
convert *.jpg -resize 50% -compress JPEG Chapter.pdf
```

Certain version of Imagemagick fail when converting multiple JPG files to a single PDF. If that is an issue, use graphicsmagick instead:

```
gm convert *.jpg -resize 50% -compress JPEG Chapter.pdf
```

Graphicsmagick is not installed by default but is small in size and is in the repo's.

---

### Post by Uruz on 2010-06-17
Excellent, excellent, excellent! I replaced the first line in the script with the one you provided and it worked perfectly!

Just out of curiosity, what's the difference between Convert and Mogrify? I'm guessing it's just a different program, but it seems strange for Ubuntu to come with two very similar programs pre-installed.

One last thing: for some reason, some of the images are .JPG instead of .jpg. Due to case-sensitivity, they get left out. Any easy way to fix this? I don't quite have a grasp on the syntax yet, is there a way I can tell it to do both file types in the same line and at the same time?

Now if only I could get it to add the chapter number and metadata automatically...

**EDIT**
Nevermind the .JPG thing, I fixed it by telling it to convert *.* rather than *.jpg. I'll add an extra line to remove the remaining *.JPG images.

---

### Post by kaibob on 2010-06-17
Convert and mogrify are both a part of the Imagemagick suite of utilities, and they perform pretty much the same function. The command-line sytax is a bit different, and mogrify typically (but not always) overwrites the original file, while convert does not.

REFERENCE:
[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

---

### Post by Uruz on 2010-06-17
Thank you very much!

---

