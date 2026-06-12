---
title: "Resize Pics"
date: 2010-05-19
forum: General Help
---

### Post by wombil on 2010-05-19
hey Guys,My query is ,"What is the best/easiest way to resize photos for Email"?
I notice that my photos are saved at 1 or 2 mb each which is too big to email,particularly if there are a few of them.Last lot of 5 amounted to 11.4 mb and with a lot of mucking around I finally got them to 2.4 but still a bit big.I right click the pics and use the"send to" bit in the dialog box which compresses them in zip. but does not make them small enough.I have been reading the forum here and gThumb has been mentioned.Would this program do what I need ok? I am running ubuntu 8.04
Thanks for looking.
wombil.

---

### Post by amite on 2010-05-19
$ sudo apt-get install imagemagic

$ man mogrify

i think it will work for u!:smile:

---

### Post by jobix on 2010-05-19
"mogrify" overwrites the original (as per its man page). You might want to use "convert". You can also "gimp" to crop and scale down the images to bring down the size before emailing.

---

### Post by wombil on 2010-05-19
Gee that was quick,16 minutes.
Thanks fellers,will try that.

---

### Post by ssj6akshat on 2010-05-19
You can try Phatch by Stani

sudo apt-get install phatch

---

### Post by ryan858 on 2010-05-19
GIMP isn't the fastest, or easiest to use solely for resizing or compressing pictures, but it's overall one of the best photo editing utilities around. You can use it to resize (as in width and height), compress, convert, touch-up, and many, many other things. Once you learn how to do the basic stuff it's a breeze and fast to process images for the web, or whatever you want. I think it has a batch processing method, so you can resize, compress, or convert an entire collection of images in no time.

---

### Post by wombil on 2010-05-19
Sorry guys,the terminal says "command not found" for the image magic.Will try phatch.
Gimp seems to be the go if i can find out how to do pics by batch.

---

### Post by wombil on 2010-05-19
phatch has loaded ok,will try these later,thanks guys

---

### Post by veko on 2010-05-19
There is Nautilus extension called [nautilus-image-converter]("http://www.bitron.ch/software/nautilus-image-converter.php").

sudo apt-get install nautilus-image-converter

It adds resize and rotate options in right click context menu for images. Easy to use and works fast. It uses ImageMagick, by the way.

Otherwise, you can use mogrify from ImageMagick directly as suggested above, or Gimp. The first one uses command line, which is good but can be slow to use if you don't remember the options, and the latter one is bit of an overkill for this purpose.

I did myself once write a script that uses mogrify with zenity GUI to quickly resize images, but this was before I discovered nautilus-image-converter. Lucky thing though, you learn best by doing things yourself. I don't have the script on hand right now, but I could post it later just to give some ideas.

---

### Post by amite on 2010-05-19
> **wombil said:**
> Sorry guys,the terminal says "command not found" for the image magic.

it's not image magic ; it is imagemagick

---

### Post by elliotn on 2010-05-19
i prefer GIMP

---

### Post by wombil on 2010-05-19
You are right Amite but I copied and pasted the command into terminal and did use ,"imagemagic",no italics of course.

---

### Post by veko on 2010-05-19
> **wombil said:**
> You are right Amite but I copied and pasted the command into terminal and did use ,"imagemagic",no italics of course.

ImageMagick is a package containing several programs. There is no such command as "imagemagick", as far as I know.

You can e.g. run "display" to get a GUI interface for viewing images. "mogrify" is the command you are looking for to resize images.

See "man imagemagick" to get a full listing of all commands.

---

### Post by wombil on 2010-05-19
Thanks veko,I was out and missed your reply before.I am an old scrubber so scripting is way out for me but I will try the other suggestions.

---

### Post by isotherm on 2010-06-25
I think this will do exactly what you want:
[http://ubuntuforums.org/showthread.php?t=1131770](http://ubuntuforums.org/showthread.php?t=1131770)

---

